# Fast method of signed number conversion (two's complement)
Here are simple and quick methods I discovered for converting signed numbers by hand. 
I haven't seen them mentioned anywhere else, but they've proven to be effective for me.

## Binary -> Decimal
When converting a binary number in two's complement to its decimal equivalent, start with the most significant bit (MSB). 
If this bit is a 1, followed by consecutive 1s, identify the lowest 1 in the sequence (right before the first 0). 
Convert the position of this bit into its corresponding negative power of 2, and then add all the values from the lower bits to this sum. 

For example, the binary number **11110101** would be calculated as **-16** (from the position of the lowest 1 in the sequence) plus **5** (the sum of the values of the lower bits), resulting in **-11**.

## negative Decimal number -> Binary
On the other hand, when converting a negative decimal number to its two's complement binary representation, 
start by taking the absolute value of the number and round it up to the next higher power of two. 
This power of two determines how far the binary representation will be filled with a continuous string of ones, starting from the MSB. 
The remaining bits are set to zero. Then, calculate the difference between the absolute value and the power of two you rounded to. 
Combine this difference with the first binary string using a logical OR operation. 

For instance, converting **-30** would involve rounding the absolute value **30** up to **32** and add the leading 1´s, resulting in 1110000. 
Then, subtracting **30** from **32** gives **2**, which in binary is **0000010**. Combining these results gives **1110010**, the two's complement of **-30**.

## both directions
Start with the **least significant bit** and move toward the more significant bits. Keep all bits the same **until and including** the first encountered `1`. From that point onward, **invert all remaining bits**.
