---
title: "Python not printing to gnome terminal?"
date: 2010-10-21
forum: General Help
---

### Post by Tesko Value on 2010-10-21
I have been using Ubuntu for about a year now and I really do love it. This is my first post because this forum has been so useful in solving my problems as they came up I havn't actually needed to post yet :)

Anyway my problem is with Python. I have used various interpreters and I'm positive, the terminal. All without any problems before I'm sure. However after a recent upgrade to 10.10 my print statements don't seem to print to the terminal.

I am using version 2.6.6 and I tried using: 
#!/usr/bin/python,
#!/usr/bin/python2.6
#!/usr/bin/env python etc. but to no avail.
Even a program consisting of one print statement doesn't work.

Can somebody out there explain to me what is happening? I would be very grateful.

---

### Post by cgroza on 2010-10-21
When you do print("test") what does it do? Nothing?

---

### Post by Tesko Value on 2010-10-21
yeah nothing... 
oh and just to clarify this is a script by the way. I,m executing it with ./aterminaltest.py
and its running but the print statements aren't working.
typing python at terminal and using it as an interpreter works fine.

---

### Post by Tesko Value on 2010-10-22
a cheeky bump. sorry this is driving me nuts.

---

### Post by The Cog on 2010-10-22
What's in your script file?
See this little dialog - print works here (Ubuntu 10.10):
> steve@StevesPC:~$ [COLOR="Blue"]cat termtest.py[/COLOR] 
[COLOR="DarkRed"]#!/usr/bin/env python
print "Hello, world!"[/COLOR]
steve@StevesPC:~$ [COLOR="blue"]chmod +x termtest.py[/COLOR] 
steve@StevesPC:~$ [COLOR="blue"]./termtest.py[/COLOR] 
[COLOR="DarkRed"]Hello, world![/COLOR]

Mind you, that example probably didn't help. It sounds like you know that much basics anyway. Do your scripts print properly if you use xterm instead of gnome-terminal? Or if you Ctrl-Alt-F1 and run them in a tty? (Use Ctrl-Alt-F7 to get the GUI back).

---

### Post by gmargo on 2010-10-22
If it's only your print statements not working, is it a python3 vs python2 problem?  Show us one of your print statements that does not work.  They work fine for me under 10.10 maverick.

---

### Post by Tesko Value on 2010-10-22
@the cog

#!/usr/bin/env python

import os
import sys


def main():
   
    print "Hello, world!"



if __name__ == "__MAIN__":
    main()

Thats my script now.. but yours worked perfectly. it must be something to do with having a main() function? Hmm maybe I don't know the basics after all :)

@gmargo

I just clean installed 10.10 to see if it was anything I messed with so as far as I know (not very) there is only 2.6 on here. 

python --version
python 2.6.6


Cheers for the help guys, really

---

### Post by Tesko Value on 2010-10-22
Same deal with tty.

Oh and I have python and python2.6 in /usr/bin   
hmmm is this the kind of thing you were talking about Gmargo?

---

### Post by Bliepo32 on 2010-10-22
Should it be this?
```
#!/usr/bin/env python

import os
import sys


def main():

    print "Hello, world!" # <-- note, I added spaces here



if __name__ == "__MAIN__":
main()

```

---

### Post by Tesko Value on 2010-10-22
No that was pretty much what I pasted, serves me right for not using code tags:)

It's definitely running but not printing. The same code works in IDLE, emacs etc..

---

### Post by matt_symes on 2010-10-22
Hi

import os
import sys

def main():
        print "Hello world"

if __name__ == "__main__":
        main()


__main__ is in lower case. main() is indented. Print "hello world" is indented

matthew@matthew-laptop:~/Music$ ./test.py 
Hello world
matthew@matthew-laptop:~/Music$ 


Kind regards

---

### Post by Tesko Value on 2010-10-22
Haha what an idiot! 
Thanks Matt. lowercase __main__ it was. Much appreciated.

---

