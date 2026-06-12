---
title: "Two Terminals ?"
date: 2009-07-14
forum: General Help
---

### Post by Cool Javelin on 2009-07-14
Each time I launch a terminal, I get 2.

This happens no matter how I launch it, If I use the "Applications-Terminal," "Applications-accessories-terminal" or Right click on the desktop and select "Open Terminal here," I get the same results.

This behavior existed in Hardy (8.04) and continues with Jaunty (9.04)

Since I couldn't find any other help on the forum, I suspect it might be a hardware issue, but everything else seems to be working OK.

I have a very old, very slow machine.

Can anyone help me with fixing this?

Thanks in advance for your help.

Mark.

---

### Post by JohnnySage50307 on 2009-07-14
Well, I'm sure you can guess that it's not a bug in the Ubuntu system, being as no one else seems to be reporting this symptom.
 
On a GenToo machine in Pitt's CS Dept, I had this same issue; the desktop enviroment there was KDE, though, so I don't know what could be causing it.  I just moved to a different machine that worked.
 
Given how you described your system as aging, maybe something hardware-wise is causing this phenomenon?

---

### Post by CatKiller on 2009-07-14
> **Cool Javelin said:**
> I suspect it might be a hardware issue

I don't see how, unless you count double-clicking on something that should be a single click as a hardware issue :)

Have you perhaps put a line that launches a terminal in one of the configuration files that get run when you start a new shell, such as ~/.bashrc? Do you get two new terminal windows if you run xfce4-terminal from an existing window? If so, do you get any output that says why? Does Xfce's terminal have a profile configuration that might be launching the second terminal?

---

### Post by Cool Javelin on 2009-07-14
CatKiller:

I did think about accidentally double clicking,

When I manually type what you suggest, (xfce4-terminal) I do get two still.

I see xfce4-terminal is actually an executable Is this the terminal program itself? or is it an indirect launcher?

Perhaps I can switch to another terminal emulator, any clues on which to use? Maybe I can change one shortcut to test another and see if the symptom stays.

Thanks.

---

### Post by kerry_s on 2009-07-14
try "**xterm**" it should be installed already.

---

### Post by CatKiller on 2009-07-14
> **Cool Javelin said:**
>  When I manually type what you suggest, (xfce4-terminal) I do get two still.

It sounds like the second one is being loaded by a profile or preference somewhere then, rather than being a problem with your launchers.

Another possibility, other than xterm, is gnome-terminal. I don't know how much of the extra Gnome bits it would bring with it.

---

### Post by Cool Javelin on 2009-07-14
Both the Hardy, and Jaunty installations are from scratch. (I had difficulty with the Jaunty upgrade and needed to repartition.)

I haven't modified any profile or preferences yet.

I created a launcher (on my desktop) to start xterm as Kerry_s suggested and I only get a single instance.

That gave me the idea to create a launcher on the desktop to start xfce4-terminal. and when run, I do get the two instances.

I don't have an issue with xterm (as opposed to xfce4-terminal) but I notice there are no font choices. I actually like that as the fewer choices you have the more performance you can get.

As for the Gnome-terminal, until I have a problem, I would rather stay small.

Might someone know where I could view the source code for the xfce4-terminal? I am suspecting there is an issue there.

Thanks, Mark.

---

### Post by CatKiller on 2009-07-14
> **Cool Javelin said:**
>  Might someone know where I could view the source code for the xfce4-terminal?

Provided you have an appropriate deb-src entry in your sources.list, you can use ```
apt-get source xfce4-terminal
```to download the source code to the current directory. I don't think that you'll find the problem there, though, or it would probably have already been reported as a bug and show up prominently in searches. Feel free to look, though.

It seems much more likely to me that it's a problem with a setting in the Home folder somewhere instead. Do other users of these machines experience the same behaviour?

---

### Post by kerry_s on 2009-07-14
do you have a intel vid card?

i use xterm on my xfce4, cause xfce4-terminal has been having problems with intel vid drivers.

just switch to another terminal , if you liked xfce4-terminal than i would suggest "roxterm" it's pretty close.

**sudo apt-get install roxterm**

---

### Post by Cool Javelin on 2009-07-14
CatKiller, Thanks, I will take a look at the source, but as you say, I doubt I will find a problem.

kerry_s, Yes, in fact the video chips are Intel. They are on the motherboard and I was going to put a daughter board as I cannot get xubuntu to give me any higher resolution then 800x600.

Maybe I will give that project a higher priority and get back here.

I will let you all know, thanks for the help.

Mark.

---

