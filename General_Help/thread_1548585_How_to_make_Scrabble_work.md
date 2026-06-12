---
title: "How to make Scrabble work"
date: 2010-08-08
forum: General Help
---

### Post by Dex73 on 2010-08-08
I've downloaded a linux native version of scrabble(scrabble_1.9-1.tar.gz) and extracted it. Now I don't know what to do. The folder the extraction made(Scrabble) has an application file that can run the game as a terminal application but not on a board that looks like the game. I haven't been able to figure out how to input a move. The instructions say...

Enter word as "YXd <word>" (Y=row, X=col, D=a/d) or "help" for other commands.

There is also a make file that may be a little screwy. It only seem to work at all when I run it in a terminal but it runs for less than a second and then closes. Is this normal?

I would like to get the game working not just in a terminal but the second best thing would be if someone could tell me how to input a move. Any suggestions would be greatly appreciated.

---

### Post by AlphaLexman on 2010-08-08
I'm guessing you have found the terminal version of 'Scrabble' which is called scribble.

Here is a screenshot:

```
         86 letters remain
   0 1 2 3 4 5 6 7 8 9 A B C D E
   - - - - - - - - - - - - - - -
0| @     -       @       -     @ |0  My Words:
1|   *       +       +       *   |1   
2|     *       -   -       *     |2   
3| -     *       -       *     - |3   
4|         *           *         |4   
5|   +       +       +       +   |5   
6|     -       -   -       -     |6   
7| @     -       *       -     @ |7   
8|     -       -   -       -     |8  Your Words:
9|   +       +       +       +   |9   
A|         *           *         |A   
B| -     *       -       *     - |B   
C|     *       -   -       *     |C   
D|   *       +       +       *   |D   
E| @     -       @       -     @ |E   
   - - - - - - - - - - - - - - -
   0 1 2 3 4 5 6 7 8 9 A B C D E

 me:0      R D N I K U E   you:0  

I go first...
Looking...............
Thinking.

I placed:
    8  TITlE
for a total of 8 points.

         81 letters remain
   0 1 2 3 4 5 6 7 8 9 A B C D E
   - - - - - - - - - - - - - - -
0| @     -       @       -     @ |0  My Words:
1|   *       +       +       *   |1   title(8)
2|     *       -   -       *     |2   
3| -     *       T       *     - |3   
4|         *     I     *         |4   
5|   +       +   T   +       +   |5   
6|     -       - l -       -     |6   
7| @     -       E       -     @ |7   
8|     -       -   -       -     |8  Your Words:
9|   +       +       +       +   |9   
A|         *           *         |A   
B| -     *       -       *     - |B   
C|     *       -   -       *     |C   
D|   *       +       +       *   |D   
E| @     -       @       -     @ |E   
   - - - - - - - - - - - - - - -
   0 1 2 3 4 5 6 7 8 9 A B C D E

 me:8      R D N I K U E   you:0  

Enter word as "YXd <word>" (Y=row, X=col, D=a/d) or "help" for other commands.
: 

```The game is 'looking' for 'Y' coordinates, 'X' coordinates, found at the sides and top and bottom of the 'board, and 'a' / 'd' for **a**cross or **d**own option, put a space between 'YXd' and the word you can make from the letters in the 'rack' for me, the letters are:
> R D N I K U ESo I could play the word 'trunked' at y=3, x=7 and **a**cross. Therefore, I would enter:
```
37a trunked
```and get:
```
You placed:
   24  TRUNKED
for a total of 24 points.

         75 letters remain
   0 1 2 3 4 5 6 7 8 9 A B C D E
   - - - - - - - - - - - - - - -
0| @     -       @       -     @ |0  My Words:
1|   *       +       +       *   |1   title(8)
2|     *       -   -       *     |2   
3| -     *       T R U N K E D - |3   
4|         *     I     *         |4   
5|   +       +   T   +       +   |5   
6|     -       - l -       -     |6   
7| @     -       E       -     @ |7   
8|     -       -   -       -     |8  Your Words:
9|   +       +       +       +   |9   trunked(24)
A|         *           *         |A   
B| -     *       -       *     - |B   
C|     *       -   -       *     |C   
D|   *       +       +       *   |D   
E| @     -       @       -     @ |E   
   - - - - - - - - - - - - - - -
   0 1 2 3 4 5 6 7 8 9 A B C D E

```Have fun!

---

### Post by Dex73 on 2010-08-08
Thanks it's working great! I just have a couple of questions. How do i input words that have words going through them. For example if I have melt and I want to play off the e to make deer, what symbol do I use to represent the e? Also it says the game is set to level 1 by default and it is really easy, although if I had to guess, I'd say the computer does know any words is the reason. It will almost always trade in, I have to define my words every time, and the computer's only words are ones I've defined. Can it not read the wordlist files, which are there with all the other files and I haven't moved it. I could use some help with this problem or I may just need to know how to up the difficulty. Thanks again!

---

### Post by AlphaLexman on 2010-08-08
> I may just need to know how to up the difficulty. Thanks again!
Just type:
```
scribble 7
```
The higher the number [1-9], the more challenging.

---

### Post by Dex73 on 2010-08-09
Never mind about the not being able to have the words cross. I think I was entering the coordinates as (x,y). Thanks for all the help!

---

### Post by AlphaLexman on 2010-08-09
> **Dex73 said:**
> Never mind about the not being able to have the words cross. I think I was entering the coordinates as (x,y). Thanks for all the help!
I've always thought that logically coordinates should be alphabetical (x,y). But this game is unnervingly backwards! (y,x)

---

