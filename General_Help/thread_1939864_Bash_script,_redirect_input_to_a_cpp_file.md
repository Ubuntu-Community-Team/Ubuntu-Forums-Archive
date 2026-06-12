---
title: "Bash script, redirect input to a cpp file"
date: 2012-03-12
forum: General Help
---

### Post by test_tube_baby on 2012-03-12
Hello,

I am using a bash script to run a cpp program several times. However, the program asks for user input. I want this input to be automated by the bash script.

I know how to do this using **redirection**, I just run the program as such:
```
./PROGRAM < INPUT.TXT
```

But, what if the program asks for several inputs, for example, the prompt may be:
```
USER:~/./ADD
ENTER FIRST NUMBER
1
ENTER SECOND NUMBER
2
SUM = 3
```

Would the bash script be:
```
./ADD < 1 < 2
``` ?

That doesn't seem to work.

How do I automate this with a bash script? I don't know how to enter multiple inputs using bash.
Does anyone know how to do this?

---

### Post by TeoBigusGeekus on 2012-03-12
Why don't you incorporate the user input in the cpp program?

---

### Post by test_tube_baby on 2012-03-12
> **TeoBigusGeekus said:**
> Why don't you incorporate the user input in the cpp program?
Because I'll be running this program several times with several different inputs. It needs to be automated with a bash script.

---

### Post by TeoBigusGeekus on 2012-03-12
> **test_tube_baby said:**
> Because I'll be running this program several times with several different inputs. It needs to be automated with a bash script.

Yeah, but each different time you'll need user input, won't you?
What about a cin loop in your code?

---

### Post by test_tube_baby on 2012-03-12
> **TeoBigusGeekus said:**
> Yeah, but each different time you'll need user input, won't you?
What about a cin loop in your code?

For running the program once,

The program asks for two inputs.

Using a bash script, how do I redirect, or enter two inputs?

---

### Post by Slim Odds on 2012-03-12
> **test_tube_baby said:**
> Hello,

I am using a bash script to run a cpp program several times. However, the program asks for user input. I want this input to be automated by the bash script.

I know how to do this using **redirection**, I just run the program as such:
```
./PROGRAM < INPUT.TXT
```But, what if the program asks for several inputs, for example, the prompt may be:
```
USER:~/./ADD
ENTER FIRST NUMBER
1
ENTER SECOND NUMBER
2
SUM = 3
```Would the bash script be:
```
./ADD < 1 < 2
``` ?

That doesn't seem to work.

How do I automate this with a bash script? I don't know how to enter multiple inputs using bash.
Does anyone know how to do this?

./ADD < input.file

Where input.file contains:
1
2

That's a one and a 2 with LF's after each

---

### Post by test_tube_baby on 2012-03-12
> **Slim Odds said:**
> ./ADD < input.file

Where input.file contains:
1
2

That's a one and a 2 with LF's after each

Thanks.
The program I have written is not as simple as the ADD program, I 
just used that as an example.


What if I have two input files, and two input prompts?

---

### Post by TeoBigusGeekus on 2012-03-12
I was thinking of something like (in C):
```
#include <stdio.h>

int main(void)
{
    int input1,input2;
    char c='y';

    while (c=='y') {
        printf("Give first value:\n");
        scanf("%d",&input1);
        printf("Give second value:\n");
        scanf("%d",&input2);
        printf("The sum is %d\n",input1+input2);
        printf("Once more?");
        while ((c=getchar()) != '\n');
        scanf("%c",&c);
    }

    return 0;
}
```

---

### Post by Slim Odds on 2012-03-12
> **test_tube_baby said:**
> Thanks.
The program I have written is not as simple as the ADD program, I 
just used that as an example.


What if I have two input files, and two input prompts?

Not with redirection. The redirect simply turns a file into the standard input.

You need to program some file input to use multiple files.

---

