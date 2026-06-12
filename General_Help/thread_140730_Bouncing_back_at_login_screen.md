---
title: "Bouncing back at login screen"
date: 2006-03-06
forum: General Help
---

### Post by silhouette on 2006-03-06
Hi all,

I'm having a problem logging into Ubuntu. First some context: before this happened, I copied a large quantity of files from the other hard drive I have in my machine to the main drive. After this I found I couldn't open any program -- when I tried to do so, I watched the cursor do its bouncing trick for a while, then all was still as if I'd never told the computer anything. I figured a restart should do the trick, so I watched it shutdown and load everything again. Having come back to the login screen, I entered my information and fired away. The screen went blue (being my desktop background color) and for a minute I thought the KDE loading box would appear.... but I was bounced back to the login screen. I tried logging into GNOME, then GNOME Failsafe, and finally Terminal Failsafe. Terminal Failsafe works but the others don't -- I'm bounced back to the login screen every time. (I haven't tried opening a prompt via the grub screen yet, but I'm sure it would work too.)

(I suppose I should add that I originally installed Ubuntu, then added Kubuntu components and KDE programs manually through Synaptic. However everything seemed to be working alright, so that may not have anything to do with this problem.)

Anyway, I'm still a Linux noob (been using it for the past three weeks), so I'm not too versed on Linux commands just yet, enough to solve this anyway. So... what should I do?

---

### Post by romdos on 2006-03-06
sounds like you may be out of space on your hard drive...
at the login screen hit <ctr><alt><F1>
this will bring you to a terminal, login and type:

```

romdos@freekbox:~$ df -h

```
this will show you how much space is left on your drive.

---

### Post by silhouette on 2006-03-06
Okay, I have 1.5 GB left. This should be *plenty* of space to load KDE or GNOME, right?

I'll try mass-rm'ing some of the stuff I tried to copy onto the drive, though, just in case.

---

### Post by silhouette on 2006-03-06
Okay, I deleted some stuff and I now have 7 GB, but it's still not working. Are there any log files I need to check (if so, where might I find them)? Would it help if I re-"apt-get"-ed some packages (kde, or something)?

Anyway, I was able to get in by going through the GRUB selection screen, choosing recovery mode, and running startx... so what does *this* mean?

---

### Post by romdos on 2006-03-06
it sounds like you have plenty of room on the disk...
try booting up as normal, at the login screen switch to a terminal <ctr><alt><f1>
and login, next do:
```

romdos@freekbox:~$ sudo killall gdm

```

to kill gnome's desktop manager, then:
```

romdos@freekbox:~$ startx

```

if X starts normally here the problem may be with gdm's configuration
if this is the case I would do:
```

romdos@freekbox:~$ sudo dpkg-reconfigure gdm

```
then start gdm again:
```

romdos@freekbox:~$ sudo gdm

```

---

### Post by silhouette on 2006-03-06
[QUOTE=romdos]it sounds like you have plenty of room on the disk...
try booting up as normal, at the login screen switch to a terminal <ctr><alt><f1>
and login, next do:
```

romdos@freekbox:~$ sudo killall gdm

```

to kill gnome's desktop manager, then:
```

romdos@freekbox:~$ startx

```
[/quote]
No dice -- I still get bounced back to the Ubuntu login screen. :-?
> 
if X starts normally here the problem may be with gdm's configuration
if this is the case I would do:
```

romdos@freekbox:~$ sudo dpkg-reconfigure gdm

```

I went ahead and tried this anyway, but it came back saying something like, "these changes will take effect as soon as all instances of X were killed", but then that "the reconfiguration failed".
> 
then start gdm again:
```

romdos@freekbox:~$ sudo gdm

```
And of course, this didn't work.

---

### Post by mr.p on 2006-03-07
[QUOTE=silhouette]No dice -- I still get bounced back to the Ubuntu login screen. :-?

I went ahead and tried this anyway, but it came back saying something like, "these changes will take effect as soon as all instances of X were killed", but then that "the reconfiguration failed".

And of course, this didn't work.[/QUOTE]

Have you tried logging in as a different user? Same result?

---

### Post by silhouette on 2006-03-07
[QUOTE=mr.p]Have you tried logging in as a different user? Same result?[/QUOTE]
Oh, cool. Yeah, mysteriously that works. What does that mean, then?

---

### Post by romdos on 2006-03-07
perhaps it is a permissions/ownership problem,
look at the output of:
```

romdos@freekbox:~$ ls -l ~/.Xauthority

```
compare the output of the user that works with the one that does not

---

### Post by silhouette on 2006-03-07
Well, okay, apparently .Xauthority doesn't exist in my home folder. (I don't remember accidentally removing it or anything...) Is there a quick fix to this or am I screwed (i.e. do I have to reinstall)?

---

### Post by romdos on 2006-03-07
I am just guessing here, but try to create a new file called .Xauthority
```

romdos@freekbox:~$ touch .Xauthority

```
change permissions to match what .Xauthority should be:

```

romdos@freekbox:~$ chmod 600 .Xauthority

```

If X still does not work, I would try copying the .Xauthority file from the user that is able to login, and then change the owner and group to your user
to change the owner and group:
```

romdos@freekbox:~$sudo chown $USER:$USER .Xauthority


```

---

### Post by romdos on 2006-03-07
I just deleated both my .Xauthority and .ICEauthority files, logged out and logged back in just fine. They were recreated automatically, so unfortuantly your problem may lie elsewhere. 
You should compare your hidden files ( . files ) that you can see with ls -a with the hidden files of a user that can login. If worse comes to worse you can deleate your user account and recreate it

---

### Post by silhouette on 2006-03-07
Okay, I tried deleting .Xauthority and .ICEauthority (.Xauthority did actually exist, I just wasn't expecting it to come first in the sorted list) just to see what would happen, and .ICEauthority was created but .Xauthority wasn't (and of course it bounced me back again). I don't really have time to futz with this more right now, but I think I might just recreate the user account like you said. Thanks for the help!

---

