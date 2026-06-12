---
title: "Ubuntu won't boot after installing and removing KDE"
date: 2011-02-21
forum: General Help
---

### Post by 3602 on 2011-02-21
So I decided to try KDe, because why not? They have Kookies.
Installed *kubuntu-desktop* by reading this: [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)
Tried it for a bit, didn't like it, so tried to remove it by reading here: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
However Terminal gave me an error, saying dependencies about *odbcinst1debian2*, saying that it depends on *odbcinst *but is not going to be installed. So I went into Synaptic and manually removed these, then did the long command.
Things got removed, reboot.
Now Plymouth boots, but it stops at five orange dots (not moving) and then nothing. No login menu. I held down the power button and rebooted three times, all stuck at Plymouth.
Yeah I can reinstall Ubuntu, I have the disk, but there are many configs that I did, that I do not remember.
So, what now?
Thank you very much.

---

### Post by Habitual on 2011-02-21
It's not clear if you have gnome installed or not. Or KDE for that matter...

Please advise...

---

### Post by 3602 on 2011-02-21
Well at the end of that delete command there is *sudo apt-get install gnome-desktop*, so...

---

### Post by 3602 on 2011-02-22
Bump.

---

### Post by runeh76 on 2011-02-22
> **Habitual said:**
> It's not clear if you have gnome installed or not. Or KDE for that matter...

Please advise...

Didnt get the purpose of this BUT...

Did u try to install Gnome back?

---

### Post by 3602 on 2011-02-22
> **runeh76 said:**
>  
Did u try to install Gnome back?
 
Um. Well how? All I got right now is the purple Plymouth.

---

### Post by runeh76 on 2011-02-23
you should have a recovery mode option when you start up your machine.

Hit ESC, and you should be able to log in via the terminal.

---

### Post by 3602 on 2011-02-23
> **runeh76 said:**
> you should have a recovery mode option when you start up your machine.
 
Failing that, hit ctrl+alt+f1 when you get the X error, and you should be able to log in via the terminal.
 
Um... for one, no I don't have any options when I boot. And second, I don't actually see any errors.

---

### Post by wiggly81 on 2011-02-23
you should be able to bring up the grub menu when booting by pressing i think "esc" after the initial bios screen, this should give you recovery options

---

### Post by runeh76 on 2011-02-23
Yes u do have a choice to choose..(recovery mode)

[https://wiki.ubuntu.com/RecoveryMode]("https://wiki.ubuntu.com/RecoveryMode")

---

### Post by wiggly81 on 2011-02-23
unless ofcause one of the 
> but there are many configs that I did, that I do not remember

was to edit the grub.cfg and remove the options

---

### Post by 3602 on 2011-02-23
> **runeh76 said:**
> Yes u do have a choice to choose..(recovery mode)
 
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
 OK, let's pretend that I have forgotten my *root* password (I don't even have one for *root*, only my user name), I'll need the CD, correct?

---

### Post by 3602 on 2011-02-23
Marking as SOLVED. Reason:
Not really *solved*. I re-installed.

---

