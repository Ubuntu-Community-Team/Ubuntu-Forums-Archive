---
title: "System not installing"
date: 2011-06-29
forum: General Help
---

### Post by soumyabratapaul on 2011-06-29
One of my friends have a Toshiba laptop Satellite Pro C650, and it was installed with Windows 7 Ultimate 32-bit. A few days back, there was a problem with the system, where, the system hanged when the Starting Windows screen appeared. After a few days the system, just crashed, and I my friend did a Windows recovery. After that the computer was running smoothly. After a few days again, the system again began giving the same problem, and then the system crashed. So I recommended that he format his computer and do a clean installation of Windows.

So, when he began the installation process of Windows 7 32-bit, the system again, freezed at &#8220;Setup is Starting&#8221; screen. Again, he tried it after restating the system, and again the system freezed, at &#8220;Setup is Starting&#8221;. I tried, to install from various media, but the screen froze, at there. I tried a mem test, and no hardware errors were found. Even I tried installing Ubuntu 10.04, and the system froze while it was loading the files, and a boot prompt came, and nothing happened. I tried with Ubuntu 10.10, and Kubuntu 10.04, and the same result.

Please advice what should I do.

---

### Post by jerrrys on 2011-06-29
will the live cd run without installing?

---

### Post by owiknowi on 2011-06-29
second: power down the whole system and disconnect from ac and remove battery for a couple of minutes.

third: you could wipe the entire hdd with killdisk to make sure there'nothing wrong with it (it shows errors too).
[http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm)

the ubuntu alternate cd has an option to erase a partition / disk too (don't know about error reporting).
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

---

### Post by dFlyer on 2011-06-29
Boot the live desktop cd and use Disk Utility to check the health status of your hard drive.

---

### Post by soumyabratapaul on 2011-06-29
The system, is not even starting with the live cd, and it it freezing, with a prompt, and then nothing is happening. I kept it like that for over an hour and then, also nothing is happening.

---

### Post by soumyabratapaul on 2011-06-29
> **dFlyer said:**
> Boot the live desktop cd and use Disk Utility to check the health status of your hard drive.

The system is not booting with the live cd option also, and it is freezing at that screen with a prompt.

---

### Post by jerrrys on 2011-06-29
how long did you let mem test run?

---

### Post by soumyabratapaul on 2011-06-29
For about an hour. It passed the test and showed no error.

---

### Post by guzjd on 2011-06-29
Did you just download the Ubuntu release or using media that you have installed from before?
 
You said the system hangs when loading files, is this at boot or during the copy phase of the installation?

---

### Post by jerrrys on 2011-06-29
sorry, but i have to ask again...

a mem test on my box is an overnight process.  did it actually finish or just showed good at that point?

---

### Post by soumyabratapaul on 2011-06-29
> **jerrrys said:**
> sorry, but i have to ask again...

a mem test on my box is an overnight process.  did it actually finish or just showed good at that point?

So I have to run mem test for over 12 hours?

Actually, I executed it for 1 hour and then just rebooted, but at that instant it has passed all the test it had performed, so no error, till the instant I had done.

---

### Post by guzjd on 2011-06-29
When you load the Live CD can you get past this screen or is this where it hangs?
 
[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

---

### Post by soumyabratapaul on 2011-06-29
> **guzjd said:**
> Did you just download the Ubuntu release or using media that you have installed from before?
 
You said the system hangs when loading files, is this at boot or during the copy phase of the installation?

I have previously, installed Ubuntu from this media, in my own computer and to many of my friends computer. This media is perfectly fine. But on my friends laptop, it is just freezing.

---

### Post by soumyabratapaul on 2011-06-29
> **guzjd said:**
> When you load the Live CD can you get past this screen or is this where it hangs?
 
[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

It is where, the system hangs, again and again. I just cannot get past this. I have tried many times, but to no avail. Even Windows is freezing, when the "Setup is Starting", screen appears.

---

### Post by guzjd on 2011-06-29
Has there been any changes to the BIOS or hardware installed on the system recently?  For it to happen in both Ubuntu and Windows it seems hardware or BIOS related.  
 
If I understand your previous response correctly you are freezing at the Ubuntu boot screen as well.  Have you tried any of the parameters or steps identified in the link I posted?

---

### Post by soumyabratapaul on 2011-06-29
When I try to install Ubuntu, no screen appears, and just a boot prompt appears. So pressing F6, does not arises, to change the boot parameters.

---

### Post by soumyabratapaul on 2011-06-29
> **guzjd said:**
> Has there been any changes to the BIOS or hardware installed on the system recently?  For it to happen in both Ubuntu and Windows it seems hardware or BIOS related.  
 
If I understand your previous response correctly you are freezing at the Ubuntu boot screen as well.  Have you tried any of the parameters or steps identified in the link I posted?

I cannot get to the screen only, then how will I change the boot parameters. And no hardware or BIOS, changes were done. I myself first thought and loaded the BIOS default settings.

---

### Post by guzjd on 2011-06-29
Can you elaborate on what exactly the prompt looks like. For example, it could be a shell, initramfs, grub, etc.

---

### Post by soumyabratapaul on 2011-06-29
> **guzjd said:**
> Can you elaborate on what exactly the prompt looks like. For example, it could be a shell, initramfs, grub, etc.

I cannot really, tell you what it really looks like, but to me it, is not a shell, because I have given some commands to check if it is a shell, but nothing just happened, but I can type. Nothing happens really in the prompt screen, and it freezes. But if I press Ctrl + Alt + Del, then many message come at the same time in the prompt, but I cannot really tell you what the message says, because it hardly stays for a second, in the screen, until new messages comes. But mostly the messages consists of error 110.

---

### Post by guzjd on 2011-06-29
How is the fix coming along?

---

### Post by cbowman57 on 2011-06-29
Am I the only one that thinks trying to force an Ubuntu installation on a system with hardware problems isn't a good idea & will reflect on the operating system?

After a couple days of screwing around with it the owner of the laptop will take it in, they will blame the failure on Ubuntu and sell him a new one, or repair it, all the while blaming linux for "causing" the problem.  I just see this story ending badly. :)

---

### Post by soumyabratapaul on 2011-06-29
No one thinks that way, there is a problem that is why I have written, and by the way I am a big Linux fan, and even in my school, I have taken all the servers from Windows to Linux, and even I use Linux along with Windows. My other computer(which are used as servers and for downloading), runs Linux.

---

### Post by cbowman57 on 2011-06-29
Not saying you're not a big fan, or that you're not capable of doing good Ubuntu installations.  I think you are very capable, just think that you're beating your head against a wall regarding this particular piece of hardware and ultimately your good intentions are going to blow up in your face.

I'll keep monitoring this thread to see how it turns out.   Make sure you reply back when you get it sorted out & I'm proven wrong. :)

---

### Post by soumyabratapaul on 2011-06-29
Nah, nothing of that sort mate. There must be a problem and I want to sort it out, with you all's help. I told my friend to install Ubuntu because it is a better OS than Windows(personal view). But during the installation, such a thing would happen, was totally out of my knowledge. Like never heard Linux freezing. Will try to find a solution, and keep you all updated. Will try to install Linux(Fedora) via USB. Lets see if that works.

---

### Post by cbowman57 on 2011-06-29
Yeah, I love my Ubuntu too but if neither Windows or Ubuntu want to act right I just think the worst.  Good luck with trying the Fedora from USB.  I am curious to read how this plays out.

---

### Post by soumyabratapaul on 2011-06-29
Yeah will keep you all updated, and in the mean time please let me know if you guys get any solution, any help will be highly appreciated and I am waiting in anticipation, and thanking you all in advance.

---

### Post by guzjd on 2011-06-29
> **cbowman57 said:**
> Am I the only one that thinks trying to force an Ubuntu installation on a system with hardware problems isn't a good idea & will reflect on the operating system?
 
After a couple days of screwing around with it the owner of the laptop will take it in, they will blame the failure on Ubuntu and sell him a new one, or repair it, all the while blaming linux for "causing" the problem. I just see this story ending badly. :)
 
