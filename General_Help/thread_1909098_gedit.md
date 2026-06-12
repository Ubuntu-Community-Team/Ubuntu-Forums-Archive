---
title: "gedit"
date: 2012-01-14
forum: General Help
---

### Post by Datahead2010 on 2012-01-14
Hello
Being a complete novice to Linux,I am trying to do some mods on my desktop and need to edit a file via the terminal and I keep getting an error and the file does not change after I edit it. Any help would be greatly appreciated. See below for info:


datahead@ubuntu:/usr/share/gnome-session/sessions$ sudo gedit gnome-with-compiz.session

(gedit:2622): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.ETCJ8V': No such file or directory

(gedit:2622): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2622): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.JGIM8V': No such file or directory

(gedit:2622): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
datahead@ubuntu:/usr/share/gnome-session/sessions$

---

### Post by drs305 on 2012-01-14
It looks like your system is having trouble either accessing or creating the system file which tracks recently-used files. Try creating it manually:

```
sudo touch /root/.local/share/recently-used.xbel
```

---

### Post by spacecheck on 2012-01-14
> **drs305 said:**
> It looks like your system is having trouble either accessing or creating the system file which tracks recently-used files. Try creating it manually:

```
sudo touch /root/.local/share/recently-used.xbel
```

Just curious, but shouldn't the message simply be ignored, since the user "root" will never need to click on a link to a "recently used" file in "root's" home folder??

