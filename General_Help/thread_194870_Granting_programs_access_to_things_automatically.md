---
title: "Granting programs access to things automatically"
date: 2006-06-12
forum: General Help
---

### Post by blackjack6.21.91 on 2006-06-12
I'm tired of having to enter my password.  It's a 16 character ordeal (brute force that, punk;) ), and right after I have entered it to boot, I get prompted for another password!  It talks about allowing nm-applet access to the default keyring (screenshot attached).  Thing is, I always want nm-applet to have access to whatever it needs, and I don't ALWAYS want to have to enter a password.  Possible?

Fish and chips,
blackjack

---

### Post by aysiu on 2006-06-12
Try adding this line to your /etc/sudoers file: ```
blackjack ALL = NOPASSWD: /usr/bin/nm-applet
``` This assumes your computer's username is *blackjack* and the *nm-applet* command is in /usr/bin.

---

### Post by blackjack6.21.91 on 2006-06-12
[SIZE="3"]Ahh, the great Aysiu has blessed my thread.  Lol.  But thanks for those firefox and thunderbird scripts, they're great!

EDIT.  I read in the file I was supposed to do it with Visudo (why is that).  So I tried *sudo visudo /etc/sudoers* and it gave me [I]usage: visudo [-c] [-f sudoers] [-q] [-s] [-V]
[/I].  I don't know which tag to run with it.  I left the error below so you know what I'm talking about.[/SIZE]

First of all, I checked and found nm-applet in /usr/bin, and I ran *sudo gedit /etc/sudoers*, and I added the line, but when I tried to save the file, I got an error about "could not save the file".  I'll attach a screenshot w/ the rest of the error.
[SIZE="3"]
One quiery though.  The original thing talked about access to the default keyring, not root access.  Will this solution work?[/SIZE]

---

### Post by aysiu on 2006-06-12
You can't edit /etc/sudoers with *gedit*.

It has to be edited from the terminal. ```
sudo visudo
```

---

### Post by blackjack6.21.91 on 2006-06-12
Ok.  I'm sorry for not actually **reading** the file.  I made an edit above.  And I tried running it with -f, but I don't know how to save.  It doesn't really have a save option on the menu, and when I do <ctrl><s> it says something wierd.  "XOFF ignored, mumble, mumble."

---

### Post by aysiu on 2006-06-12
No, forget about what the file tells you. Just type ```
sudo visudo
``` at the command prompt. No *-f* option is needed.

Apparently, my installation uses *nano* for editing sudo, and to save in that you use *control-x*.

You can also just do ```
sudo nano /etc/sudoers
``` but that's not the "proper" way to edit /etc/sudoers, and it won't check for syntax errors.

Oh, and before you do anything: ```
sudo cp /etc/sudoers /etc/sudoers.backup
``` of course.

---

### Post by DoktorSeven on 2006-06-12
[QUOTE=aysiu]You can't edit /etc/sudoers with *gedit*.

[/QUOTE]

Well, you can, actually, but still from the commandline:

```

EDITOR=gedit sudo visudo
```

---

### Post by aysiu on 2006-06-12
Thanks for the clarification, DoktorSeven.

---

### Post by blackjack6.21.91 on 2006-06-12
Alright but how do i save?

---

### Post by aysiu on 2006-06-12
If you do ```
EDITOR=nano sudo visudo
``` you save by pressing Control-X, Y, Enter

If you do ```
EDITOR=gedit sudo visudo
``` you save by pressing Control-S

---

### Post by blackjack6.21.91 on 2006-06-12
> One quiery though. The original thing talked about access to the default keyring, not root access. Will this solution work?

It looks like I was correct.  After adding the line and rebooting, nm-applet probably has root access, but it doesn't have access to the keyring.  Any thoughts?

---

### Post by galact on 2006-06-16
bug ??? network-manager ?? .... 

idem problem

---

### Post by srt4play on 2006-08-20
> **aysiu said:**
> Try adding this line to your /etc/sudoers file: ```
blackjack ALL = NOPASSWD: /usr/bin/nm-applet
``` This assumes your computer's username is *blackjack* and the *nm-applet* command is in /usr/bin.

By "computer's username" do you mean the hostname of the machine or his login name?

---

### Post by Alpha_Maverick on 2006-08-21
bump. I now no longer have any connections showing on nm-applet. I have tried removing completely, and reinstalling, after returning to original sudoers file. nothing.](*,) ](*,)

---

### Post by Alpha_Maverick on 2006-08-21
double, sorry, can't delete

edit: scratch that, I think it was the xserver glitch, but I'm a little skittish about trying again:(

---

### Post by madcap_magician on 2006-08-23
I think what you were originally looking for is this:

[http://www.ubuntuforums.org/showthread.php?t=187874&highlight=network+manager+password](http://www.ubuntuforums.org/showthread.php?t=187874&highlight=network+manager+password)

However it's only a temporary thing, as soon as you update network manager again it's back to typing in your password.

---

