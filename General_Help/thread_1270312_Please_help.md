---
title: "Please help"
date: 2009-09-19
forum: General Help
---

### Post by harecanada on 2009-09-19
I turned my computer off one night and now I have a black screen. I thought it was my video card so I removed it and plugged my monitor into my onboard card but still nothing happened. Can someone give me a hand on this?
harecanada

---

### Post by skatinjj on 2009-09-19
Assuming the computer was working before it was turned off, try cleaning the memory contacts with rubbing alcohol (isopropyl) and cotton swabs (dip cotton swap in alcohol).

Just the gold contacts not the actually circuitry.

---

### Post by oldsoundguy on 2009-09-19
try plugging your monitor into another computer.

---

### Post by harecanada on 2009-09-19
oldsoundguy - I tried plugging it in to another computer and it works great. 
skatinjj: I'll clean the contacts and put it back in the puter and let you know how it goes.

Everything was working fine up to this point. Haven't had any real problems.
Thanks for your help so far.
harecanada

---

### Post by oldsoundguy on 2009-09-19
do you get any splash screen and THEN it goes black, or is it that it NEVER shows anything?

---

### Post by solidblu on 2009-09-19
Does it make any sounds (fans, drives spinning up, etd) when you hit the power button?  

If no:  Assuming you check to make sure it is plugged in what you can do is open it up and reset the power supply cable on to the mother board and try hitting the power button when you have it open.  Does the CPUs fan spin at all?

If not this could either be your power supply or the power button for some reason isn't creating a circut to tell the motherboard to turn on, but from  your post it sounds like you didn't open your computer before hand this seems less likely.

I would check for sounds as power supplies dying are not too unheard of.

---

### Post by harecanada on 2009-09-19
The computer itself, turns on and then ubuntu comes up as if it is going to start then it goes black and the on/off light flashes on and off continuously. I can't turn the monitor on or off. If I unplug it from everything and then plug it in again it still flashes. If I plug it into another computer it seems to reset itself and works fine. No more flashing. What does this all mean? Is it hardware or software? I can't figure it out. I have a lot of data that I need on this computer though and I don't want to lose it.
harecanada

---

### Post by Soley on 2009-09-19
Have you tried a live disc in the computer to see if it boots up?

---

### Post by harecanada on 2009-09-19
Soley. I haven't yet.I'm on a very old computer right now trying to get it working OK. I'll try my new one with the problem and get back to you. Thanks.
harecanada

---

### Post by grundygreen on 2009-09-19
> **harecanada said:**
> The computer itself, turns on and then ubuntu comes up as if it is going to start then it goes black and the on/off light flashes on and off continuously. I can't turn the monitor on or off. If I unplug it from everything and then plug it in again it still flashes. If I plug it into another computer it seems to reset itself and works fine. No more flashing. What does this all mean? Is it hardware or software? I can't figure it out. I have a lot of data that I need on this computer though and I don't want to lose it.
harecanada

hit ctrl-alt-f4 tell us the error messages.

---

### Post by harecanada on 2009-09-19
OK, so I plugged the monitor into the computer. It immediately started the on/off light flashing. I tried rebooting with a live cd but no luck. Then I plugged the monitor directly into the motherboard. The blinking light went off immediately. Then I got a message that said there is a ad-on graphics card and the graphics card on the motherboard could not be used. So it really does feel like I have a bad graphics card all of a sudden.
Any suggestions?
harecanada

---

### Post by harecanada on 2009-09-20
If I take the graphics card out, how do I activated the on board graphics on the motherboard?
harecanada

---

### Post by odinb on 2009-09-20
In the BIOS of the motherboard.

Read the manual for specifics.

---

### Post by harecanada on 2009-09-20
How would I find out what's on the motherboard for graphics?
harecanada

---

### Post by harecanada on 2009-09-21
Hello,
I've been trying everything I could think of to handle this problem and then today I tried using the Kubuntu live cd for Jaunty 64bit and it worked. So I'm on the net via this cd. Now what this means to me is that the graphics card is probably not the problem. Can someone give me a hand and see if I can recover the data that is on this computer? 
harecanada

---

### Post by harecanada on 2009-09-21
OK.
So I'm running my computer off the Kubuntu Live cd. Is there any way to get at the information on my computer from the live cd? I want to backup the data if I can't save my system.
harecanada

---

### Post by skatinjj on 2009-09-24
**To mount:**

```
sudo mkdir /media/hda1
sudo mount /dev/hda1 /media/hda1
```

Not sure if you are backing up to another hard drive or pen drive.
[B]
For pen drive:[/B]
```
sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1
```
[B]
For second hard drive:[/B]
```
sudo mkdir /media/hda2
sudo mount /dev/hda2 /media/hda2
```

---

