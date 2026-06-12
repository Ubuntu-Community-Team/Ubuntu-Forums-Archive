---
title: "How to make a batch file?"
date: 2010-02-16
forum: General Help
---

### Post by PDA1 on 2010-02-16
How do I create a batch file?

I want to quickly get to the Root directly (or whatever it's called).

This is how I do it now; (the text in bold is what the computer spits out)
[B]
me@me-desktop:~$  [/B]sudo -s
**[sudo] password for me:**  (then I enter my password)
**root@me -desktop:~# **

I'd like to just type one the new of the batch file and then hit enter.  The batch file would then do the rest.

---

### Post by Jackzor on 2010-02-16
Is this an example of breaking the rules? Or is that just when you ask for the GUI Root?

---

### Post by akakingess on 2010-02-16
> **PDA1 said:**
> How do I create a batch file?

I want to quickly get to the Root directly (or whatever it's called).

This is how I do it now; (the text in bold is what the computer spits out)
[B]
me@me-desktop:~$  [/B]sudo -s
**[sudo] password for me:**  (then I enter my password)
**root@me -desktop:~# **

I'd like to just type one the new of the batch file and then hit enter.  The batch file would then do the rest.

Am I to assume that you have to run the batch file as root? If so then, you can just type sudo (name of batch file) and hit enter, it will ask for the root password as usual, but that is the technically safer way to run files as root, rather than giving you complete root control, it will just run that file as root and then end your root privileges until you request them again.  Please let me know if I am misunderstanding.

---

### Post by BrandonBan6 on 2010-02-16
If I understand you correctly, it appears you are wanting to just log in as root? Correct? Otherwise akakingess is correct in his post, you will have root access until/while the file executes. 

There are plenty of tutorials out there of how to to log in as root, because I wouldn't advise it, I won't post a how to for it either.

---

### Post by cariboo on 2010-02-16
```
sudo -i
```

Takes you directly to root's home folder. Using:

```
sudo -s
```

you should really specify what shell to use.

---

### Post by PDA1 on 2010-02-16
I'm at a loss for words.

I was just asking how to make a batch file.

What's the syntax I use..etc, etc?

Doesn't anyone know how?

---

### Post by SteveHillier on 2010-02-16
Unless I am very much mistaken a batch file is a file that contains a series of shell commands.
The rest is up to you but please heed the warnings about giving root unfettered control

---

### Post by BrandonBan6 on 2010-02-16
lol! Sorry... beyond the title, I did not draw that conclusion from your post. 

create a file (no ext necessary) with your favorite editor
give it executable permissions:
```
sudo chmod +x /path/to/file 
```
run the file from terminal or by double clicking on it:
```
 sudo ./filename 
```

---

### Post by Ahadiel on 2010-02-16
> **PDA1 said:**
> How do I create a batch file?

I want to quickly get to the Root directly (or whatever it's called).

This is how I do it now; (the text in bold is what the computer spits out)
[B]
me@me-desktop:~$  [/B]sudo -s
**[sudo] password for me:**  (then I enter my password)
**root@me -desktop:~# **

I'd like to just type one the new of the batch file and then hit enter.  The batch file would then do the rest.

So you just want a root shell to open up when you press a button? Seems like a big security risk.

---

### Post by akakingess on 2010-02-16
I guess I was under the same confusion as BrandonBan6, sorry about that, but he is correct, that is the easy way, if you get good at doing Bash scripting then you can do virtually anything via scripting. Learning all of the commands/syntax is the fun/time-consuming part (I am reading a couple of different books on it now), but I would stick to the basics for now. Sorry again about the confusion.

BTW: Ahadiel does have a good point, that could pose a huge security risk, if anyone could click on that batch file and have root privileges...

---

### Post by wrightrocket on 2010-02-16
> **PDA1 said:**
> How do I create a batch file?

I want to quickly get to the Root directly (or whatever it's called).

This is how I do it now; (the text in bold is what the computer spits out)
[B]
me@me-desktop:~$  [/B]sudo -s
**[sudo] password for me:**  (then I enter my password)
**root@me -desktop:~# **

I'd like to just type one the new of the batch file and then hit enter.  The batch file would then do the rest.
From the example you gave, you don't need a batch file, you just want to be able to access root without typing your password. Seriously, consider whether you want to do this before you do. If your system is ever left unattended around untrustworthy places, then it definitely would not be a good idea.

The solution to your question:
In a terminal type the following and authenticate (one more time!)
sudo visudo

Use the arrow keys to move to the bottom of the file you should note a line that is as follows:
%admin ALL=(ALL) ALL

Modify this line so that it reads this way instead:
%admin ALL=(ALL) NOPASSWD: ALL

It seems the default editor is nano, so to save your changes do:
Press CTRL+O and Enter.
Press CTRL+X again.

Now, you can do any sudo command without a password! Danger!!!!

---

### Post by weblordpepe on 2010-02-16
wrightrocket is correct. thats how you can perform any sudo without a password.

To make a batch file - its pretty simple. You just make a text file using any program you like, and put the commands you want on each line.
Then you save it, typically with a .sh extension so everyone knows what it is.

Then you can right-click it, and select 'executible' so the file is treated as a script/program and not a document. You can make it executible from the command line by typing **chmod +x /path/to/the/file/whatever**

---

