---
title: "Lost gui after ending xorg process."
date: 2011-12-03
forum: General Help
---

### Post by Alexalad on 2011-12-03
In short, I checked my system monitor a few weeks ago and went to the tab "processes." I noticed that "xorg" was taking up 100% of my cpu and I selected it, then clicked "end process." Immediately afterward, my computer restarted and now I don't have a gui. I have a fullscreen terminal.
I'm not very experienced with ubuntu  (obviously). And when I use startx, I get this output:
```
xauth: /home/*username*/.Xauthority not writable, changes will be ignored
xauth: error in locking authority file /home/user/.Xauthority

exec: 3: /usr/bin/X: not found
giving up.
xinit: no such file or directory (errno 2): unable to connect to X server
xinit: no such process (errno 3): server error.
xauth: error in locking authority file /home/user/.Xauthority

```

I assumed it was just a package problem, so I uninstalled xorg, xserver-xorg and ubuntu-desktop. But when I tried to install them, it output that the packages couldn't be found. Anyone have any ideas as to what the problem is or more importantly, is it fixable? I'm still not even sure how ending a process affected my whole gui. Luckily, I have a live USB and have already backed up all my important files to an external hardrive.

---

### Post by carranty on 2011-12-03
Well I'm not surprised the computer restarted when you shutdown xorg - you shouldn't really be stopping processes unless you know what they do - but it shouldn't have caused any persistent problems, it should have been fine after a reboot.  What else did you do in that session (between the time you turned on the computer and stopped xorg)?  

Have you not had a gui at all for the last few weeks, or does it sometimes work and sometimes not?

When you say you use startx what do you mean?  Are you typing startx in the terminal and hitting enter?  Do you log into this terminal first, do any error messages come up before you type *startx*?

Can you paste the output of your xorg configuration file to this thread, it should be in /etc/X11/xorg.

Also, please paste the output of 

```
ls -l /usr/bin/X
```and 

```
ls -l /home/user/.Xauthority
```EDIT : Before you do all that, I've read that some people have had success simply by deleting the Xauthority file and rebooting.  I wouldn't recommend deleting it, but rename it as something else 
```

cd 
mv .Xauthority .XauthorityBak
```and then reboot.  You may need superuser privileges for that last bit, depending on the permissions of the file

---

### Post by Alexalad on 2011-12-03
Haha, yeah, I figured that out the hard way.

In that particular session, I didn't do anything because everything was so slow as soon as I booted up. That's why I ended xorg, thinking it would help. I might (i'm not sure) have updated some packages in the session before.

And, no. The gui has never worked since then.

Um, I login, and everythings fine. No errors or anything. After I login, I type startx. So yes, I type startx in the terminal then press enter. And no errors occur until I press enter.

My xorg.conf file looks like this:
```
Section "screen"
	Identifier	"default screen"
	Defaultdepth	24
EndSection

Section "module"
	Load "glx"
EndSection

Section "Device"
	Identifier	"default device"
	Driver	"fglrx"
EndSection
```

Sudo ls -l /usr/bin/X output:
-rwsr-sr-x 1 root root 9664 2010-04-08 18:53 /usr/bin/X

Sudo ls -l /home/username/.Xauthority output:
-rw------- 1 root root 0 2011-11-29 17:51 /home/username/.Xauthority

And I tried your last suggestion, but nothing changed when I reboot.

---

### Post by carranty on 2011-12-03
I think your problem is with the permissions of the Xauthority file, I'm pretty sure it shouldn't belong to root, though i don't have one of my own to compare it to at the moment.  

If you haven't already done so, copy .XauthorityBak back to .Xauthority and type

```
sudo chown username .Xauthority
``` replacing 'username' with your username and then reboot.

---

### Post by Alexalad on 2011-12-03
I copied back, entered your command, reboot, and no change unfortunately.

---

### Post by carranty on 2011-12-03
I'm not sure then.  I'll get back to you tomorrow when I have access to my 10.04 install.  I'll be able to compare files better then.  Hopefully some one will come along before then who knows more than me!

---

### Post by MG&amp;TL on 2011-12-03
If you haven't had xorg and xserver installed, then it's no wonder that startx can't find /usr/bin/X.

I imagine that you will not have your GUI back until you install those packages. Could you give us the exact error message that it outputs when you try and install those packages?

---

### Post by Alexalad on 2011-12-03
Ok, I just tried to install xserver-xorg, and it output:

Package is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
   xserver-xorg-video-intel xserver-xorg-core
E: Package xserver-xorg has no installation candidate

---

### Post by MG&amp;TL on 2011-12-03
So... install what it suggests. :D

---

### Post by Alexalad on 2011-12-03
I tried, but I got the same output, except there are no packages to replace them.
I still got:
E: Package xserver-xorg-video-intel has no installation candidate

---

### Post by MG&amp;TL on 2011-12-03
Hmmm. Weird. Googling up on apt now about installation candidates. :D

---

### Post by Alexalad on 2011-12-03
If it changes things, I downloaded packages: xorg, xserver-xorg, and ubuntu-desktop. I put those packages on an external usb. Then I took the packages and copied them to my /var/cache/apt/archives directory, because somebody told me that should allow me to install the 3 packages...which it did not, obviously.

Also, I don't know how packages are installed and what not, but it might be worth noting, that I have no internet access from the terminal. I've tried connecting using the terminal, but I always get an error. I had wifi before my gui broke, too.

---

### Post by MG&amp;TL on 2011-12-03
Oh. Okay, fairly simple then, I should think.

First of all, you can install debian packages by copying them from a USB and using:

```
cd <folder containing debs>
sudo dpkg -i *.deb
```

Secondly, packages are typically installed by downloading a package, setting up the necessary records of what goes where, and calling dpkg. :)

