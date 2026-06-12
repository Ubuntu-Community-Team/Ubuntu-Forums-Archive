---
title: "Wirless USB devices stoped working (keyboard and mouse)"
date: 2010-01-14
forum: General Help
---

### Post by chinaCat86 on 2010-01-14
Hi,
I am running 9.04 on  a relatively new ASUS laptop.

All has been well, but yesterday my MS wireless mouse and my Logitech wireless keyboard randomly stoped working. I have not the faintest idea as to what may have caused this. 

I have looked around but have found no problems like this that supply a useful answer (at least useful to me).

One interesting thing though is that dmesg | grep mouse returned 
[    1.906384] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    3.960028] mice: PS/2 mouse device common for all mice

Which I am not too sure what that means, but besides an ipod own no Mac items. 

Where to begin?

---

### Post by audiomick on 2010-01-14
you've tried changing the batteries?
just to be sure. I know it is an obvious question.;)

---

### Post by chinaCat86 on 2010-01-14
yes, I have. 
Just changed the mouse last week. 
Also, when these batteries are low I am given a warning normally. For example, the mouse goes weak. or letters dont respond quick enough. Further, why would both the mouse and the keyboard run out at the same time?

---

### Post by chinaCat86 on 2010-01-15
Friendly bump.

Anyone have any pointers, or anything I can look at would be greatly appreciated.

---

### Post by chinaCat86 on 2010-01-15
Well, I tried booting in Vista as well--have only actually done once that since I installed it. And the mouse and keyboard still do not work. This confounds the situation even more.

---

### Post by chinaCat86 on 2010-01-15
[FONT=Courier New]dmesg | tail
[  125.956083] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[  127.940089] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[  129.287918] wlan0: direct probe to AP f647e6b8 try 1
[  129.486466] wlan0: direct probe to AP f647e6b8 try 2
[  129.685051] wlan0: direct probe to AP f647e6b8 try 3
[  129.870540] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[  129.893543] wlan0: direct probe to AP f647e6b8 timed out
[  131.913076] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[  133.860054] hub 2-0:1.0: connect-debounce failed, port 2 disabled
[  135.805051] hub 2-0:1.0: connect-debounce failed, port 2 disabled[/FONT]


[FONT=Arial]I wonder what this means. I see this is a problem in 9.10, but I am still using 9.04. I was going to upgrade this weekend seeing as how I some free time, but I feel this may be a deeper issue. Considering that in Windows Vista I also have an issue. But why would this randomly happen. [/FONT]

---

### Post by RedRat on 2010-01-15
> **chinaCat86 said:**
> Well, I tried booting in Vista as well--have only actually done once that since I installed it. And the mouse and keyboard still do not work. This confounds the situation even more.
Since it appears to fail in both Windows and Ubuntu, this indicates a computer problem. Perhaps with your wireless receiver. While it could be with the senders in each device, since both failed simultaneously that is unlikely. If not the receiver, then your USB port might be having a problem.

---

### Post by chinaCat86 on 2010-01-15
Any ideas on how to confirm if it is the ports, or if so how I would go about fixing such an issue?

---

### Post by RedRat on 2010-01-15
> **chinaCat86 said:**
> Any ideas on how to confirm if it is the ports, or if so how I would go about fixing such an issue?

The simplest check would be to plug your receiver into a different USB port, does it work then? You probably have some on front and some in the rear. You might want to try them all and see if get some joy.

If you have another computer available or easy access to one, try the devices on that computer. If they also fail to responds, there is a strong possibility that the receiver has failed (I am assuming that it is unlikely that both the mouse and Keyboard would fail at exactly the same time). 

If they work on another computer, then you may have some problem with your motherboard where the USB section is. One fix, if that is the case, is to buy a USB card (you can get some very inexpensive ones now) and put it into a vacant slot. If this fails to restore activity, then you have a motherboard problem. The only solution then is a new motherboard, there are few out there who actually repair motherboards. 

Good luck.

---

### Post by chinaCat86 on 2010-01-16
--
>>the simplest check would be to plug your receiver
>>into a different USB port, does it work then? You 
>>probably have some on front and some in the rear. 
>>You might want to try them all and see if get some joy.
--
Has been tried, but I gave it another go. Even tried plugging in an IPOD. The Ipod was not picked up on the side ports, but was in the back. I have moved keyboard and mouse receivers there, and have shut down to no avail. I wonder about these side usbports. The laptop is six months old. I would have to take issue with such a problem. 

--
>>If you have another computer available or easy access to one,
>>try the devices on that computer. If they also fail to responds, 
>>there is a strong possibility that the receiver has failed (I am 
>>assuming that it is unlikely that both the mouse and Keyboard 
>>would fail at exactly the same time). 
--
I tried the mouse, and that worked without issue. I would assume the keyboard would work as well, but one device at a time.

