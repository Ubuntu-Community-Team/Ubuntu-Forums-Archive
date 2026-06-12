---
title: "Just installed Ubuntu! A Few Problems..."
date: 2009-10-25
forum: General Help
---

### Post by bds28338 on 2009-10-25
okay, just installed ubuntu, went on without a hitch, I'm already loving it! I do have two small problems though.

number 1.) you know the generic beep that is played when you're messing around in BIOS or Windows has a aneurysm? It's killing me, it plays at random times like when I'm pressing the up or down button in the drivers menu. Anyway to turn it off?

number 2.) Proprietary drivers! I have a few listed, two for wireless, and three for graphics.

for graphics related drivers we have
 NVIDIA accelerated graphics driver (version 180) [Recommended]
 NVIDIA accelerated graphics driver (version 173)
 NVIDIA accelerated graphics driver (version 96)

I just installed the recommended one as it's the latest version and it says recommended

and for wireless we have
 Broadcom B43 wireless driver
 Broadcom STA wireless driver

so as for my question, I'm assuming I did okay by the version 180 NVIDIA right?
and the wireless drivers did absolutely nothing, and I kind of want to get my wireless networking running, so what should I do? I can follow directions and such I'm good with computers, you'll just have to be detailed. Click here, type this, tell me what this said, etc.

---

### Post by rockstarrem on 2009-10-25
As for the wireless, can you hook up a wired connection to download the driver?

---

### Post by bds28338 on 2009-10-25
yes, I'm on a wired connection right now, I don't believe they have a Linux driver? I've been reading on the forums and apparently Broadcom does not like to play nicely with Linux. Everything is working perfectly, I figured out the beep myself, and I have a wired connection, I just have to get this wireless working.

---

### Post by rockstarrem on 2009-10-25
Can you right click at the top where the networks are and see if you can connect to your wireless one? This may sound like a stupid question, but I read that there is support for Broadcom now.

---

### Post by bds28338 on 2009-10-25
when I right click, it brings up a small menu where I can enable networking and wireless, both are enabled. I also going to the wireless menu in Edit Connections and manually putting in my router, but it does not connect or do anything at all. I cannot scan for wireless connections.

---

### Post by rockstarrem on 2009-10-25
Is this what you need? [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by bds28338 on 2009-10-25
we'll give it a whirl, I believe ubuntu already gave it to me, but this may be a different one.

---

### Post by P4man on 2009-10-25
if you left click the network manager, do you get a list of access points?
If you do, then the driver is working, if you dont, then perhaps try the other restricted driver.

If neither works, open a terminal and type

```
lspci
```
(note that is LSPCi in lowercase)

if its a usb wifi stick instead run:

```
lsusb
```

and copy paste the output here

---

### Post by bds28338 on 2009-10-25
umm... there's no .exe or whatever it is Linux uses to install files, so... no clue as to how to use it.

---

### Post by rockstarrem on 2009-10-25
This should help I think: [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

---

### Post by bds28338 on 2009-10-25
P4Man makes me feel quite foolish right now... yup got it connected... just had to eh... left click >.< should I use any of the drivers ubuntu provided me with in the proprietary drivers page?

---

### Post by P4man on 2009-10-25
guys, why dont we first determine if he really needs to download and compile drivers? he's new to ubuntu, lets see if the automatically suggested restricted drivers dont work. Otherwise he's gonna have to install build-dep, find out how to compile and then possibly repeat the whole process with each kernel upgrade.

---

### Post by P4man on 2009-10-25
> **bds28338 said:**
> P4Man makes me feel quite foolish right now... yup got it connected... just had to eh... left click >.< should I use any of the drivers ubuntu provided me with in the proprietary drivers page?

Im not sure. Im guessing you already are using one of them. If not, if it aint broke dont fix it. But sometimes opensource drivers have issues with WPA or not so good range, then you could try the restricted driver and see if it helps. But again, if it works now, lets not mess up just yet :)

---

### Post by bds28338 on 2009-10-25
yeah, really the only thing that worries me is I'm literally sitting right next to the router and it's giving me 75% signal strength. but it works, so I'm good for now, we'll just wait and see what happens.

---

### Post by P4man on 2009-10-25
oh and btw, no need to feel foolish. You'll find out that ubuntu, unlike windows doesnt throw popups inf your face for everything. Its too modest, it makes your stuff just work without mentioning it ;). Its like that for just about every hardware you add, you wont see "new hardware detected" but it will probably just work.

---

### Post by P4man on 2009-10-25
> **bds28338 said:**
> yeah, really the only thing that worries me is I'm literally sitting right next to the router and it's giving me 75% signal strength. but it works, so I'm good for now, we'll just wait and see what happens.

thats probably *because* you are setting right next to it. wifi works best at a few meter distance

---

### Post by bds28338 on 2009-10-25
yeah, I took a run around the house and it seems to be working fine. One last tweak and I should be good, is there any way to stop buntu from asking me for my password each time I change something? I just want it to ask once, when I log in.

---

### Post by P4man on 2009-10-25
Its possible, but im not gonna tell you Im afraid.
have a look here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Now the thing is, since you're new to the OS, and only just installed it you are experimenting and installing and trying stuff out, so you have the sudo popup quite often. Once you stop tweaking and start using it, you'll find out its really not an issue. I for one, like to be reminded im doing something potentially harmful.

---

