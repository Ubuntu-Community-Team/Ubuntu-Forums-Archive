---
title: "Can Ubuntu become XP ??"
date: 2010-04-02
forum: General Help
---

### Post by Sdream on 2010-04-02
[SIZE=4][COLOR=Navy]1.
The following thread was posted about 20 hours ago:

How to deal with "vwv101@ubuntu:~$_"

Installing Ubuntu 9.04 on Virtualbox

Host : XP Pro. sp2
Guest: Try to install Ubuntu 9.04 by a live CD

At the end of installation,
appears black screen with white words,
at the end of the words there are:
Ubuntu 9.04 ubuntu tty1
Ubuntu login: vwv101
Password: v331024v

Does not login but more words and at the end appears:

vwv101@ubuntu:~$_

Help Please

I am stuck here
What must I do to login?
[/COLOR][/SIZE]
[COLOR=DarkRed]
[/COLOR][SIZE=3][COLOR=DarkRed]2.
An advice was given as the hereunder:

first..edit out your pass from your post

restart it by
Code:

sudo shutdown -r now

should load normally after that[/COLOR][/SIZE]


[SIZE=4][COLOR=Blue]3.
I did and reported:

Thank you, Dayofswords!
Have just tried and the following is what comes out after pressing the Enter key:
Shutdown: illegal time value
Try `shutdown --help' for more information.[/COLOR][/SIZE]


[FONT=Arial Black][SIZE=4][COLOR=DarkRed]4.
Machine was shut down for about 8 hours

The computer is started now
To my surprise
Ubuntu which I tried to install has disappeared from Virtualbox
XP which is the Host  shows up instead[/COLOR][/SIZE][/FONT]


[COLOR=DarkGreen][I][FONT=Century Gothic][SIZE=5]Help please
Why is this?
Is it what "[/SIZE][/FONT][/I][/COLOR][SIZE=3][COLOR=DarkRed][COLOR=DarkGreen]*[FONT=Century Gothic][SIZE=5]sudo shutdown -r now" is supposed to do?[/SIZE][/FONT]*[/COLOR]
[/COLOR][/SIZE]

---

### Post by lisati on 2010-04-02
First of all, go easy on the fonts!
Secondly, it is not a good idea to post your password in a public forum.

---

### Post by HPD2 on 2010-04-02
looks like you did log in but to the CLI (Command Line Interface) instead of the GUI (Graphical User Interface.)

```
sudo shutdown -r now
```that will restart the computer, its does the same as
```
sudo reboot now
```

---

