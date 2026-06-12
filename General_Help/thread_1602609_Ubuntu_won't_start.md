---
title: "Ubuntu won't start"
date: 2010-10-21
forum: General Help
---

### Post by nitzan on 2010-10-21
Hi all.

I bought a new computer and installed ubuntu 10.04 about 2 months ago, and until yesterday it worked pretty well.
Last night it acted kind of weird (slow, application would start loading and then just die) so I restarted the machine.
That's when I understood that something bad happened.

When the machine starts and the os begins to load I get a bunch of text that says things like:
mount: mounting /dev on /root/dev failed: No such file or directory

same for sys and proc, there might be much more in the buffer but I can't seem to able to go up.

I did not do any thing special last night and so I'm clueless of the reason for this.
Also, since in this version of ubuntu the boot options are not displayed by default I tried pressing a key on boot in order to try another booting option but when I do that I just get the flickering cursor sign.

I'm already starting to accept the fact that I'll need to re-install ubuntu, but I decided to try here first...  any ideas?

Thanks.

---

### Post by coffeecat on 2010-10-21
> **nitzan said:**
>   any ideas?

Before you go to the trouble of reinstalling Ubuntu, I would check the health of the hard drive from the live CD first. Some research by Google showed that some hard drives failed very early on. These symptoms could conceivably be a failing drive.

Boot up the live CD and go to System > Administration > Disk Utility, highlight the internal drive and view the SMART data. You could run a self-test if you want.

I'm sure the probability of a failing drive is low, but this only takes a few minutes and saves you the aggravation of doing a fresh install only to find the drive fails shortly after.

Apart from that... Sorry, no other ideas.

---

### Post by UnterUn on 2010-10-21
Can you get into/enter into the terminal *at all?*

If you *can* _try_:

```
dpkg-reconfigure gnome
dpkg-reconfigure desktop
sudo dpkg-reconfigure xserver-xorg

```and if that fails try 
```
sudo apt-get install ubuntu-desktop
```There might be another solution if you can enter into the terminal so I'd wait a little while before reinstalling

---

### Post by nitzan on 2010-10-21
I will try the live CD in a few hours and will report the results.

As for the terminal, what i get looks kinda like a terminal, but those commands you wrote are not found.
I get "(initramfs)" and can put input, i click tab for the possible commands but none works (reboot, poweroff, ipconfig, mount...)

Thanks.

---

### Post by nitzan on 2010-10-21
> **coffeecat said:**
> Boot up the live CD and go to System > Administration > Disk Utility, highlight the internal drive and view the SMART data. You could run a self-test if you want.

The disk utility had this to say:
SMART status: Not Supported

and when I do the Check Filesystem I get a "File system is NOT clean."

I have no idea what that means.  I guess though it's not good.
Thanks.

---

### Post by coffeecat on 2010-10-22
> **nitzan said:**
> and when I do the Check Filesystem I get a "File system is NOT clean."

The unsupported SMART status is a frustration but an unclean filsystem is just an unclean filesystem, not evidence of hardware trouble.

It might be repairable. When you get that message, does it give you an option for a filesystem repair? I've not used Disk Utility on an unclean filesystem so I don't know what else it might say. If it does give you that option then try a repair. I don't know whether you did a forced restart when the system "acted kind of weird", because a forced restart can be the cause of this, but for the weirdness I don't know.

If there is not an option for a repair, take a note of the partition device name. It will be something like /dev/sda1 or /dev/sda3. For the following, replace sdaX with sda1, sda2, whatever yours is. Open a terminal in the live session and do this command:

```
sudo fsck /dev/sdaX
```If fsck finds problems it will ask you to make choices with questions that may not be easily understandable. If you want it to press ahead anyway and attempt an automatic repair without asking impenetrable questions, use this command:

```
sudo fsck -y /dev/sdaX
```

---

### Post by nitzan on 2010-10-22
> **coffeecat said:**
> ```
sudo fsck /dev/sdaX
```

