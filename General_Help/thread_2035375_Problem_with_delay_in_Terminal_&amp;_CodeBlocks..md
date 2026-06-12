---
title: "Problem with delay in Terminal &amp; Code::Blocks."
date: 2012-07-30
forum: General Help
---

### Post by Malcolm Jackson on 2012-07-30
I am working through Ivor Hortons book Beginning C, 3rd edition,  using Terminal and CodeBlocks 10.04, on 11.04 'Natty Narwhal'.
There have been a couple of problems such as getchar that I have managed to get solved on line, but now on Page 180 I have hit a brick wall. There is a sample program called Simple Simon. 
Simple Simon is a memory game that posts a sequence of numbers on the screen for you to memorise. After 1 second the numbers are erased, and you have to key in what you remember, and hope that you have remembered correctly.
I have not been able to get the program working on terminal or through code blocks, despite several days of trying to find out what is wrong.
A couple of days ago I decided to start from scratch and write the program myself, building up a bit at a time and perhaps find out why the original program won't work for me.
The problem I have got is with the following piece of code. (This code works OK on XP and Vista):-

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main()
{
    long now = 0;
    printf("Hello world!");
    now = clock();

    for(;clock() - now<CLOCKS_PER_SEC    ;);/*After 1 second delay this "*/
    printf("\r");                           /*"code should erase "Hello world!"  */
    printf("       ");
    return 0;
}
I have fried all sorts of delay methods, but they all end up not doing what I want to do.
Instead of writing Hello world! on the screen and erasing it after 1 second, the screen comes up and after 1 second   Hello world! is printed and erased at the same instant.
I put a break in before the delay, and can see  Hello world! is indeed printed.
On XP and Vista this program works correctly. 
I have checked through the man pages, but don't yet know enough to know if I have found an answer or not. Nothing I have tried works, so would be mightily obliged if some one will let me know what to do to get this working.
Many thanks,
Malcolm Jackson.

---