spacecheck
(just don't let it bounce)

---

### Post by MG&amp;TL on 2012-01-14
Sanity check: I get this all of the time, but the file is changed. Are you sure you saved it?

Just checkin' :)

---

### Post by Datahead2010 on 2012-01-14
DRS305
No that didn't work. (See Below) Not to mention I can not get to the root directory to see what is there, as it keeps saying I do not have permission. When I installed the system it only asked for one password. What is with that? 


datahead@ubuntu:/$ sudo touch /root/.local/share/recently-used.xbel
touch: cannot touch `/root/.local/share/recently-used.xbel': No such file or directory
datahead@ubuntu:/$

Also as to the file changing what it does is creates a file with the same name with a ~ on the end

---

### Post by spacecheck on 2012-01-14
> Not to mention I can not get to the root directory to see what is there, as it keeps saying I do not have permission.
There are simple ways to do this, but I meant in my post, that it didn't seem necessary to bother creating it.
> When I installed the system it only asked for one password. What is with that?  Designed to reduce user error by limiting the amount of potentially damaging activity that would be possible during a root session, for example. Certain tools can be started as su, however, which inherently enable root privileges nonetheless. Much greater care must then be taken, to prevent system damage...
> Also as to the file changing what it does is creates a file with the same name with a ~ on the end 	
In this instance, I assume it cannot save the desired changes because the file "gnome-with-compiz.session" may already be in use during the active session.  This might not be the case at runlevel 3, for example, where the session would  have neither Gnome nor compiz operating. I suspect there may be an additional tool used to modify compiz settings during the active session, but as I've never bothered with such things, I can only guess.

Good luck!

---

### Post by Datahead2010 on 2012-01-14
Thank you everyone for all the help. What I ended up doing was using the edited files with the ~ on the end and deleting the original file and then renamed the edited ones and got the thing to work. There is more than one way to skin a cat as they say.

Thank you everyone for the good advise. I am sure there will be many other questions to come, but we made it through the first hurdle and my desktop is working like a dream.

Thank you all
Ron

---

### Post by mörgæs on 2012-01-14
Good, then please mark the thread 'solved' using 'thread tools'.

---

### Post by drs305 on 2012-01-14
> **spacecheck said:**
> Just curious, but shouldn't the message simply be ignored, since the user "root" will never need to click on a link to a "recently used" file in "root's" home folder??


Well, here's an example: I use gedit as root a lot to open grub files. The files I open with gedit as root are listed in gedit's 'Recent' list, and are different than those when I open gedit as a normal user. Gedit get's the 'Recent' list from root's recently-used.xbel file as far as I know.

---

### Post by spacecheck on 2012-01-15
Thanks for the response, drs305.

> I use gedit as root a lot to open grub files.
Do you mean, you actually login as the user "root", thus having automatic access to the "root" home folder? Or, do you mean you are logged in as normal user and use "sudo" for root privileges, which would not give you (or gedit) access to the "root" home folder?

If the former, I see no reason why root's "recent-used" file would not automatically be created & modified.

If the latter, I do not see how the standard user (or his "sudo" command) would have  the extended privileges to modify the "root" home folder, including creating & modifying the root recently-used.xbel file.

Nor do I see why the user would need to, from the standard account, since the "recently-used" links to these files will never appear to that user, at least not while using the standard account. Right? Or, am I just overlooking something?

---

### Post by drs305 on 2012-01-15
> **spacecheck said:**
> Do you mean, you actually login as the user "root", thus having automatic access to the "root" home folder? Or, do you mean you are logged in as normal user and use "sudo" for root privileges, which would not give you (or gedit) access to the "root" home folder?

If the former, I see no reason why root's "recent-used" file would not automatically be created & modified.

If the latter, I do not see how the standard user (or his "sudo" command) would have  the extended privileges to modify the "root" home folder, including creating & modifying the root recently-used.xbel file.

Nor do I see why the user would need to, from the standard account, since the "recently-used" links to these files will never appear to that user, at least not while using the standard account. Right? Or, am I just overlooking something?

I do not log in as root; I use 'gksu gedit'. When I open up system files it does change the /root/.local.... *.xbel file to reflect the files I have just accessed via gedit (opened with gksu).

As for exactly how/why it is supposed to work, I don't have any inside knowledge. My original post was just to suggest that if the system was complaining about not being able to find a file, creating it may have solved the issue since this file isn't very important in the grand scheme of running the OS.

---

### Post by spacecheck on 2012-01-16
I see. You create the /folder/file simply to keep gedit from complaining, since it has no other real purpose or use for you.

This form of complaint has appeared in each Ubuntu system and derivate I have ever used, any time I have called a gksu command. I have simply ignored it, thinking it wasn't worth the bother to change or to complain.

If it is appearing for everyone else as well, however, it would seem responsible to pass the developers a tip about it, so they could waste a little time removing a tiny problem which makes a lot of new folks unnecessarily worried.

Thanks for the imput!

---

### Post by Derek Karpinski on 2012-01-16
The fix:
 
```
sudo mkdir -p /root/.local/share
```

---

### Post by vuarnet on 2012-01-19
> **Derek Karpinski said:**
> The fix:
 
```
sudo mkdir -p /root/.local/share
```

^^^ has anyone tried this? i'm getting a similar error and would like to fix it... i dont like stuff printing in my terminal that i can't fix :-/

---

### Post by drs305 on 2012-01-19
> **vuarnet said:**
> ^^^ has anyone tried this? i'm getting a similar error and would like to fix it... i dont like stuff printing in my terminal that i can't fix :-/

It's a simple command run as root that creates a folder. It's similar to what I originally proposed, but backs it off one step to make sure the /root/.local/share folder exists (before trying to make the /root/.local/share/recently-used.xbel file).

*As long as you enter the command correctly*, it will create the subfolder and should allow the file to be created when gedit is used as root.

If it works, you won't get the ...xbel.. error message. If it doesn't, it isn't going to harm your system in any way.

---

### Post by Derek Karpinski on 2012-01-19
Yes, I tried it. If you don't trust it, break down the command.

sudo is execute with root privileges
mkdir -p is make directory, and if parent doesn't exist, make it too. (/root/.local doesn't exist by default.) If you don't add the -p flag, you need to make /root/.local, then /root/.local/share

```
man mkdir
```

  The error is harmless, and comes up because that dir doesn't exist.

Good for you for not trusting code.

---

### Post by dcstar on 2012-01-20
> **Datahead2010 said:**
> Hello
Being a complete novice to Linux,I am trying to do some mods on my desktop and need to edit a file via the terminal
........

[http://www.liberiangeek.net/2011/12/add-open-as-administrator-to-nautilus-context-menu-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/12/add-open-as-administrator-to-nautilus-context-menu-in-ubuntu-11-10-oneiric-ocelot/)

---

