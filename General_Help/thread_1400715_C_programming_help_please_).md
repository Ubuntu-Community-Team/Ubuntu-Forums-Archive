---
title: "C programming help please :)"
date: 2010-02-07
forum: General Help
---

### Post by Donok on 2010-02-07
Hey guys.  I coded the following program below: but I have a problem... I think its perhaps the logic I have used is not too good... here it goes...
The program below should:                      ask the user to enter a letter ('a' to 'z' or 'A' to 'Z') and outputs VOWEL or CONSONANT depending upon the input. You should use a switch statement to identify the vowels and cascade these cases togther. If the user types in a character which is not a letter you should print out the message NOT-A-LETTER. 



I get the program to do all of these but when I execute it and say I type in A the output I  get is A is a Vowel and then A is a CONSONANT as well<< its this extra bit which is my problem... It shows that all the Vowels are vowels but are also Consonants which dose not make sense.
Here is the c code:

#include <stdio.h>
#include "simpleio.h"

int main()                   // This program has the BOTH feature added to it
{
    char letter;
    
    printf("Please enter a letter 'A'-'Z' or 'a'-'z' : \n");
    letter = getchar();
    
    if ((letter >= 'A' && letter <= 'Z' ) || (letter >='a' && letter <= 'z'))
    {
        printf(" %c is a CONSONANT\n", letter);        
    }
        
    else
    {
        printf("NOT-A-LETTER\n");
    }
    
    switch(letter)                                                      
    {
        case 'A' : printf(" A is a vowel\n"); break; 
        case 'a' : printf(" a is a vowel\n"); break;
        
        case 'E' : printf(" E is a vowel\n"); break;
        case 'e' : printf(" e is a vowel\n"); break;
        
        case 'I' : printf(" I is a vowel\n"); break;
        case 'i' : printf(" i is a vowel\n"); break;
        
        case 'O' : printf(" O is a vowel\n"); break;
        case 'o' : printf(" o is a vowel\n"); break;
        
        case 'U' : printf(" U is a vowel\n"); break;
        case 'u' : printf(" u is a vowel\n"); break;
        
        case 'Y' : printf(" Y is BOTH\n   "); break;
        case 'y' : printf(" y is BOTH\n   "); break;
                        
    }
         
    return 0;
}
many thanks hope you can help me out. what I wanted was how do I print out vowel and only this instead of having both.

---

### Post by rnerwein on 2010-02-07
hi
your program is just you told him:
/* input A --> letter >= A && letter <= Z         ---> that's true  you print CONSTANT */
if ((letter >= 'A' && letter <= 'Z' ) || (letter >='a' && letter <= 'z'))
    {
        printf(" %c is a CONSONANT\n", letter);        
    }
        
    else
    {
        printf("NOT-A-LETTER\n");
    }
...
....
case 'A' : printf(" A is a vowel\n"); break;   /* this is ok too - ok */

ciao

---

### Post by Donok on 2010-02-07
> **rnerwein said:**
> hi
your program is just you told him:
/* input A --> letter >= A && letter <= Z         ---> that's true  you print CONSTANT */
if ((letter >= 'A' && letter <= 'Z' ) || (letter >='a' && letter <= 'z'))
    {
        printf(" %c is a CONSONANT\n", letter);        
    }
        
    else
    {
        printf("NOT-A-LETTER\n");
    }
...
....
case 'A' : printf(" A is a vowel\n"); break;   /* this is ok too - ok */

ciao
thanks for that sorry to bother you but what I really wanted to know is how do I print out vowel and only this instead of having both. vowel and consonant

---

### Post by akashiraffee on 2010-02-07
```

if ((letter >= 'A' && letter <= 'Z' ) || (letter >='a' && letter <= 'z'))
    {
        printf(" %c is a CONSONANT\n", letter);        
    }

```So everything between a-z & A-Z is a consonant?  Take this out and use a "default" case in your switch for the consonants:
```

        default:  
            printf(" %c is a CONSONANT\n", letter);        
            break;

```
              

getchar() returns an int, not a char.  You need to correct that.  It will not make a difference to anything else and will help insure the code works properly.

You can save yourself some unnecessary duplication by forcing the letter to lower case:
```

if (letter < 97) letter +=32;
if (letter < 'a' || letter > 'z')... /* not a letter */

```Now you only need to deal with a-z instead of a-z and A-Z.

---

### Post by DGortze380 on 2010-02-07
look at some pseudo code and see if you can find the logic errors.

```

// get user input (1 char)
  //check for valid input
   // if valid, check for vowel
       // if vowel print message
       // else print message
   // else print message
// return

```

---

### Post by Donok on 2010-02-07
Oh I do now see what is wrong. This has made it much clearer and logical thanks all for your replies much appreciated....My mind does wierd things...

---

### Post by nikhilbhardwaj on 2010-02-07
it syas that coz thats exactly what its supposed to do
or so you've written

---

### Post by Donok on 2010-02-08
> **akashiraffee said:**
> ```

if ((letter >= 'A' && letter <= 'Z' ) || (letter >='a' && letter <= 'z'))
    {
        printf(" %c is a CONSONANT\n", letter);        
    }

```So everything between a-z & A-Z is a consonant?  Take this out and use a "default" case in your switch for the consonants:
```

        default:  
            printf(" %c is a CONSONANT\n", letter);        
            break;

```getchar() returns an int, not a char.  You need to correct that.  It will not make a difference to anything else and will help insure the code works properly.

You can save yourself some unnecessary duplication by forcing the letter to lower case:
```

if (letter < 97) letter +=32;
if (letter < 'a' || letter > 'z')... /* not a letter */

```Now you only need to deal with a-z instead of a-z and A-Z.
ahh I do see but the only problem is with the default... if i type in say a ! or a " it will print it is a consonant  too when id rather it say its not a letter, and thats it.

---

### Post by jim_24601 on 2010-02-09
> **akashiraffee said:**
> 
```

if (letter < 97) letter +=32;
```


I shouldn't convert a character to lower case like that, in a homework assignment any more than production code. I draw the OP's notice to the character type functions in <ctype.h>, particularly isalpha() and tolower().

---

