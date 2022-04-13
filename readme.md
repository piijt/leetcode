/**
  Sheet for solved solutions, at leetcode.com 
*/

The algorithm for myAtoi(string s) is as follows:

Read in and ignore any leading whitespace.
Check if the next character (if not already at the end of the string) is '-' or '+'. Read this character in if it is either. This determines if the final result is negative or positive respectively. Assume the result is positive if neither is present.
Read in next the characters until the next non-digit character or the end of the input is reached. The rest of the string is ignored.
Convert these digits into an integer (i.e. "123" -> 123, "0032" -> 32). If no digits were read, then the integer is 0. Change the sign as necessary (from step 2).
If the integer is out of the 32-bit signed integer range [-231, 231 - 1], then clamp the integer so that it remains in the range. Specifically, integers less than -231 should be clamped to -231, and integers greater than 231 - 1 should be clamped to 231 - 1.
Return the integer as the final result.
[UNSOLVED]
<pre>
/**
 * @param {string} s
 * @return {number}
 */
var myAtoi = function(s) {
    let symbol = "";
    if(s.split("").includes("+")) {
        symbol = "+"
    }
    if(s.split("").includes("-")) {
        symbol = "-"
    }
    let valid_digits = s.replace(/[^1-9]/g, ""); 
    if(!valid_digits.lengt <=0) {
        return 0
    }
    let digits = valid_digits.split("")
    const unary = "+";
    const nega = "-";
    const res = []
    const valid= digits.reduce((a,b) => {
        if(parseInt(a+b) && parseInt(a) && parseInt(b)) {
            return a+b
        }
    });
    return symbol.length > 0 ? symbol + valid_digits : valid_digits 
};
</pre>

[SOLVED]
Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range [-231, 231 - 1], then return 0.

Assume the environment does not allow you to store 64-bit integers (signed or unsigned).
<pre>
var reverse = function(x) {
    const minIntegerNumber = Math.pow(-2, 31) 
    const maxIntegerNumber = Math.pow(2, 31) - 1 
    let add = ""
    if(x < 0) {
        add = "-"
    }
    
    let tmp = x.toString().split("");
    let rev = tmp.reverse();
    let join = parseInt(add + rev.join(""));
    if(x < 0) {
        return join < minIntegerNumber ? 0 : join
    } else {
        return join > maxIntegerNumber ? 0 : join
    }
};
</pre>
