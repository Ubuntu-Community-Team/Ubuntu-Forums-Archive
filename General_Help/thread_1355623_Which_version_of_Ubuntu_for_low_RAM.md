---
title: "Which version of Ubuntu for low RAM?"
date: 2009-12-15
forum: General Help
---

### Post by Greg Xix on 2009-12-15
Currently running an old Compaq Evo D500 as my "2nd computer". As some of you might be aware, the old Comapq Evo's are NOT USB bootable/Live USB capable. So, I need to use the much slower Live CD. Long story, short: I need to "Live Boot" this machine for a few important tasks a handful of times a week while running something else on my "Main computer".

Without permanent changes to the HDD, I always need to "install" a few small/medium sized programs within the Live CD environment; but the Live CD + Programs max out that 256MB RAM pretty quickly. Not to mention it performing pretty slow.

As a test, I temporarily downgraded my Main computer to 1GB RAM and did a dry run with the Live CD + normal program installs + usual tasks and that setup proved to be satisfactory.

So my 2 options were:

1. spend $125 on a "better clunker" that is USB Bootable with more RAM
2. spend $35 to punch the RAM up currently from 256MB to 1GB (3 slots: 2x256 + 1x512)

So I chose the 2nd. And the 256 and 512 sticks are currently being shipped.

Ultimately, my question is: Even with the upgraded RAM; to maximize it, what Ubuntu version should I use? The Live CD I currently use is a 9.04, but would going down to a Live CD of 8.10, 8.04 or even 7.04 be less RAM intensive? or would that only produce negligible gains for sacrificing upgraded Ubuntu enhancements?

I know, I know. Many of you will say to try Xubuntu. Well I didnt like 8.04 all that much. Although, now I am currently downloading 9.10 and will try that next.

---

### Post by nothingspecial on 2009-12-15
I would suggest crunchbang, or like me Ubuntu minimal with openbox.

