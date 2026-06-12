---
title: "Why so slow?"
date: 2009-07-01
forum: General Help
---

### Post by veggen on 2009-07-01
I've just installed Ubuntu, ran the updater and I'm now playing with it, and I can't help but notice it's running drastically slower than my Win XP. I'm guessing I need to do some low level tweaks to get it up to speed.
Am I right about this or is there something I can do without being a guru?

Thanks.

---

### Post by HermanAB on 2009-07-01
What is slow?

File access, program loading, browsing the web?

If web browsing is slow, the most likely cause is a lame name server.  Run 'ipconfig /all' on Windows to see what name servers it uses, then modify Linux '/etc/resolv.conf' to use the same ones.

---

### Post by hibliss on 2009-07-01
Is this a partitioned install, or did you use Wubi?

---

### Post by veggen on 2009-07-01
> **HermanAB said:**
> What is slow?

File access, program loading, browsing the web?

Well, everything really, but mainly file access and program loading.

> **HermanAB said:**
> 
If web browsing is slow, the most likely cause is a lame name server.  Run 'ipconfig /all' on Windows to see what name servers it uses, then modify Linux '/etc/resolv.conf' to use the same ones.

Thanks for the tip, I'll give it a shot. Hopefully, it will alleviate the problem at least a little bit.

> **hibliss said:**
> Is this a partitioned install, or did you use Wubi?

A regular, partitioned install. I'm using ReiserFS, and I also have about 1.5GB in swap space... Maybe that gives some clue.

Thanks for your time, guys :)

---

### Post by veggen on 2009-07-02
Anyone?

Sorry for such a soon bump, but there's really a lot of traffic here so the topic sinks fast...

---

### Post by moster on 2009-07-02
You post so much information of your computer that people need more time to read everything ;)

edit:
From information you gave, I can tell you that Ubuntu do not have "Boost" button.

---

### Post by veggen on 2009-07-02
> **moster said:**
> You post so much information of your computer that people need more time to read everything ;)

Lol, you're absolutely right. :)
Let me correct that:

Intel C2D 2.2 GHz
Gigabyte 965P-S3
1 GB DDR2
GeForce 8600GT
IDE HDD Western Digital 160 GB (with 8MB of cache, I think)

I have 4 partitions:
2 NTFS, used by Win XP SP3 (20 GB, 110 GB)
1 ReiserFS, used by Ubuntu (20 GB)
1 swap (1.5 GB)

> **moster said:**
> 
edit:
From information you gave, I can tell you that Ubuntu do not have "Boost" button.

Sadly, I know... I was just hoping that there might be some easy tweak that could help with speed a bit. For example, I switched from Nautilus to XFE and it noticably improved my file access speed. So, if there are other defaults that can be replaced by a speedier alternative... well, I'm all ears :)

---

### Post by moster on 2009-07-03
Well, you have nvidia, that should leave some graphic problems outside... If you not do it already go to system > administration > hardware drivers and enable nvidia official driver. They are fastest. If you mean that Ubuntu have more sluggish GUI than windowsXP I would agree with you. Also, when using windows NTFS from ubuntu it is slower than using it from windows itself. ext3, ext4 are different story :)

Try playing little with system menu > prefereces > appearance. You can tweak there little.

I today install newest Ubuntu 9.4 on this computer:
AMD Duron 1.3 Ghz from cca 2002.
512 RAM
HDD IBM 7200 15GB from 1999. (XP is on 20 GB seagate 5400)
Nvidia geforce2 MX 400 64MB RAM

It was dual boot with XP. Loaded with old games ubuntu and XP. It is for some little boy that he can trash some computer. All I can say, it seems slower from fresh XP. But over time, when I loaded that XP with everyting boot is not 45 seconds anymore but 1,5 minute, everything starts to crawl. That is not happening with ubuntu. But I say again, GUI is slower. But I have effects on even on that Geforce 2 card. I was tempted to try putting vista, but there was not time, or space :)

Ok, I maybe little off topic now, but I was trying to make an example. Pushing data around disk should not be slower, startup should be around 45 sec on your drive... I do not really know.

here is one thread in this forum, that you can actually compare CPU results against similar to see if something is really wrong or that speed is just how it is gonna be from now on :)
[http://ubuntuforums.org/showthread.php?t=60264]("http://ubuntuforums.org/showthread.php?t=60264")

For the end, you do not have to be afraid for anything in ubuntu. It will work on 10 year old above computer, my current overclocked one, or some future icore10. :)

edit:
I forgot to say something really important that cost me a lot of money and nerves. Look what is compatible with linux and THEN buy your hardware. Not other way around. Instead of being able to crack WEP keys, you will not being able to even surf.

---

### Post by veggen on 2009-07-04
Thanks for the tips, and for clearing up some issues for me, as well!
I did some tweaking with drivers and default apps and it's working pretty good now.
You're right about the GUI, but if you steer clear of Nautilus, it's not bad at all.

---

