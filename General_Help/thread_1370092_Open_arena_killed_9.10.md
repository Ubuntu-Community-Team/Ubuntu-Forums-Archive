---
title: "Open arena killed 9.10"
date: 2010-01-01
forum: General Help
---

### Post by PartsMan on 2010-01-01
I downloaded Open arena on my desktop. (specs below)
As soon as I opened the game my screen went black and became unresponsive.

I finally held the power button down to shut down. Then when I tried to restart it did not work.
Regular boot turns the computer back off before reaching the desktop. 

I then tried recovery mode. It hangs up at
    * Setting up console font and keymap...

The machine will run DSL and Tiny core both live but not my x9.10 cd.
I could not mount my HD in DSL or Tinycore.

What should I do?

---

### Post by mechro on 2010-01-01
Perhaps the game isn't set to run at your screen resolution. See if there is an openarena folder in your home folder... it may be hidden. In the folder there may be a configuration file called something like openarenarc. Open that file in Text Editor and you might find some screen resolution settings you can edit.

I apologise for all the mights and mays but I don't have Open Arena installed so I'm making educated guesses.

---

### Post by PartsMan on 2010-01-01
I kind of figure that my dell's graphics are the reason for the original freeze.

Running the game is the least of my worries now.

I can't check my home folder because I can't boot anything that will mount it.
I am thinking because it is ext4.

---

### Post by mechro on 2010-01-01
> **PartsMan said:**
> 

Running the game is the least of my worries now.



Oops. Sorry, didn't properly read your opening post.

You say your LiveCD won't boot? Have you booted from it before?

---

### Post by PartsMan on 2010-01-02
It's the one I loaded both computers from.

I just tried it again on my laptop. Worked fine.

Is something wrong with my computer?

---

### Post by Groundswell on 2010-01-02
did you try again on your problem machine? just running the live disk that is? do that and post back result

oops, nevermind. saw it. sounds bad :( do you have a standard ide - laptop ide adapter? it's just a wee little guy that lets you plug ur laptop hard drives to standard and vis versa, if you do, try booting that problem computers hard drive on your laptop

---

### Post by PartsMan on 2010-01-02
It seems to be a problem with X.

Playing with my stack of live cds I figured out that if I force X I can boot some of them.

How do I force/adjust X with Xubuntu 9.10?

---

### Post by mechro on 2010-01-02
Here are Boot Option instructions for Ubuntu LiveCD (I assume Xubuntu is the same)...

[https://help.ubuntu.com/community/BootOptions#Common](https://help.ubuntu.com/community/BootOptions#Common)

You can choose one of the pre-configured boot options or edit the boot line as required.

---

### Post by PartsMan on 2010-01-02
O K 
I have booted the live X9.10 cd by turning acpi off.
Now how do I fix my HD install?

---

### Post by mechro on 2010-01-02
Right. I'm not sure what's broken. The hard shutdown you did may have borked the File System. Try a File System repair as follows...

Boot your LiveCD. Don't mount or navigate to any of your installed partition/s. Open a Terminal and do the following command...

```
sudo fsck
```

Depending on your partitioning it should offer to check and repair each of your partitions. If it warns that a partition is mounted (possibly swap) then select N. 

Try and reboot your installation and report back.

---

### Post by PartsMan on 2010-01-02
It didn't seem to work with Xubuntu. I am trying a UNR 9,10 cd that I have now.
It was like it recognized the command but didn't run it.
I may have to download and burn the regular 9.10 to fix this. 
That will take a while on my connection and PIII laptop.

---

### Post by PartsMan on 2010-01-02
Nope. Same thing with 9.10 UNR.
It gives me this

fsck from util - linux - ng 2.16

and then gives me a command prompt.

---

### Post by PartsMan on 2010-01-03
I am trying a fresh install before I give up on this machine.

---

### Post by mechro on 2010-01-03
> **PartsMan said:**
> I am trying a fresh install before I give up on this machine.

That would be my suggestion.

If you ever get an unresponsive system situation again there are some handy key strokes to safely shutdown/reboot your computer...

Hold Alt & SysRq(Print Screen key) then type R S E I U B

Explanation here...

[http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/](http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/)

---

### Post by PartsMan on 2010-01-04
I am afraid it is my board. My fresh install of x9.10 loaded on the second try and booted once but on the first restart I got a black screen.

Then I pushed my pride aside and loaded XP sp3.
It loaded and boots fine but my resolution is stuck at the basic square defaults.

I can't load drivers for my Wireless card, Ethernet, Video, or sound.

I'm going to tinker with it some more tonight but I think I need a new toy.

---

### Post by PartsMan on 2010-01-06
I got drivers from Dell and XP is working fine now.

Why does Windows work but Ubuntu will not even run live?

---

### Post by Kylerobhew1 on 2010-01-16
same problem here i changed resoloution in the configuration file with no results.
i have an intel graphics card 512 megs ram and a 2.66ghz intel celeron d processor.

---

### Post by fancypiper on 2010-01-16
I have seen bad memory acting similarly.  Have you run memtest?

---

### Post by Kylerobhew1 on 2010-01-16
yeah i just let it run all night i just upgraded to 1gb corsair before memtest same problem presists

p.s. no live cd problems just open arena

---

### Post by mechro on 2010-01-17
Open Arena FAQ here...

[http://openarena.wikia.com/wiki/FAQ](http://openarena.wikia.com/wiki/FAQ)

---

### Post by carlosgs91 on 2010-01-17
.

---

### Post by PartsMan on 2010-01-19
I got an older Dell 2350 (similar Intel graphics chip) and it ran 8.04 but not 9.10. Apparently my 2400 had a real graphics issue.

The plan now is to put my drives, power supply, processor and the video card I ordered in the 2350.

Bigger Faster Stronger:)

---

