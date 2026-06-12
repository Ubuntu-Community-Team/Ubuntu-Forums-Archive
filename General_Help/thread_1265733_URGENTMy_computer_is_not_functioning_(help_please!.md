---
title: "URGENT:My computer is not functioning (help please!)"
date: 2009-09-13
forum: General Help
---

### Post by james.exe on 2009-09-13
Acer Aspire One ZA 3
Ubuntu Netbook Remix 9.04
2GB Ram
160GB HD

I was trying to get the hibernate function to work and I pretty much just followed what I was told to do. Using tuxonice wasn't working as described here: 
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

So another user suggested I try another method:
> **P4man said:**
> "sudo shutdown -r now" is a command to reboot the machine, not to hibernate it. Why did you try that? At least I hope it rebooted?

Like I said earlier, i don't know tux on ice, or how to use it, I just helped you with the questions you had. But a quick on their website shows you should do something very different. Try this:

```
sudo /usr/local/sbin/hibernate 
```If that fails, have you tried  uswusp yet?

If not, have a look here:
[https://help.ubuntu.com/community/PowerManagement/Hiberate#uswsusp](https://help.ubuntu.com/community/PowerManagement/Hiberate#uswsusp)


The short version, try:

```
sudo aptitude install uswsusp
```and then

```
sudo s2disk
```


This is what my computer looks like now:
[http://i31.tinypic.com/ei17o9.jpg](http://i31.tinypic.com/ei17o9.jpg)
It's as if my computer is just a terminal now. I trust that there is some way to reverse this effect?
I type in my login/password and still no desktop.

---

### Post by whitethorn on 2009-09-13
hi,

Looks like your X server isn't starting, log in and try typing 

```
startx
```

You can also try if you're using gnome, replace gdm with kdm for kde.

```
sudo /etc/init.d/gdm restart
```

Hopefully this will get your desktop back.

---

### Post by james.exe on 2009-09-13
When I run the first code, it says, "Couldn't create cookie"
When I run the second code, it says, 
"Stopping GNOME Display Manager... [OK]
Starting GNOME Display Manager... [fail]"

---

### Post by james.exe on 2009-09-13
Can anyone else help? Sorry for the impatience, it's just that I have all of my school stuff on my system. I don't want to have to go through the hell of having to reinstall Ubuntu and download all updates, etc.

---

### Post by whitethorn on 2009-09-13
hmmmm I'm stumped.  I hope someone else comes along soon.

---

### Post by james.exe on 2009-09-13
It happened right after I ran ```
sudo s2disk
``` in the terminal if that helps

---

### Post by benj1 on 2009-09-13
well judging by the troubleshooting at the bottom of the swsusp tutorial, when you come out of suspend it drops you in the wrong virtual terminal. 
if so does ctrl-alt-F7 bring up the gui ?

EDIT: dont worry about your work, you can always copy it to a usb disk if the worst comes to the worst
```
cp ~/path/to/work /media/disk
```
will copy it to your usb disk

---

### Post by james.exe on 2009-09-13
Nope, didn't do anything :(

---

### Post by james.exe on 2009-09-13
The problem with that is that I don't exactly know the exact path to my different files..
Is there really no way to fix this?

---

### Post by benj1 on 2009-09-13
well the only thing i can suggest is

```
sudo aptitude purge uswsusp
```
that should get rid of all of the configuration files that it added.

after that shut down and restart

---

### Post by Whiffle on 2009-09-13
Oh theres always a way to fix it.

Looks like GDM is failing to start, likely because your X server is borked for some reason.  I don't know why that would be, but we could look and see why its crashing.

Login to that terminal, and then do:

```

sudo grep EE /var/log/Xorg.0.log

```

And tell us what it says.

---

### Post by james.exe on 2009-09-13
All that gives me is an error message:
EXT3-fs error (device sda1)....
...
...
...
aptitude: error while loading shared libraries: libept.so.0: cannot open shared
object file: no such file or directory

---

### Post by benj1 on 2009-09-13
regarding finding where your stuff is, theres two commands:
cd - change directory
ls - list contents of directory

```
cd ~
``` will take you to your home directory '/home/james.exe' or whatever (you should already be there.

```
ls
``` will show you whats there.

if theyre in Documents

```
cd Documents && ls
``` will change to the Documents folder and list the contents.

---

### Post by james.exe on 2009-09-13
> **Whiffle said:**
> Oh theres always a way to fix it.

Looks like GDM is failing to start, likely because your X server is borked for some reason.  I don't know why that would be, but we could look and see why its crashing.

Login to that terminal, and then do:

```

sudo grep EE /var/log/Xorg.0.log

```And tell us what it says.

I just got a bunch of error messages as well.
**First SDVO output reported failure to sync or input is not trainded!!!**

---

### Post by Whiffle on 2009-09-13
> **james.exe said:**
> All that gives me is an error message:
EXT3-fs error (device sda1)....
...
...
...
aptitude: error while loading shared libraries: libept.so.0: cannot open shared
object file: no such file or directory

Hmm.  That does not look good, almost as if either your drive isn't mounted or something.  What does
```

sudo mount

```

give?

---

### Post by fooman on 2009-09-13
see if running this helps at all:

```
sudo dpkg-reconfigure uswsusp
```

---

### Post by bobbob1016 on 2009-09-13
Have you tried booting into "Recovery Mode"?  Press escape at boot, highlight Recovery Mode and press enter.  Then do fix x or xfix.

---

### Post by james.exe on 2009-09-13
**sudo mount just gives me a whole bunch of lines of code that don't make much sense to me:**
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys tye sysfs (rw,noexec,nousid,nodev)
varrus on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)

**sudo dpkg-reconfigure uswsusp gave me:**
sudo: unable to execute /usr/sbin/dpkg-reconfigure: No such file or directory

---

### Post by james.exe on 2009-09-13
xfix doesn't seem to be working on the recovery mode menu
dpkg-reconfigure: not found

---

### Post by Whiffle on 2009-09-13
Okay it says that your / (root), is mounted, good.

Second command says it can't find that command, bad.

What does "ls /" say?

---

### Post by james.exe on 2009-09-13
> **Whiffle said:**
> Okay it says that your / (root), is mounted, good.

Second command says it can't find that command, bad.

What does "ls /" say?

Desktop Pictures Videos                       output.pdf
Documents Public amsn_received          skype-debian_2.0.0.72-1_i386.deb
Music Templates examples.desktop

---

### Post by james.exe on 2009-09-13
Any other suggestions, guys?

---

### Post by Whiffle on 2009-09-13
I would mount your flash drive and copy your files onto it.  I'm not certain where to go from here as to fixing it though.  If I had it in front of me it'd be a whole lot easier :-P   I'll give it some thought...

---

### Post by james.exe on 2009-09-13
Well I think I'm just going to have to go ahead and reinstall ubuntu seeing as I have no other real options. Thanks, everyone, for the help. If it's one thing I love about the forums, it's the genuine support I get from strangers.

---