Yup, that fixed the problem, THANKS!
It had a lot of fixes to do, but right after I was already able to mount the device and once I restarted everything got back to normal.

I hope that no data got lost, is there any way to make sure?

Also, even before this issue I did encounter a few problems (the computer sometimes get stuck and a restart is needed).
Can this be caused by a hardware problem?

Thank you.

---

### Post by coffeecat on 2010-10-22
> **nitzan said:**
> I hope that no data got lost, is there any way to make sure?

If any stray data is found in a fsck, it will be put into the lost+found folder. You can see this folder by going to Places > Computer > File System, but you won't be able to open it without root privileges. To check what is inside, do this from a terminal:

```
sudo ls -l /lost+found/
```If you get the output 'total 0' there's nothing there.

> **nitzan said:**
> Also, even before this issue I did encounter a few problems (the computer sometimes get stuck and a restart is needed).
Can this be caused by a hardware problem?

Difficult to be sure. Yes, hardware problems such as faulty RAM can cause freeze-ups, but there are often threads with people complaining about freezes so perhaps some combinations of hardware reveal freeze-inducing bugs. I don't know. All I can say is that the only system freezes I have had with Linux is when I have been doing something - ahem - adventurous :wink: or with misbehaving apps. Or a few years ago with a particular motherboard that didn't seem to like certain RAM sticks that worked OK elsewhere. But that one froze up Windows as well.

If you get a lock-up, it's best to use the magic-key combination. This unmounts filesystems properly before shutdown and avoids filesystem corruption. More here:

[http://en.wikipedia.org/wiki/Magic_keys](http://en.wikipedia.org/wiki/Magic_keys)

---

### Post by nitzan on 2010-10-23
> **coffeecat said:**
> If any stray data is found in a fsck, it will be put into the lost+found folder.
Thanks, I was wondering what this folder is all about...
And it's empty so I guess it's all good.

I'm not doing anything "adventurous" that I'm aware of..  most of the time the computer freeze-up is while streaming video using flash.
Also, some programs will all of the sudden terminate (eclipse for example).

I suspect it to be something with the hardware since I have another computer running same ubuntu version and no trouble there (media machine).
The questions is: is there a way to know for sure?  I should still have warranty for most of the parts in the machine, but I can't just go there and say "I think something is wrong"


> **coffeecat said:**
> 
If you get a lock-up, it's best to use the magic-key combination. This unmounts filesystems properly before shutdown and avoids filesystem corruption. More here:

[http://en.wikipedia.org/wiki/Magic_keys](http://en.wikipedia.org/wiki/Magic_keys)
Thanks for this reference, I will read more into it.

---

### Post by coffeecat on 2010-10-23
> **nitzan said:**
> most of the time the computer freeze-up is while streaming video using flash.

I believe I've seen threads where people get freezes when using flash. I never have but flash doesn't have a very good reputation. For the rest...

> **nitzan said:**
> I suspect it to be something with the hardware since I have another computer running same ubuntu version and no trouble there (media machine).
The questions is: is there a way to know for sure?  I should still have warranty for most of the parts in the machine, but I can't just go there and say "I think something is wrong"

Hardware faults can certainly be the cause of freezes but it can difficult pinpointing them. Or, as I mentioned earlier, it could be perfectly good hardware but a certain combination of hardware which unmasks obscure bugs in Ubuntu. Difficult to know.

---

### Post by nitzan on 2010-10-23
> **coffeecat said:**
> Hardware faults can certainly be the cause of freezes but it can difficult pinpointing them. Or, as I mentioned earlier, it could be perfectly good hardware but a certain combination of hardware which unmasks obscure bugs in Ubuntu. Difficult to know.

Well, for the first couple of weeks I had this recurring problem of starting up the computer, it looked like the it's starting to boot but then nothing, just blinking cursor.   I had to press the restart button on the computer over and over until the boot kicked in.
It was very frustrating but then just suddenly stopped happing all together and i suspected that one of the updates fixed that.
Hopefully the same will happen with some more of the problems I'm getting.

Thanks again for the help!

---

