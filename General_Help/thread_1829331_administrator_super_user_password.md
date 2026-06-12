---
title: "administrator super user password"
date: 2011-08-20
forum: General Help
---

### Post by choochoousmc on 2011-08-20
I just installed 10.04 on a new system.
I downloaded the newest version to the harddrive default location.
Inserted a usb stick already formatted
selected startup disk creator.

It found the downloaded Ubuntu file it recognized the usb stick.

but it refuses to  create it.
apparently my standard user (administrator) password doesn't allow the creation.

Heard Ubuntu has another password built in that is required to do some high level tasks

Does anybody have the password

And I need the commands to become super user permanently with my standard password.

Thanks

---

### Post by haqking on 2011-08-20
the super user or root user is disabled by default in Ubuntu and the forum guidelines does not permit instructions or recommedations on enabling it.

There is no need to enable the root user as everything is done using either sudo or gksudo (gksudo being used for graphical apps and sudo at command line)

See here [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

When you created your install it should of asked you for a username which is what you login with and should be in the admin group and so enabling you to use sudo to gain eleveated privelege for a short time to do tasks.

So any admin password required should be your login password.  If sudo is not allowing you to user your password then for some reason you may not be in the sudo group

see here to reset password [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

and here to reapir sudo [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by choochoousmc on 2011-08-20
yes it asked for name and password  during installation.

But start up disk creator will NOT accept my normal password to create a USB startup disk.

Start up disk creator should NOT require a special hidden password!

I followed the online directions and it fails.

Linux is getting to be as bad as windows, in not letting you do simple tasks to get your work done.

So I am still hung up I select startup disk creator from the menu, and it refuses to create it.  It is wanting a password I do not have

---

### Post by Topsiho on 2011-08-20
If you have to do something only root (the usual name for the administrator) can do, then you put sudo in fromt of the command, and give the password you entered while installing Ubuntu, when asked for it.

You need to do this when you change something in the system, or so. You don't need to sudo and give the password when you do things to your own files, in your home directory.

In Ubuntu there is not a separate root password for root, the password given during the install is the password you need.

You want to become root permanently, but the main advantage of Ubuntu over other linuxes is that you don't need to. You do a root command using sudo, and for that command you are root. So you need not become root permanently, with the dangers that that incurs, so as being able to wreck your system, or an intruder getting root rights on your system.

It is possible though, but I'm not telling you how :)

When giving a password after sudo, you'll find that if you do so again within, I think, ??? minutes, your command is executed without password. This is to prevent too much irritation.

Topsiho

---

### Post by haqking on 2011-08-20
> **choochoousmc said:**
> yes it asked for name and password  during installation.

But start up disk creator will NOT accept my normal password to create a USB startup disk.

Start up disk creator should NOT require a special hidden password!

I followed the online directions and it fails.

Linux is getting to be as bad as windows, in not letting you do simple tasks to get your work done.

So I am still hung up I select startup disk creator from the menu, and it refuses to create it.  It is wanting a password I do not have

So at what point during these instruction are you getting stuck at [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

can you show us a screen dump of what you are doing

---

### Post by choochoousmc on 2011-08-20
error window
Authenticate
           System policy prevents mounting
an application is attempting to perform an action that
requires privileges. Authentication is required to perform
this action

then a password window.

It will NOT accept my user login password. Nothing has been done to the system yet as it is a brand new live cd install of 10.04

Then a new window opens   INSTALLATION FAILED       ONLY OPTION IS TO QUIT

---

### Post by haqking on 2011-08-20
> **choochoousmc said:**
> error window
Authenticate
           System policy prevents mounting
an application is attempting to perform an action that
requires privileges. Authentication is required to perform
this action

then a password window.

It will NOT accept my user login password. Nothing has been done to the system yet as it is a brand new live cd install of 10.04

Then a new window opens   INSTALLATION FAILED       ONLY OPTION IS TO QUIT

can you show a screen dump, it is easier to help when we can see whats going on, even though you typed the message, it helps to see whats happening when you get that message

---

### Post by choochoousmc on 2011-08-20
How do I do a screen dump?

I also went to users groups to see if I could change settings there.

My login password does not work there either.

---

### Post by spiky001 on 2011-08-20
I just use the print screen button

Have you pressed the caps lock it is case sensitive

---

### Post by haqking on 2011-08-20
> **choochoousmc said:**
> How do I do a screen dump?

I also went to users groups to see if I could change settings there.

My login password does not work there either.

press the PrtSc key and it should save a copy to yoru desktop.

you might want to try the resetting password option in the link i posted in my first post.

Edit: can you also go to terminal and type the following then show us the output:

grep <username> /etc/group

replacing the <username> with yourname and no <> symbols

---

### Post by choochoousmc on 2011-08-20
i have been using 10.10 for last year. As a general replacement for windowa. I understand and use all general functions for day to day use.
And I did get a procedure here a year ago to become the permanent SUDO user.
There is a hidden password during installation that you need to use to make certain changes to the system. But you can use the terminal to become permanent sudo user to eliminate having to use this hidden p/w.
Most every thing I do is done via the drop down menus.
See my next new post to see what has happened since I originally requested help.

> **Topsiho said:**
> If you have to do something only root (the usual name for the administrator) can do, then you put sudo in fromt of the command, and give the password you entered while installing Ubuntu, when asked for it.

You need to do this when you change something in the system, or so. You don't need to sudo and give the password when you do things to your own files, in your home directory.

In Ubuntu there is not a separate root password for root, the password given during the install is the password you need.

You want to become root permanently, but the main advantage of Ubuntu over other linuxes is that you don't need to. You do a root command using sudo, and for that command you are root. So you need not become root permanently, with the dangers that that incurs, so as being able to wreck your system, or an intruder getting root rights on your system.

It is possible though, but I'm not telling you how :)

When giving a password after sudo, you'll find that if you do so again within, I think, ??? minutes, your command is executed without password. This is to prevent too much irritation.

Topsiho

---

### Post by uRock on 2011-08-20
Start the USB creator via CLI and it will not ask for any passwords.```
sudo usb-creator-gtk
```

---

### Post by choochoousmc on 2011-08-20
I will do the grep......... printout later

I have rebooted. redownloaded the iso to the usb stick.
Used ARK to extract.
Copied everything back to the downloads folder.
The stick is formatted fat32  via ubuntu disk utility

I tried startup creator again. This time it took my password. It says I did a successful create and can now use in any computer after setting boot default to usb.

I did that. Rebooted, but it still goes back to the original hard drive installation.
It won't boot from the USB. So something else has failed

---

### Post by haqking on 2011-08-20
> **choochoousmc said:**
> I will do the grep......... printout later

I have rebooted. redownloaded the iso to the usb stick.
Used ARK to extract.
Copied everything back to the downloads folder.
The stick is formatted fat32  via ubuntu disk utility

I tried startup creator again. This time it took my password. It says I did a successful create and can now use in any computer after setting boot default to usb.

I did that. Rebooted, but it still goes back to the original hard drive installation.
It won't boot from the USB. So something else has failed

is your BIOS boot order set to allow booting from USB and USB before HDD ?

---

### Post by Old_Grey_Wolf on 2011-08-20
> **choochoousmc said:**
> 
...Used ARK to extract.
Copied everything back to the downloads folder.
The stick is formatted fat32  via ubuntu disk utility...


You don't extract the iso. You just use USB Creator to make a live USB from the iso.

---

### Post by haqking on 2011-08-20
> **Old_Gray_Wolf said:**
> You don't extract the iso. You just use USB Creator to make a live USB from the iso.

+1 didnt see that bit.

i agree

---

### Post by Topsiho on 2011-08-21
> **choochoousmc said:**
> 
And I did get a procedure here a year ago to become the permanent SUDO user.


First: I didn't know or realize it is against the forum rules to give this procedure.

But it is very unwise to break one of the main security properties of Ubuntu.

Being root permanently puts your system into serious danger. Might as well stay with Windows that way. First you can break your system, on purpose, if you want to, but also accidentally, which you most certainly don't want. And if your computer is cracked by someone on your account, as a root, then (s)he can do this for you. For free.

Then it's far better to bear some little irritation of having to sudo and give your password once in a while. Makes it easy to remember it. Hope it is a STRONG password, it's your main defence against an angry outside world :)

Topsiho

---

### Post by choochoousmc on 2011-08-22
> **Old_Gray_Wolf said:**
> You don't extract the iso. You just use USB Creator to make a live USB from the iso.

I know that but the creator woulf not accept the password. And in the end the ark and creator created the same files. But more later in a stand alone post.

---

### Post by choochoousmc on 2011-08-22
> **haqking said:**
> is your BIOS boot order set to allow booting from USB and USB before HDD ?

Yes!!

---

### Post by choochoousmc on 2011-08-22
> **haqking said:**
> +1 didnt see that bit.

i agree

I Know the procedure. It just was not working.

---

### Post by choochoousmc on 2011-08-22
> **Topsiho said:**
> First: I didn't know or realize it is against the forum rules to give this procedure.

But it is very unwise to break one of the main security properties of Ubuntu.

Being root permanently puts your system into serious danger. Might as well stay with Windows that way. First you can break your system, on purpose, if you want to, but also accidentally, which you most certainly don't want. And if your computer is cracked by someone on your account, as a root, then (s)he can do this for you. For free.

Then it's far better to bear some little irritation of having to sudo and give your password once in a while. Makes it easy to remember it. Hope it is a STRONG password, it's your main defence against an angry outside world :)

Topsiho

Neither did I.  It must be a relatively new thing as I got it about a year ago, but apparently forgot to save it.
Unless the supercomputer got lucky, my 15 character password supposedly would taske longer to extrapolate than any of us are ever  going to live.

---

### Post by choochoousmc on 2011-08-22
ok thanks to all that proffered help.
But for some reason the extract never did work right.
After a reboot, it took my password, but never would do an install and an upgrade.

But here is a possible solution why.   I was trying to jump a version from 10.04 to 11.04.

The upgrade manager during all this, finally notified me there was a newer version 10.10
I let the manager do the upgrade. Then an hr later said there was 11.04 available.
I did that upgrade and am now using 11.04

However, never did get it to perform the live usb. The creator did make a live USB  but it never did boot from it or allow me to install it.

---

### Post by haqking on 2011-08-22
> **choochoousmc said:**
> ok thanks to all that proffered help.
But for some reason the extract never did work right.
After a reboot, it took my password, but never would do an install and an upgrade.

But here is a possible solution why.   I was trying to jump a version from 10.04 to 11.04.

The upgrade manager during all this, finally notified me there was a newer version 10.10
I let the manager do the upgrade. Then an hr later said there was 11.04 available.
I did that upgrade and am now using 11.04

However, never did get it to perform the live usb. The creator did make a live USB  but it never did boot from it or allow me to install it.

you mention the extract ?  what extract, extract of what ?

---

