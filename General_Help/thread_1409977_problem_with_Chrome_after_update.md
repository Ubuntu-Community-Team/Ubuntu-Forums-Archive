---
title: "problem with Chrome after update"
date: 2010-02-18
forum: General Help
---

### Post by motorhead_1 on 2010-02-18
after the last update I cannot lunch the browser chrome...


Failed to execute child process  opt/google/chrome/google-chrome 'No such file or directory'

---

### Post by Mawoon on 2010-02-18
What is your output of this command

```
whereis google-chrome
```

My output is
google-chrome: /usr/bin/google-chrome /usr/share/man/man1/google-chrome.1

I just recently installed the 5.0 google chrome, try doing the same

PS: if you install something with sudo aptitude install, it will automatically remove your google-chrome for one reason. It's also listed in Computer janitor, while it's still installed

---

### Post by Johnny19734 on 2010-02-18
> **Mawoon said:**
> What is your output of this command

```
whereis google-chrome
```

My output is
google-chrome: /usr/bin/google-chrome /usr/share/man/man1/google-chrome.1

I just recently installed the 5.0 google chrome, try doing the same

Well follow the path and open it. Your answer is right there. "/usr/bin/google-chrome" Make a shortcut!

---

### Post by Mawoon on 2010-02-18
Also know, /usr/bin/google-chrome is a symlink to /opt/google/chrome/google-chrome.

/opt/google/chrome/google-chrome is a shell document that in the end executes /opt/google/chrome/chrome

/opt/google/chrome/chrome is a  ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), stripped

If you miss this file, you won't be able to run it

---

### Post by motorhead_1 on 2010-02-18
> **Mawoon said:**
> What is your output of this command


  i don't have any output with this command...

daitarn@daitarn-laptop:~$ whereis google-chrome
google-chrome:
daitarn@daitarn-laptop:~$

---

### Post by motorhead_1 on 2010-02-18
...

---

### Post by Chris_huh on 2010-02-19
I'm having this same problem, and can't work out how to fix it. Any help would be great.

---

### Post by fragos on 2010-02-20
When looking for an executable the "which" command is a better choice. "whereis" gives you a list of any file or folder of that name.

---

### Post by Johnny19734 on 2010-02-21
All you have to do is go where the program was install and do a "CTRL+H" You will see all the hidden files. All in GUI. No need for commands. Thne find the ".chrome" folder and find the .EXE. Create the shortcut and your done. Thats the beauty of Nautilus. AND!!! If you do a "Sudo Nautilus" in terminal you can move folder and files in GUI as ROOT. This will come in handy. Screw  mk dir and mv commands in terminal with long *** directories listed next to them. No need....Hope this helps. These forums are great but some time ppl do things the hard way. I'll never know why :confused:

-JJ

---

### Post by Johnny19734 on 2010-02-21
> **Johnny19734 said:**
> Well follow the path and open it. Your answer is right there. "/usr/bin/google-chrome" Make a shortcut!

This may not be the exe. In linux it will find any thing with the name "google-chrome". Do a search for "chromium-browser"

Launch terminal and type : chromium-browser

If it launches there is nothing wrong with the install. You just have to find it.

---

