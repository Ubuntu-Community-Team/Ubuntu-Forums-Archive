---
title: "I need help disabling the ridiculously loud pc beep."
date: 2009-08-05
forum: General Help
---

### Post by dennyx13 on 2009-08-05
Hey,
I'm running jaunty on a compaq presario f500.
Whenever the computer shuts down, or i accidentally hit a key like the right key on a text and it won't move right it makes an insanely loud pc beep.
That was a horrible description of when it happens, but it's pretty much whenever i do stuff like that.
how do i disable this?
I've already tried sudo modprobe -r pcspkr or something like that. can not remember the exact command. but that didn't work.
Help is greatly appreciated!

---

### Post by gldearman on 2009-08-05
Tough one.

You do know that

```
$ sudo modprobe -r pcspkr
```

will only work until your next reboot, right?  So, if you are saying that it didn't work, are you sure?  Have you rebooted the computer since?

If that command really wasn't working, then make sure that the pcspkr module is even relevant to your machine.  You may be disabling the wrong module.  Reboot, then type

```
lsmod | grep -i pcspkr
```

If you get no output, then the pcspkr module isn't even being loaded when Ubuntu starts, so disabling it will do nothing.

Let us know how this turns out.  Maybe we can fix your problem yet.

---

### Post by gldearman on 2009-08-05
You know what, there's a better way.

Don't bother screwing around with kernel modules, trying to find the one that controls the system beep and disable it.

There is a package in the repository that will redirect the system beep from to your regular sound card.  It's called softbeep.  Try installing that with Synaptic and see if it helps.

---

### Post by philcamlin on 2009-08-05
or you could just unplug it physically from your pc

---

### Post by dennyx13 on 2009-08-05
ran the command you posted and got the result
> dennis@dennis-laptop:~$ lsmod | grep -i pcspkr
pcspkr                 10496  0 


so not sure what that means.
but i'll try that softbeep app real quick though.

---

### Post by michy99 on 2009-08-05
I have a pair of wire-cutters if you want to borrow them.

---

### Post by gldearman on 2009-08-05
What your output means is that you *are* running the pcspkr module, so disabling it should solve your problem.  It is, essentially, the device driver for the speaker that makes that beep.  So, if it isn't running, that beep goes away.

Try this if softbeep doesn't help:

To disable the module, type this:
```
sudo modprobe -r pcspkr
```

Then, check to see if that worked, by typing:
```
lsmod | grep -i pcspkr
```

If the second command gives you no output, then you have successfully disabled the module.  Check to see if that makes the system beep go away by trying to make your computer make that annoying beep.  If it beeps, then that didn't help.  If you can't make it beep, then your problem is fixed ... but only until your next reboot.

To make that temporary solution permanent, you will have to blacklist the pcspkr module.  That means editing your blacklist file.  Type the following:
```
sudo gedit /etc/modprobe.d/blacklist.conf
```

A text editor window will open.  Scroll to the bottom of the file.  Add this line:

```
blacklist pcspkr
```

Save and close.  That should render the temporary solution permanent.

---

### Post by dennyx13 on 2009-08-06
AWESOME. the sound of silence is epic. 
I think i saw what i did wrong. I might have misspelled blacklist.conf and made a blacklist.comf file before. :S whoops. think i just misread it when i did it the first time. 
Definitely resolved now though. 
I was just about ready to take you up on the offer for wire clippers michy >.>
Thanks to everyone for the quick replies and good help!

---