---

### Post by Alexalad on 2011-12-03
I also get this dependency error sometimes when I try apt-get install commands:

E: unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

When I try the -f form of the command I get something very similar:

The following packages have unmet dependencies:
Xserver-xorg:	Depends:	xserver-xorg-core (>= 2:1.7) but it is not installable
	Depends:	xserver-xorg-video-all but it is not installable or
		xserver-xorg-video-6
	Depends:	xserver-xorg-input-all but it is not installable or
		xserver-xorg-input-7 but it is not installable
	Depends:	xserver-xorg-input-evdev but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by Alexalad on 2011-12-03
The dpkg command output:
dpkg: dependency problems prevent configuration xserver-xorg:
xserver-xorg depends on xserver-xorg-core (>= 2:1.7); however:
	package xserver-xorg-core is not installed

And it says this package depends on a bunch of other packages that start with xorg or xserver.

---

### Post by MG&amp;TL on 2011-12-03
Hmm. Two ways around this.


1. Get your wifi to connect via command-line, possible, just can vary wildly in difficulty from person to person. This should autmagically install deps.

2. Manually (yes, I'm sorry) download all of the X stuff (and their deps), then dpkg them.

I can't really help to got your internet connected, but there are several who can. 

3. Reinstall. Backup your stuff, then nuke. If neither of the above fix, do that.

---

### Post by Alexalad on 2011-12-03
Ok, I think I'm going to try do it manual (here comes a long, fun saturday night) because I've already spent hours trying to connect to my wifi. But there were SO MANY PACKAGES. Sigh...Welp. Better get started, wish me luck!

---

### Post by MG&amp;TL on 2011-12-03
Wish you the best of luck. I do sympathise, I have had to do this on a debian install at one point. And do them one by one, apt doesn't usually remove all of the packages that a package depended on.

And if you do get it working, it's probably the best-loved ubuntu ever! :)

---

### Post by Alexalad on 2011-12-03
Ok, so after the manual method didn't work. I found a way to connect to wifi. So how can I use this to help me because trying to install xorg just output the same thing when I didn't have wifi. And yes, i'm positive i'm connected because ping is working fine. Any ideas.

---

### Post by MG&amp;TL on 2011-12-04
Okay, so what (exactly) does it say when you install:

```
sudo apt-get install xserver-xorg-core
```

?

---

### Post by kjphilips on 2012-06-06
> **carranty said:**
> 

```

cd 
mv .Xauthority .XauthorityBak
```

and then reboot.  You may need superuser privileges for that last bit, depending on the permissions of the file



I used ctrl + alt + F1 to get to a terminal and was having one heck of a time trying to get the desktop back up. I renamed the .Xauthority file then rebooted and... all is well!

I had been stuck in a log-in loop this worked for me! Thank you!!!!

---

