---
title: "How do I run a program as super user (root)?"
date: 2011-02-15
forum: General Help
---

### Post by artsim2011 on 2011-02-15
Hi, I have been trying to run the program unrevoked so that I can flash and root my phone. I want to do this on Linux, but this requires me to run the program as root and I don't know how to do this. I looked it up online and it told me to simply type sudo reflash or gksudo reflash and I tried both, sudo says it can't find the program and gksudo does something then nothing appears to happen please help.

---

### Post by idokus on 2011-02-15
What is the error message you are getting?

Go to the/a terminal
go to the location where the "reflash" command is.

```
sudo ./reflash
``` 
(if you are in the same directory as the reflash utility)

I don't have a phone I want to flash so I cannot reproduce, but a common mistake is when you want to execute a command which you downloaded is that you forget to specify the location of the executable.

default behavior under linux is that the executable path does not contain the currect working directory. This is done for security reasons.

I hope this helps you.

ps. I found it hard to figure out what you wanted to do, because you didn't use paragraphs. So it was not directly clear to me what tried, what the context was, etc.

---

### Post by mcduck on 2011-02-15
"sudo" is the way. If you are trying to run a program that's not installed in any of the system locations (like a program on your desktop) you need to move to correct directory first, or provide full path to the executable when you want to run it.

So, assuming the program is called "reflash" and you have it on your desktop:
```

cd ~/Desktop
sudo ./reflash
```

or:
```
sudo ~/Desktop/reflash
```

This isn't even related to running things as root, but running things in general.

What comes to rot access on Ubuntu: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by hawkmage on 2011-02-15
Sudo can also report it can't find the file because it doesn't have the executable bit set.

---

### Post by artsim2011 on 2011-02-15
Thanks to everyone for answering.

TO idokus

The command that you listed worked I wasn't adding ./ at the beginning and after that everything worked correctly thank you so much.

---

