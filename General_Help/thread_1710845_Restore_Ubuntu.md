---
title: "Restore Ubuntu?"
date: 2011-03-20
forum: General Help
---

### Post by 1chess2u Christian on 2011-03-20
My Ubuntu has been working strangely ever since I updated it about two weeks ago. I want to restore it to the condition that I installed it, but with all my files intact. Can anyone help me?

---

### Post by abyrne on 2011-03-20
When you installed Ubuntu, did you put your home folder on a separate partition?

---

### Post by Script Warlock on 2011-03-20
unfortunately there is no system restore yet in ubuntu..

---

### Post by 1chess2u Christian on 2011-03-20
I do not believe that I put my Home folder on a separate partition, but it may be possible, although very unlikely, as I do not know how to move files and folders between partitions. As for there not being any system restore for Ubuntu, I believe that it would be unwise to leave that unchanged. But, as I do not know how to create programs (yet), I cannot do anything about that. If anybody would be willing to teach me how, I would appreciate it greatly.

---

### Post by Script Warlock on 2011-03-20
reinstall is not an option, clean your ubuntu. what kind of strange things happen?

---

### Post by 1chess2u Christian on 2011-03-20
Well, for starters, my Compiz will not work at all (even the close-bar on top of the open windows is not there.) Furthermore, applications will close without warning and without me doing anything to close them.

---

### Post by abyrne on 2011-03-20
> Well, for starters, my Compiz will not work at all (even the close-bar on top of the open windows is not there.)
Can your computer handle Compiz? There could be a problem with video card comparability.

> Furthermore, applications will close without warning and without me doing anything to close them.
Which applications?

---

### Post by 1chess2u Christian on 2011-03-20
Yes, the Compiz has worked on my computer before (I would not be complaining about it suddenly not working if it had worked before), and of the types of applications, well, the games started doing it first, and then other things. The only application that has not yet closed spontaneously is Google Chrome.

---

### Post by abyrne on 2011-03-20
> **1chess2u Christian said:**
> The only application that has not yet closed spontaneously is Google Chrome.Ahh, good ol' reliable Google.

Try starting one of the crashing applications from the Terminal. When it crashes, observe the output. Notice anything strange?

---

### Post by 1chess2u Christian on 2011-03-20
First off, I don't know enough yet to start a program from the Terminal (unless it's like with Windows.) Second, I don't know enough to tell what's normal and what's not. I also don't know how to fix it if I do see something weird.

---

### Post by 1chess2u Christian on 2011-03-20
> **abyrne said:**
> Ahh, good ol' reliable Google.

Indeed! I do not use any other internet browser, because of the lack of toolbars, and fast speed.

---

### Post by abyrne on 2011-03-20
> **1chess2u Christian said:**
> First off, I don't know enough yet to start a program from the Terminal (unless it's like with Windows.) Second, I don't know enough to tell what's normal and what's not. I also don't know how to fix it if I do see something weird.

Starting applications in the Ubuntu terminal is similar to starting one through Windows, except you don't need to specify the entire path of the program. For example, if you wanted to start Firefox, you would fire up the Terminal and type in
```
firefox
```
and hit Enter. If you wanted to start your text editor, the process is the same except you would type in 
```
gedit
```
instead of firefox. Ususally, it's just type the name of the program and hit Enter. I should also note that there shouldn't be any capitalization or spaces in the name of the program.

Once you start a program, it should output some text through the terminal. If it crashes, copy that output from the terminal and show it here (please use the CODE button when posting this output).

---

### Post by 1chess2u Christian on 2011-03-20
What would the code name for Open Office Word Processor?
That's the program that closes most often.

---

### Post by abyrne on 2011-03-20
> **1chess2u Christian said:**
> What would the code name for Open Office Word Processor?
That's the program that closes most often.

Ehh. I just did a little research on Open Office. It seems to not output anything to the terminal when it runs. Any other programs that crash often?

---

### Post by 1chess2u Christian on 2011-03-20
Globulation 2 is one of them. (when this first happened, i was at school, so I thought that it was the network admin, but it happened when I wasn't at school)

---

### Post by abyrne on 2011-03-20
I don't have that game but I think the command is ```
glob2
```

---

### Post by 1chess2u Christian on 2011-03-20
Thank you, but I found out already. Get the code soon...

---

### Post by 1chess2u Christian on 2011-03-20
here is the code. retiring for the night
```
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

```
If that isn't weird, then I must be messed up in the head. :)

---