--
>>If they work on another computer, then you may have
>>some problem with your motherboard where the USB 
>>section is. One fix, if that is the case, is to buy a USB 
>>card (you can get some very inexpensive ones now) 
>>and put it into a vacant slot. If this fails to restore activity, 
>>then you have a motherboard problem. The only solution 
>>then is a new motherboard, there are few out there who 
>>actually repair motherboards. 
--
Well, thanks. I have some rare free time and was going to do a clean install of 9.10 and win 7 this weekend I think I will hold off until I can resolve this issue. However, it is looking more and more of some sort of hardware issue. This bothers me. It would bother me less if my laptop fell off the desk or something, but I simply come out of a shower and return to this mess. 

Thanks. In hopes it is not a hardware issue I will continue to solicit advise. My ands are just not fit to do any serious laptop work. Too cramped. 
Good luck.

---

### Post by RedRat on 2010-01-16
[chinaCat86]("http://ubuntuforums.org/member.php?u=863310")
I see that it is a laptop that is only 6 months old. If that is the case, you might still be under warranty. You may want to check with whoever sold you the laptop or manufacturer. There are very few people who can or will repair laptops out there, but it can be done. 

It is possible that reinstalling software might rectify the situation, but since both Windows and Ubuntu are both out, I suspect it is more likely a hardware issue.

---

### Post by chinaCat86 on 2010-01-16
the other odd thing to note is that when I try to use the wireless keyboard in a BIOS setting or in grub everything hangs for about thirty-seconds. If i use the wireless keyboard my laptop keyboard becomes unresponsive for about 30 seconds. Neither keyboard will work, but after about 30 seconds all keys pressed on the laptop keyboard processed. Almost like it is receiving the input from the wireless keyboard but not knowing howto process it. I am short of saying this is a total hardware issue for other USB devices, such as my IPOD, are still functioning.

redrat, I greatly appreciate all the help and suggestions.

---

### Post by chinaCat86 on 2010-01-22
After traveling the past few days I randomly decide to plug in my mouse and keyboard. Figuring it won't work. But after not messing with it for a few days I decided to give it a go. They work! For some random reason the mouse and the keyboard works. It has been about ten minutes now. Hopefully this continues I have some video editing to do and it sure would be nice to be able to use a mouse this week. 

So I my problem fixed itself, but this does not feel solved. Additionally, doing searches this has seemed to be a continual bug with no real fix.  Take Care, and thanks again for your help RedRat. It was greatly appreciated.

---

### Post by RedRat on 2010-01-22
> **chinaCat86 said:**
> After traveling the past few days I randomly decide to plug in my mouse and keyboard. Figuring it won't work. But after not messing with it for a few days I decided to give it a go. They work! For some random reason the mouse and the keyboard works. It has been about ten minutes now. Hopefully this continues I have some video editing to do and it sure would be nice to be able to use a mouse this week. 

So I my problem fixed itself, but this does not feel solved. Additionally, doing searches this has seemed to be a continual bug with no real fix.  Take Care, and thanks again for your help RedRat. It was greatly appreciated.

I am glad that it has apparently cured itself. I am curious though and would ask you, did you by any chance take the battery out of the machine during you traveling?? 

My daughter has a Toshiba running Windows Vista, and we had a similar lock up. I took the machine to where we bought it (Fry's) and the technician removed the battery completely, waited about a minute, then put it back in. The problem was resolved! He told me to try that when you have some software/hardware issues, it seems to reset the machine internally.

---

### Post by chinaCat86 on 2010-01-23
I did not. However, I did run it on battery and got it uncomfortably low--I don't like getting the battery to low.

---

### Post by RedRat on 2010-01-23
> **chinaCat86 said:**
> I did not. However, I did run it on battery and got it uncomfortably low--I don't like getting the battery to low.
Well then you didn't rest the computer. According to the technician, you must remove the battery completely and let the machine sit for about a minute. Interesting that it cured itself. This still suggests a hardware issue and not a software issue, I think.

---

### Post by chinaCat86 on 2010-04-22
It's back. Same exact issue. Hopefully it decides to cure itself. Grr...

---

### Post by RedRat on 2010-04-22
> **chinaCat86 said:**
> It's back. Same exact issue. Hopefully it decides to cure itself. Grr...
Try that trick I suggested by taking the battery out completely and let the machine sit for about a minute or maybe more. See if that solves it.

---

### Post by P4man on 2010-04-22
The output you posted earlier strongly suggests a hardware problem. Can you plug another (wired) mouse or keyboard in the same USB plug? If so, does that work? If it doesnt, your usb ports are dying. If that does work, its probably the receiver.

---