Which is what Crunchbang is but with alot of default apps and a few handy scripts and predone config files so you don`t have to do it all your self.

So if you like the tons of apps crunchbang installs with then go with that, or if you would like alternative ones, do the second.

[HINT] - its much easier to edit crunchbangs rc.xml and menu.xml to your own liking than starting with openbox from scratch even if you go the ubuntu minimal route. Oh and a couple of the scripts in /usr/bin/crunchbang come in handy too - [/HINT]

I even do this with my machines that are perfectly capable of running Ubuntu.

---

### Post by plucky on 2009-12-15
Can you sacrifice some Hard Disk space?

Create a linux swap partition which the Live disk can use as extra memory space when the physical memory is full.

Quicker than having to reload programs from the Live CD.

Good Luck

---

### Post by audiomick on 2009-12-15
This might interest you:
[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

---

### Post by benj1 on 2009-12-15
if youre just going to be using it as a live cd why not something like puppy

---

### Post by Cheesemill on 2009-12-15
Is there a reason you can't install an OS onto this machine? Running from a Live CD will always be alot slower than an installed OS.

---

### Post by snowpine on 2009-12-15
Ubuntu's Live CD is horribly slow; Ubuntu just wasn't designed to be used that way. I really recommend something like Puppy that's a) designed specifically to run from a live CD; b) saves your session to a USB stick or file on your hard drive, so you don't have to reinstall those applications every time you boot up.

---

### Post by Greg Xix on 2009-12-15
> **audiomick said:**
> This might interest you:
[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

> **Cheesemill said:**
> Is there a reason you can't install an OS onto this machine? Running from a Live CD will always be alot slower than an installed OS.


Actually, I do have 9.04 Installed on the HardDrive. But there are a few programs I use that I don't want permanently installed on the computer, which is the reason I use the Live CD environment. That also goes for any changes to a Live CD itself, hence the Persistence/Live CD-rw rig won't work for me either (although its kind of a cool idea). I sort of need to have a "virgin" computer environment for each and every Live CD boot. I know it sounds weird, but I have my reasons and everybody's situation is different.


As for the Puppy. I really would prefer a Debian-based environment because I install 3 '.deb' files that I have to rely on. So I tried Crunchbang and there was no desktop environment at all. Frankly, I just don't want to spend 10mins "tweaking it" every Live CD session before getting to work on my regular stuff.


I just need something ready to go out of the box. So I am gonna stick with a "Live Ubuntu CD" since I am upgrading the RAM from 256 to 1GB anyway. And I know the basic Ubuntu environment pretty well.

So back to my original question: Would an earlier version of Ubuntu use a significant amount less RAM? Like Feisty or Hardy? If Lubuntu was out, I would probably use that. Knoppix for some reason has a lot compiz enabled on bootup and its really annoying.

Thanks for the suggestions, I know we all have our pet flavors of Linux outside of Ubuntu.


.

---

### Post by benj1 on 2009-12-16
> **Greg Xix said:**
> Actually, I do have 9.04 Installed on the HardDrive. But there are a few programs I use that I don't want permanently installed on the computer, which is the reason I use the Live CD environment. That also goes for any changes to a Live CD itself, hence the Persistence/Live CD-rw rig won't work for me either (although its kind of a cool idea). I sort of need to have a "virgin" computer environment for each and every Live CD boot. I know it sounds weird, but I have my reasons and everybody's situation is different.


As for the Puppy. I really would prefer a Debian-based environment because I install 3 '.deb' files that I have to rely on. So I tried Crunchbang and there was no desktop environment at all. Frankly, I just don't want to spend 10mins "tweaking it" every Live CD session before getting to work on my regular stuff.


I just need something ready to go out of the box. So I am gonna stick with a "Live Ubuntu CD" since I am upgrading the RAM from 256 to 1GB anyway. And I know the basic Ubuntu environment pretty well.

So back to my original question: Would an earlier version of Ubuntu use a significant amount less RAM? Like Feisty or Hardy? If Lubuntu was out, I would probably use that. Knoppix for some reason has a lot compiz enabled on bootup and its really annoying.

Thanks for the suggestions, I know we all have our pet flavors of Linux outside of Ubuntu.


.

if its just for certain programs could you not setup a ram based filesystem to install the program, then when youve finished the program wouldn't be saved, ive never done it but im sure it would be possible, would be easier and faster than using a live cd.

---

### Post by nothingspecial on 2009-12-16
I can`t answer your question.

What, I know though, is installing ubuntu minimal and adding openbox on a seperate partition (and I cannot see how that would differ from running a live cd...........enlighten me :)) is the best way to do this.

I probably just don`t understand your needs.

---

### Post by viljun on 2009-12-16
I also didn't like 8.04 so much. Instead Xubuntu 9.10 feels much faster and installed even a machine that I didn't get 8.04 to work. I really recommend Xubuntu 9.10.

---

### Post by Gizenshya on 2009-12-16
Have you considered making an altered LiveCD based off of an Ubuntu LiveCD?  Just take out some programs you don't want, and put in some programs/settings you want.  If you don't use OpenOffice, for example, then just remove that for space.  That should free up plenty.

Or, if the comp has a DVD drive, just add a program or programs like mentioned above, and then just burn the resulting larger ISO file to a DVD instead of CD.

1GB of memory is plenty for anything I can think of, unless you are doing video editing or graphics work.

---

### Post by Tek-E on 2009-12-16
I know its not Ubuntu but you might try DSL (Damn Small Linux)
DSL runs great on P.O.S. Machines.  And its a pretty neat little distro.

---

### Post by Greg Xix on 2009-12-19
> **Gizenshya said:**
> Have you considered making an altered LiveCD based off of an Ubuntu LiveCD?  Just take out some programs you don't want, and put in some programs/settings you want.  If you don't use OpenOffice, for example, then just remove that for space.  That should free up plenty.

Or, if the comp has a DVD drive, just add a program or programs like mentioned above, and then just burn the resulting larger ISO file to a DVD instead of CD.

1GB of memory is plenty for anything I can think of, unless you are doing video editing or graphics work.


Actually, yeah. I was wondering how to rig up something like that. What programs are the best/easiest for that sort of thing.

One thing I have noticed, is that Live DVD's seem to run slightly smoother than Live CD's. So I am using that now.

---

