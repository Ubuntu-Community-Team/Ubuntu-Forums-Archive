---
title: "How to make a command auto run after startup?"
date: 2009-09-13
forum: General Help
---

### Post by Floyd770 on 2009-09-13
I already apologize, I'm sure this topic is beat, BUT...  

I'm not really sure what to search for here..

I have to run

```
sudo modprobe ndiswrapper
```

every time I reboot this machine in order to get my wireless card activated.

There has got to be a better way.  

Is there a simple way to have this run on its own after the desktop loads?

I would guess there is a file I just need to add that line to and I'll be good to go?  How does it handle running an SUDO command without being able to be prompted for the password?

I'm using Jaunty btw.. 32bit if it makes any difference for this.

Many thanks in advance..

I'm pretty new to this, but I follow directions well.

---

### Post by harrismh777 on 2009-09-13
hi,
You need to add ndiswrapper to the end of your modules file.  You could try:

sudo gedit /etc/modules


also see:  

[https://wiki.ubuntu.com/SetupNdiswrapperHowto?action=show](https://wiki.ubuntu.com/SetupNdiswrapperHowto?action=show)

---

### Post by stderr on 2009-09-13
You need 

```
**gk**sudo gedit /etc/modules
```

but otherwise that's correct :) (@harrismh: I *hate* the need for gksudo, I really do... and I never used to remember it either for ages when I started using Ubuntu :)) 

For other startup scripts, you can use System->Preferences->Startup whatever-it's-called-in-jaunty

---

### Post by Floyd770 on 2009-09-13
Fantastic!

Thanks so much!

Do commands run in the modules file automagically run as root?

---

### Post by stderr on 2009-09-13
You can't put commands in /etc/modules; these are names of modules to load only. 

So if you run ```
lsmod | grep ndis
``` to get a listing of loaded modules matching the "ndis" string, you should see "ndiswrapper" in there. 

To run commands at boot you need to use a different method:
 o to run an application/script when the graphical interface starts up, use the System->Preferences->whatever-it's-called menu option (sorry, running Ubuntu Intrepid Ibex here, and it's called something different to Jaunty), or
 o to run a bash script at textual bootup, it'd be best to use method 3 under [https://help.ubuntu.com/community/UbuntuBootupHowto]("https://help.ubuntu.com/community/UbuntuBootupHowto")

---

### Post by sgosnell on 2009-09-13
Open System/Preferences/Startup Applications.  Click on Add.  Give it whatever name you like.  For command, put sudo modprobe ndiswrapper.  Add any comments you want, and you're done.  Reboot, and it should be run automatically.

---

### Post by renkinjutsu on 2009-09-13
that only works for commands the user has privelages for.
and the sudo won't be able to prompt the user for a password without a terminal. For commands to run as root (if it doesn't require a gui, you can edit the /etc/rc.local file and chmod +x it)

---

### Post by LoREZ on 2009-09-13
I have startup issues as well, but I know about Startup Applications.  It's not working.

Where is the text file that Startup Applications writes to?  

I'm trying to get gnome-do to startup and it won't, even though it's checked inside Startup Applications and inside gnome-do's preferences.  My thinking is that the gui programs tripped over eachother at some point and wrote unexecutable code to the file.  This happened with my GRUB file, and I had to do some manual house-cleaning, which corrected the problem. I'm hoping that will work here (crosses fingers).

---

### Post by renkinjutsu on 2009-09-13
doesn't gnome-do add itself to the startup anyway? there's a box in the preferences right?

---

### Post by LoREZ on 2009-09-13
Yes it does, however it is not actually starting up for me, even though the preference box is checked, in addition to the checkbox in the Applications Startup being checked.  As far as I can tell, it's the only program that is doing this on my system.

---

