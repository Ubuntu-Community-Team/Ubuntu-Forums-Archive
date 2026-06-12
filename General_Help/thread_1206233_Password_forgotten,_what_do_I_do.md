---
title: "Password forgotten, what do I do?"
date: 2009-07-06
forum: General Help
---

### Post by Camilia on 2009-07-06
I have forgotten my password to my PC. Fortunately have pc set to boot without password.

Found these instruction but I don't understand them.
the standard "hack" is to press "esc" at GRUB and edit the line starting with "kernel" adding rw init=/bin/bash to the end, and then booting into the root account, and then running "passwd <username> to reset your password.

What can I do?

---

### Post by t4thfavor on 2009-07-06
on the grub prompt before the pc begins to load the OS, press esc. Then select recovery mode. This is also known as single user mode.
You will get the option of a root shell. On the root shell prompt type passwd <ussername> where <username> is your user name. It will let you set your password without the old one.


at this point, you should set the root password as well, and in your case write it ddown and store it in a safe location.

Try not to do this again :)

---

### Post by Camilia on 2009-07-07
> **t4thfavor said:**
> 
before the pc begins to load the OS, press esc. 
Then select recovery mode. T
You will get the option of a root shell. On the root shell prompt type passwd <ussername> where <username> is your user name. It will let you set your password without the old one.


Saw my user name. Typed in a password. It didn't work. Pc wanted a code.

---

### Post by credobyte on 2009-07-07
> **Camilia said:**
> Saw my user name. Typed in a password. It didn't work. Pc wanted a code.

What code ? :-k

---

### Post by Camilia on 2009-07-07
> **credobyte said:**
> What code ? :-k

I don't know. It said code not found.

---

### Post by credobyte on 2009-07-07
Try this :

[LIST=1]
[*]Turn your computer on.
[*]Press ESC at the grub prompt.
[*]Press e for edit.
[*]Highlight the line that begins kernel ………, press e
[*]Go to the very end of the line, add** rw init=/bin/bash**
[*]press enter, then press b to boot your system.
[*]Your system will boot up to a passwordless root shell.
[*]Type in passwd username
[*]Set your password.
[*]Type in reboot
[/LIST]

---

### Post by Camilia on 2009-07-07
> **credobyte said:**
> Try this :

[LIST=1]
[*]Turn your computer on.
[*]Press ESC at the grub prompt.
[*]Press e for edit.
[*]Highlight the line that begins kernel ………, press e
[*]Go to the very end of the line, add** rw init=/bin/bash**
[*]press enter, then press b to boot your system.
[*]Your system will boot up to a passwordless root shell.
[*]Type in passwd username
[*]Set your password.
[*]Type in reboot
[/LIST]

I got to what I think was the root shell. I saw root(non):/#
typed in user name. Code code not known.

Not certain what this means: Type in passwd username
Thus typed in user name. Then a password, then pc name and user name.

---

### Post by credobyte on 2009-07-07
> Not certain what this means: Type in passwd username
Thus typed in user name. Then a password, then pc name and user name. 	
[B]
My username is :[/B] dainis
**Command would look like :** passwd dainis

---

### Post by Camilia on 2009-07-07
> **credobyte said:**
> [B]
My username is :[/B] dainis
**Command would look like :** passwd dainis

Thanks,I got it working.

---

### Post by tasyhari on 2009-07-12
> **credobyte said:**
> Try this :

[LIST=1]
[*]Turn your computer on.
[*]Press ESC at the grub prompt.
[*]Press e for edit.
[*]Highlight the line that begins kernel ………, press e
[*]Go to the very end of the line, add** rw init=/bin/bash**
[*]press enter, then press b to boot your system.
[*]Your system will boot up to a passwordless root shell.
[*]Type in passwd username
[*]Set your password.
[*]Type in reboot
[/LIST]

My wife just forgot her password in ubuntu. I think this posting is really useful.. Thank alot.. ;)

---

### Post by Camilia on 2009-07-12
> **tasyhari said:**
> My wife just forgot her password in ubuntu. I think this posting is really useful.. Thank alot.. ;)

8.Type in passwd username confused me. Example is:
username is : dainis
Command would look like : passwd dainis

---

### Post by wojox on 2009-07-12
Type:

```
passwd <yourusername>
```

<yourusername> = who you log in as.

---

### Post by aysiu on 2009-07-12
Why bother editing the kernel line when you can just boot into recovery mode?
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by toledo1 on 2009-07-27
i just downloaded and installed ubuntu and on the first start up it asked me for a username and password, i dont recall asking for one before installation or after, ive read a a few posts about getting your username with recovery, ls/home, and when i try that it says directory not found, when i try the command passwd username, i think i guessed the username right but it does not ask me to enter a new password, just gives me a long list of options that i cant use. i dont have a cd, does anyone know how i can fix this, or do i need to just reinstall the whole program and try not to skip that part next time

---

### Post by aysiu on 2009-07-27
> **toledo1 said:**
> i just downloaded and installed ubuntu and on the first start up it asked me for a username and password, i dont recall asking for one before installation or after, ive read a a few posts about getting your username with recovery, ls/home, and when i try that it says directory not found, when i try the command passwd username, i think i guessed the username right but it does not ask me to enter a new password, just gives me a long list of options that i cant use. i dont have a cd, does anyone know how i can fix this, or do i need to just reinstall the whole program and try not to skip that part next time
I see your problem right now.

You said you typed ```
ls/home
``` There's actually a space in there. The command is ```
ls /home/
``` *ls* is the command and it stands for **l**i**s**t. */home/* is the directory you want to list the contents of. I'd probably add in an extra slash at the end just to make sure you're listing what's inside /home and not listing /home itself.

So please be sure to actually type ```
passwd *username*
``` where *username* is your actual username (the one listed from the previous command).

---

### Post by Camilia on 2009-07-27
[QUOTE=toledo1;7687925]i just downloaded and installed ubuntu and on the first start up it asked me for a username and password ls/home directory not found. The username right but it does not ask me to enter a new password, just gives me a long list of options that i cant use. i dont have a cd, does anyone know how i can fix this, or do i need to just reinstall the whole program and try not to skip that part next time[/QUOTEWhat were the options?

Which os are you using?

---

