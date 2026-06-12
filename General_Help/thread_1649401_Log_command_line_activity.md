---
title: "Log command line activity"
date: 2010-12-20
forum: General Help
---

### Post by al_mic on 2010-12-20
Hi,

I want to ask you something about how to log the activity in command line to a file.

For example, it happens to test different cli tools in one day and a week later to want to use again those commands I tested. But I do not remember how they wore. (command plus options and all steps).
Or another case is when I log in to a remote server and I do all sort of stuff there that fixes a problem.
I will want to have a way to document all those commands from cli from that ssh session and to use them another time.

Do you know such a tool to start a session monitoring or something and then end it and save to a log file named by me? Or something that does that automatic.

(I know about the history file, but I have there all things a bit chaotic and those logs are rotated, plus I can not set tags to a set of commands - it would really help me to set tags to set of commands - that is why if I can save them to a daily file, or a session file, I can write a file name that will mean something for me)

Thank you.

---

### Post by nothingspecial on 2010-12-20
Type

```
script
```

before you start.

---

### Post by Drenriza on 2010-12-20
This is intersting.

How do you save the file before quitting?
Does it also record if you enter an database?

---

### Post by nothingspecial on 2010-12-20
It records all output to the terminal
```

     Certain interactive commands, such as vi(1), create garbage in the type&#8208;
     script file.  Script works best with commands that do not manipulate the
     screen, the results are meant to emulate a hardcopy terminal.
```

from the man page

Type```
 man script
```

---

### Post by al_mic on 2011-01-06
That is a very good tool.

Thank you!

---

### Post by al_mic on 2012-05-19
Just found this new tool called ttyrec
here is a video about it:
[http://revision3.com/haktip/how-to-ttyrec](http://revision3.com/haktip/how-to-ttyrec)

It will record all your terminal activity into a file which you can then play it back, like a video :)

home page:
[http://0xcc.net/ttyrec/index.html.en](http://0xcc.net/ttyrec/index.html.en)

ubuntu install:
```
sudo apt-get install -y ttyrec
```

start recording:
```
ttyrec
```

play or replay:
```
ttyplay ttyrecord
```

---

### Post by CharlesA on 2012-05-19
Back to sleep you go..

---

