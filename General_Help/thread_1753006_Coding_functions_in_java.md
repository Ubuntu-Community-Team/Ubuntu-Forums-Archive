---
title: "Coding functions in java:"
date: 2011-05-08
forum: General Help
---

### Post by javajames97 on 2011-05-08
Basically i am fairly new to java, and so i started looking at all the different things i could learn in basic java and made a completely useless program that is cluttered and irritating to look at, but i have this problem with calling up functions, this is my code:```

import java.io.*;
import java.util.Scanner;

class project2 {
    public void mast(String[] args) { //DEFINED here
        //useless code is here
    }
    public static void main(String[] args) {
        int repet = 1;
        while (repet==1) {
            mast(); //CALLED here
            int re = 'y';
            System.out.println("\n\nwould you like to stay? (y/n): ");
            try {
                re = System.in.read();
            }catch(java.io.IOException exp){ exp.printStackTrace();}
            if (re=='y') {
                continue;
            } else {
                repet = 3;
                break;
            }
        }
        System.out.println("bye for now\n");
    }
}

```
i have marked where i have defined and called the function, i can't help getting the feeling that i haven't called the function correct but i don't know if i need any prefixes - i.e prefix.mast(). My question is how to call up defined functions, but if you do notice anything else wrong with this please don't hesitate to tell me.

---

### Post by javajames97 on 2011-05-08
my output from javac compiler is as follows
```

james@james-laptop:~/Desktop/coding/Jcoding$ javac pro2.java
pro2.java:52: mast(java.lang.String[]) in project2 cannot be applied to ()
            mast();
            ^
1 error

```

---

### Post by kostkon on 2011-05-08
try changing the line
```
mast();
```
to e.g.
```
this.mast("test");
```

---

### Post by cgroza on 2011-05-08
You need to declare the mast function static because it is being called directly from main, which is a static function. Static functions can only access static functions and variables.

---

### Post by cipherboy_loc on 2011-05-08
When you defined mast, you defined it as:

```

mast (array of string elements)

```

You called it as:

```

mast (~nothing here~)

```


You need to change either of them for it to work.


Cipherboy

---

