---
title: "Grub Rescue"
date: 2011-03-26
forum: General Help
---

### Post by LostnConfused on 2011-03-26
Hey, last night I deleted some **** off my computer, not knowing what I was doing tbh, I had windows 7 as my default OS and uBuntu for play. When I deleted some of the disk ****, I then restarted my computer and I get a black screen saying:

```

Error: no such partition.
grub rescue>
```
I have looked all around at other threads, trying to solve this problem,
What I have done:
Tried to run my Windows 7 CD-DVD and nothing happens.
Right now I am currently downloading Ubuntu on my laptop, to see if I can make another CD of it, and boot into it hopefully.
If anybody knows what I can do to solve this, I would be verrry happy.
I would also donate PayPal money if anybody needed, I know I am a first time poster, but this has been frustrating me for quite some time. So please, if you can do.

---

### Post by LostnConfused on 2011-03-26
Hey, last night I deleted some **** off my computer, not knowing what I  was doing tbh, I had windows 7 as my default OS and uBuntu for play.  When I deleted some of the disk ****, I then restarted my computer and I  get a black screen saying:

```

Error: no such partition.
grub rescue>
```I have looked all around at other threads, trying to solve this problem,
What I have done:
Tried to run my Windows 7 CD-DVD and nothing happens.
Right now I am currently downloading Ubuntu on my laptop, to see if I can make another CD of it, and boot into it hopefully.
If anybody knows what I can do to solve this, I would be verrry happy.
I would also donate PayPal money if anybody needed, I know I am a first  time poster, but this has been frustrating me for quite some time. So  please, if you can do.

---

### Post by drs305 on 2011-03-26
You can take a look at this thread:
[Grub Rescue Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")

It will help you recover your system. Either in that thread or here, please post the contents of the boot info script RESULTS.txt. That file will help us see the condition of your system if the thread doesn't help you solve this on your own. Info about the boot info script is located in the 'Rules for posting' section of the thread.  ;-)

---

### Post by LostnConfused on 2011-03-26
I cannot do anything with my computer sir, I tried looking at the thread you listed, but it says to do things when not in rescue, as I am on my laptop right now. My desktop is "bricked" as you can say, in Grub Rescue. I cannot do anything on it but the BIOS menu thing I believe it is called.

---

### Post by LostnConfused on 2011-03-26
I believe I may have deleted the drives my ubuntu was on? Im not sure what I did to be honest.

---

### Post by drs305 on 2011-03-26
Most of the previously-referenced thread is what to type at the grub rescue prompt, but we can help you in this thread just as easily.

If you have or are downloading the LiveCD, when you are able to boot from it:

Go the the following site and download the boot info script. Run it and post the contents of RESULTS.txt here and we can help or suggest your options.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

You can burn the LiveCD on any computer, and your broken computer (unless it's a netbook) should boot the CD. If it doesn't, just make sure the CD is selected as the first boot option in BIOS. (If you need help with that, ask).

---

### Post by LostnConfused on 2011-03-26
I just set the CD to be the first to boot into in my BIOS part, but it still isn't doing it, it just goes straight to the Grub Rescue> screen. Ive tried restarting and everything 5 times atleast, I have 3 different CD's of Ubuntu and none of them are working.

---

### Post by LostnConfused on 2011-03-26
When I try to enter the Ubuntu CD or my Windows 7 CD, my computer just starts making a loud noise, sounds like an alarm going off.

---

### Post by LostnConfused on 2011-03-26
It will not allow me to boot into anything, and now I have to go run errands, and will be back in 45 minutes, so I hope somebody will come up with an answer by then, or still be here to help me when I get back, thank you.

---

### Post by drs305 on 2011-03-26
Sounds like the CD didn't burn correctly. If the CD drive is set to boot first (you hear it spinning up is one indication) then the reason you are getting the grub rescue prompt is because the BIOS gave up trying to boot the CD.

Since it's not working on the other computer either, there is most likely a problem with the disc. Try burning it a slow speed, ensure you are burning an image and not the file, and after burning it make sure to check the MD5SUM:
[How To MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

There is almost always someone around to help out, if we can.  :-)

---

### Post by Julian Luna on 2011-03-26
That happened to me before. Let me remember what I did... hmm yeah try running from the CD and installing the grub2 (Probably search the command line, which I don't know)
Hope this helps you
[http://aroundtheweb.info/2010/10/restorerecover-grub-2-ubuntu-10-10-maverick-meerkat-reinstalling-windows-xpvistawin7/](http://aroundtheweb.info/2010/10/restorerecover-grub-2-ubuntu-10-10-maverick-meerkat-reinstalling-windows-xpvistawin7/)
If not, you'll probably need to reinstall the whole ubuntu

---

### Post by cavalier911 on 2011-03-26
1. Is this a wubi install ?

2. Download and follow directions for running and posting output of boot_info_script :
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
This can be done from the ubuntu live cd.
With the information posted by you from the output of boot_info_script some suggestions can be made for you to safely restore your system so it boots again.

Use code tags when you post the output.

---

### Post by prshah on 2011-03-26
> **LostnConfused said:**
> I had windows 7 as my default OS
```

Error: no such partition.
grub rescue>
```
Tried to run my Windows 7 CD-DVD and nothing happens.


You need the Windows 7 installation CD to resolve this issue. Please see [http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html) for details on how to boot off your Windows 7 CD/DVD and recover your Win 7 installation.

Please post back here with details if you run into any problems.

---

### Post by drs305 on 2011-03-26
Threads merged. Creating multiple threads causes duplication of effort and possibly conflicting advice. Please create only one thread per issue.

---

### Post by LostnConfused on 2011-03-26
> **prshah said:**
> You need the Windows 7 installation CD to resolve this issue. Please see [http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html) for details on how to boot off your Windows 7 CD/DVD and recover your Win 7 installation.

Please post back here with details if you run into any problems.

I cannot do any commands within the Grub Rescue screen besides like sl or ls. I cannot boot into any CD, as I tried that and my computer just starts beeping very loud and doing nothing untill I hit escape, then it goes back to the Grub Rescue.
I dont know what else to do, I have tried 2 Ubuntu CD-DVD and they are both fresh out of the package, and I have tried my regular windows 7 installation CD-DVD.

---

### Post by prshah on 2011-03-27
> **LostnConfused said:**
> I cannot do any commands within the Grub Rescue screen 
I have tried my regular windows 7 installation CD-DVD.

1) The GRUB rescue screen will not be of help to you to solve this problem.
2) To boot off the Windows 7 CD, please make changes in the BIOS to boot off CD. If you don't know how to enter/make changes in the BIOS, please post back for more information; though I would suggest that in that case, it would be better for a qualified/knowledgeable person to take a look at it.
3) If you do not have a working Windows CD, please consider alternate "recovery" discs as detailed [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

---

