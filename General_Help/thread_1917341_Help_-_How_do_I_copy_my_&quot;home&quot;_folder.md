---
title: "Help - How do I copy my &quot;home&quot; folder"
date: 2012-01-29
forum: General Help
---

### Post by ockron on 2012-01-29
I managed to break ubuntu (sadly) and want to save my "home" folder to my external HDD before I re-install ubuntu.

I made a recovery disk (USB) but I am unable to copy home folder because I don't have "permissions to read it".

Can anyone help me please?

I am using 11.10 and Gnome...

---

### Post by Bucky Ball on 2012-01-29
In a terminal type:

```
sudo nautilus
```

That will open Nautilus with root permission and you should be good to go.

---

### Post by cryptotheslow on 2012-01-29
Use:

```
gksudo nautilus
```

rather than sudo.

gksudo is intended for graphical applications. Hopefully someone can come along and explain the difference :popcorn:

---

### Post by Bucky Ball on 2012-01-29
> **cryptotheslow said:**
> Use:

```
gksudo nautilus
```rather than sudo.

gksudo is intended for graphical applications. Hopefully someone can come along and explain the difference :popcorn:

+1. gksudo is right. My mistake. ;)

---

### Post by ockron on 2012-01-29
> **Bucky Ball said:**
> +1. gksudo is right. My mistake. ;)

Thank you both so very much. 

I managed to "break" Ubuntu and is now desperate to fix it again.

I was changing my desktop background (deleting the current one from the list to replace with a new one) when my system just froze.

I was forced to force shut down my system and now I cannot log into my main profile ... it just freezes when I try to log in.

Luckily I have this guest profile so I have some use of it 

Can anyone please help me?!

I use ubuntu 11.10

---

### Post by cryptotheslow on 2012-01-29
I still don't know why it is right :confused:

Is it something to do with the context it loads associated gtk libraries in or what?

(Yes I'm being lazy :P )

---

### Post by cryptotheslow on 2012-01-29
> **ockron said:**
> Thank you both so very much. 

I managed to "break" Ubuntu and is now desperate to fix it again.

I was changing my desktop background (deleting the current one from the list to replace with a new one) when my system just froze.

I was forced to force shut down my system and now I cannot log into my main profile ... it just freezes when I try to log in.

Luckily I have this guest profile so I have some use of it 

Can anyone please help me?!

I use ubuntu 11.10

Ohhh OK - and the guest profile does not have sudo / gksudo rights I presume?

---

### Post by ockron on 2012-01-29
> **cryptotheslow said:**
> Ohhh OK - and the guest profile does not have sudo / gksudo rights I presume?

Correct ...

I try to login to my profile and it just hangs ... there is no response and the only way out it to press the power button.

---

### Post by cryptotheslow on 2012-01-29
OK - well if you hard powered down while logged in you probably have some file corruption in a gnome or unity config file.

This probably doesn't require a re-install - but will require some command line stuff from Recovery mode to fix.

Do you know how to get into Recovery mode while booting?

---

### Post by ockron on 2012-01-29
> **cryptotheslow said:**
> OK - well if you hard powered down while logged in you probably have some file corruption in a gnome or unity config file.

This probably doesn't require a re-install - but will require some command line stuff from Recovery mode to fix.

Do you know how to get into Recovery mode while booting?

YES ... I discovered that this morning ... You hold down the Left Shift key when it reboots, but I have no idea what to do there ... 
Can you help?

---

### Post by cryptotheslow on 2012-01-29
OK good - that Recovery mode gives you a root login meaning you can access your user files without being moaned at about permissions. Please shout up if you encrypted your home directory!

It seems the desktop background image setting is stored in:
/home/ockron/.gconf/desktop/gnome/background/%gconf.xml

- change ockron to be your actual username on the machine.

So you would boot into Recovery then issue these commands:

```
cd /home/ockron/.gconf/desktop/gnome/background

cp ./%gconf.xml ./%gconf.xml.bak

rm ./%gconf.xml

init 6


```

That makes a backup of the file, deletes the file and finally reboots the machine.

You should then be able to login (albeit with no background image).

---

### Post by ockron on 2012-01-29
> **cryptotheslow said:**
> OK good - that Recovery mode gives you a root login meaning you can access your user files without being moaned at about permissions. Please shout up if you encrypted your home directory!

It seems the desktop background image setting is stored in:
/home/ockron/.gconf/desktop/gnome/background/%gconf.xml

- change ockron to be your actual username on the machine.

So you would boot into Recovery then issue these commands:

```
cd /home/ockron/.gconf/desktop/gnome/background

cp ./%gconf.xml ./%gconf.xml.bak

rm ./%gconf.xml

init 6


```

That makes a backup of the file, deletes the file and finally reboots the machine.

You should then be able to login (albeit with no background image).


I followed the instructions once ... no luck.
Now I'm trying it a second time to make sure.... fingers crossed here !!

---

### Post by ockron on 2012-01-30
> **cryptotheslow said:**
> OK good - that Recovery mode gives you a root login meaning you can access your user files without being moaned at about permissions. Please shout up if you encrypted your home directory!

It seems the desktop background image setting is stored in:
/home/ockron/.gconf/desktop/gnome/background/%gconf.xml

- change ockron to be your actual username on the machine.

So you would boot into Recovery then issue these commands:

```
cd /home/ockron/.gconf/desktop/gnome/background

cp ./%gconf.xml ./%gconf.xml.bak

rm ./%gconf.xml

init 6


```

That makes a backup of the file, deletes the file and finally reboots the machine.

You should then be able to login (albeit with no background image).

Yay ... I can now login, as in I get the splash screen, but the icons are gone and it seems unity does not start :(

HELP ..Plaese

---

### Post by cryptotheslow on 2012-01-30
OK - once logged in try pressing Ctrl Alt T (all 3 keys together) to bring up a Terminal window.

If that brings up a Terminal enter the command:

```
unity --reset
```If it does not bring up a Terminal, try Ctrl Alt F1 (all 3 keys together) - which should give you a full screen tty - login and enter the command above, followed by "sudo init 6" to reboot.

Let us know how you get on.

---

### Post by ockron on 2012-01-30
> **cryptotheslow said:**
> OK - once logged in try pressing Ctrl Alt T (all 3 keys together) to bring up a Terminal window.

If that brings up a Terminal enter the command:

```
unity --reset
```If it does not bring up a Terminal, try Ctrl Alt F1 (all 3 keys together) - which should give you a full screen tty - login and enter the command above, followed by "sudo init 6" to reboot.

Let us know how you get on.

A brand new (special) problem again.

Something is overloading my CPU so that I keep on getting "time out" errors.
I timed out 4 times before I could log in and now I keep on getting theses messages.
[   480.492119] INFO: task ionice:1996 blocked for more than 120 seconds.
[   480.492244] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.

---

### Post by ockron on 2012-01-31
Hi all.

I Solved the issue with a re-install.

Thanks for all the assistance.

---

### Post by Bucky Ball on 2012-01-31
You're welcome. Please mark the thread 'Solved' from 'Thread Tools' to help others. ;)

---

