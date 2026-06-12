---
title: "x server does not work"
date: 2010-12-24
forum: General Help
---

### Post by gbmtoday on 2010-12-24
hey there:)

I installed some insecure packages and after I reboot my laptop the gdm didnt come and it went straightly to CommandLine waiting for me to login .

then I did
```
apt-get install -f
```

but it didn't any good .

and when I try to starx I get this
[http://pastie.org/1402994](http://pastie.org/1402994)

any suggestions?

---

### Post by theasprint on 2010-12-24
Hi,

Can I know what Graphics card you are using now?

To show the Graphics card :
```
lspci | grep VGA
```

So I think after knowing what graphics card you use, then you can go and download the latest driver from your graphics card producer's website (nvidia, ati, intel etc), transfer the driver file into your PC, and install the graphics driver by: 

```
sudo bash <your graphics driver's directory
```

Hope this helps. But yes, it should be your graphics problem. 
Unless your gdm is gone.

---

### Post by gbmtoday on 2010-12-24
I installed nvidia-glx-185 and nvidia-current but it didnt help
my Graphic card is 
```
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 240M] (rev a2)
```

---

### Post by theasprint on 2010-12-24
Hi,

Where did you get your "nvidia-glx-185" and "nvidia-current"?
I assume from the Hardware Drivers menu in Ubuntu?

Tell you what, this is what I would do for all the Nvidia problems.
For your case:
1. Download the latest driver for your card at nvidia.com. Remember to download the Linux version

2. Then transfer the driver file into your PC.

3. Since gdm is already off (because you straight booted into CLI)
then you would just install the driver by:
```
sudo bash <your Nvidia driver's directory>
```

4. Then turn on gdm
```
sudo service gdm start
```

If you have problems, go to the thread in my signature below and try following the instructions of TheRawGod and see if it works.

* So far all the users I've helped have their problems solved, be it Graphics gone, lag, freezing etc.

Good Luck :D

---

### Post by gbmtoday on 2010-12-24
no I installed them by apt-get in recovery mode :) 

but I cant open the nvidia website .Would it be ok  if I install the nouveau driver  ?!

---

### Post by theasprint on 2010-12-24
Hi,

The problem actually lies within the nouveau driver.
The nouveau driver may not be completely compatible with all nvidia cards, (in fact most of them cause problems) thus causing users to experience freezing, lagging and unavailability to play flash videos.

If you can't open the Nvidia website, then use another PC to download, just like this one which you are using to post.
Then you may transfer you file to your original "spoilt" PC
(Transfer by any means, thumbdrive, LiveCD etc will do.)

And then follow my steps above to solve your problem.

One thing. Your driver isn't an optimus driver is it? Or else my solution would not work. Because I can solve non-optimus Nvidia problems, whereas the optimus problems, I don't think anyone can solve it.
Optimus is not supported with Ubuntu.

---

### Post by gbmtoday on 2010-12-25
ok

I Downloaded the driver from nvidia website.

and I installed it successfully . and then I used startx to see the Desktop ( gdm didnt work )

but when I restarted the my laptop it didnt go to the X and went straightly CLI .

I used Ctrl+alt+F7 and all that came was a blank screen.

I used startx and gdm but none of them worked .

I tried to install the driver again but it said 
```
The Nouveau kernel driver is currently in use by your system. This driver is incompatible with NVIDIA driver, and must be disabled before proceeding. Please ...
```

I dont know what's going on !! I installed it once and it worked but now ...
I already removed nvidia-glx nvidia-current and nvidia-settings 

What should I do now !?!:(

---

### Post by gbmtoday on 2010-12-25
I blacklisted some Nouveau stuff and installed the driver again so my X came again .
but gdm still doesnt work .

Thanks to theaspring

---

### Post by cascade9 on 2010-12-26
> **gbmtoday said:**
> hey there:)

I installed some insecure packages and after I reboot my laptop the gdm didnt come and it went straightly to CommandLine waiting for me to login .


If everything was working fine before you installed these 'insecure packages' then I'm 99.999% sure thats the cause. 

@ theasprint- just because somebody has an nVidia card installed doesnt mean that the nvidia drivers or nouveau are at fault. Also, constantly posting that people should d/l and manually install the nvidia drivers is NOT a god idea. It can make things much harder for user if there is a kernel update, etc.

---

### Post by theasprint on 2010-12-27
Hi,

Ok. Go to the thread in my signature below. (The one about Nvidia GeForce 330M) and follow the instructions of TheRawGod 

* I would just like to make sure if you've done this 
> putting the following parameter to [FONT=Courier New]/etc/default/grub: GRUB_CMDLINE_LINUX="nouveau.modeset=0"[/FONT].

And after that you should install the drivers after setting
```
sudo service gdm stop
```

just like what TheRawGod did. 

@Cascade9: I understand that there is a problem when users update their kernel, even I face this problem. But once after installing the driver again, everything will work as usual.

---

### Post by cascade9 on 2010-12-27
> **theasprint said:**
> @Cascade9: I understand that there is a problem when users update their kernel, even I face this problem. But once after installing the driver again, everything will work as usual.

Thats just one issue. Its the mostly likely issue to be hit, but its not the only one.... 

I just dont get why you are posting 'how to manually install nvidia drivers' in cases like this, where its probably not the problem.

---

### Post by theasprint on 2011-01-01
Hi,

Solved? Well Congrats!

Remember to report back if you meet any new problems.

---

### Post by cascade9 on 2011-01-02
> **theasprint said:**
> Hi,

Solved?

Funny idea of 'solved'. Initial post- GDM broken. Last post- GDM broken.

---

