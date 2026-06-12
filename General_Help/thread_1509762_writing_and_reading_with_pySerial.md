---
title: "writing and reading with pySerial"
date: 2010-06-14
forum: General Help
---

### Post by miak on 2010-06-14
Hi,

I am trying to use pySerial to write a script that gives specific command to hardware using tty terminal and then receives the output, parses it and then does some other work with it which is not the issue.
So I had hard time using pyserial, I though it might be some problem with tty or network or something else, so I tried using it with normal gnome terminal(\dev\pts\4) on my computer, here is the python code that I run:
```
import serial
ser = serial.Serial("/dev/pts/4")
ser.write("ls\n")
```
just an example to see if it works or not, and the response for to this command i see :
```
me@me-lucid:~$ ls


```and nothing after that.
I thought that it might be the case that terminal sends something back, but i tried receiving text and didn't work, so i guess that's not the case. Can anyone help with this?
What am I doing wrong?

Thanks,
miak

---

### Post by miak on 2010-07-11
Just if somebody else runs into this problem:
I don't think there is anything wrong with the code itself, just that's the result of some security program running on ubuntu, since I was able to get this work on actual machine I wanted to.
But if anyone has any idea why, i'd be happy to know.

---