I suspected hardware problem and referred him to some diagnostic tools that should help him get down to the root of the problem. (Via PM)

---

### Post by soumyabratapaul on 2011-06-30
Guys after some, hard effort, I finally booted into the system, and guess what Linux(Kubuntu 10.04 LTS) could not even recognise the HDD. I suspect that there is a bad sector error, and referred to get an RMA. Lets see what happens, and will let you all posted.

---

### Post by cbowman57 on 2011-06-30
Well at least a HDD can be replaced, even on laptops.  Glad you got to the root  of the problem, hope you get it sorted out and then you can show your friend the power of Ubuntu. :)

---

### Post by soumyabratapaul on 2011-07-01
> **cbowman57 said:**
> Well at least a HDD can be replaced, even on laptops.  Glad you got to the root  of the problem, hope you get it sorted out and then you can show your friend the power of Ubuntu. :)

Yeah, waiting eagerly for that. Thanks for all your help regarding the matter.

---

### Post by soumyabratapaul on 2011-07-02
Guys, kept my friends laptop running for 12 hours, with the Windows 7 Ultimate (32-bit) Installation Disc, and finally, it started to install the OS. Now guess, what I went out for 3 hours, and came back to see, that the main power had been shut down by someone, and the laptop naturally ran out of juice. 

Got to sit it with again, just so frustrating!

---

### Post by goldshirt9 on 2011-07-02
i have just installes windows 7 64bit ultimate on my wifes laptop and that took at max 
1 hour ( not including updates) .
i would say you have a faulty hdd.
if you know the make you can run hdd checkers.
memtest worked on my pc in about 20 mins to verify a stick of ram was faulty.


but you have to have a o/s installed to do that.:(

---

### Post by mörgæs on 2011-07-02
> **goldshirt9 said:**
> 
memtest worked on my pc in about 20 mins to verify a stick of ram was faulty.


but you have to have a o/s installed to do that.

No, memtest runs in a live boot.

---

### Post by monte001 on 2011-07-02
i want to know the outcoming too because i had the same problem.

the only exception was, i can install windows but not linux.

monte001

---

### Post by soumyabratapaul on 2011-07-03
I have already said that my friends laptop has a bad sector, and that is why it is freezing and hanging. BTW, in my computer, it took only 10 minutes to install Windows 7 64-bit and within 5 minutes I had installed the drivers and then 10 minutes to install other softwares. So total of 25 minutes for a running PC. I have adviced my friend to get an RMA. Let's see, what happens and will let all you guys informed.

---

