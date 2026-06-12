---
title: "Memory leaks?"
date: 2009-07-22
forum: General Help
---

### Post by poubelle on 2009-07-22
Hi there,

I moved to Ubuntu from MacOS a few months ago and I am really enjoying the journey.

My question is about memory leaks. 

I had this issue on my iBook when I used Firefox. Every so often I just had to reboot to clear it, it seemed. It would gradually get slower and slower until I rebooted. 

Now I've gone from a low 768MB RAM on a G4 with OS X to 256MB on a Pentium III with Ubuntu, and though obviously resources are in short supply to begin with, I believe I am seeing some lag that I assume is due to memory leaking. The performance will eventually grind to a halt after a couple of hours of continuous use, and rebooting helps a lot. This is quite frustrating.

I'm not too knowledgeable about hardware, but I understand from doing a bit of Google Maps API scripting that if Web applications are sometimes written without instructions to flush the memory they occupy when they are closed. With all the AJAX junk around these days (Facebook basically makes my computer unusable) I can see how my available memory would just dry up.

Is this a correct supposition? Has anyone observed memory leaks on an Ubuntu machine? Have you pinned it down to specific applications? 

I realize my options are limited with this machine -- it was rescued from the garbage and I can't afford to upgrade -- but it would help to know WHY my memory gets sucked up, and any techniques that will help or applications to avoid.

Thanks!

---

### Post by t4thfavor on 2009-07-22
Firefox 1.5 was generally pretty leaky, 2.0 was better, but still leaky. 3.0 is better yet, and most of us don't even notice, then again were not running 256MB ram.

3.5 has been up for days, and its currently occupying 300MB of ram with around 6 tabs open. Meaning its also fairly leaky, just better at cleaning up before it gets too big.

Are you running full Gnome, or did you install a smaller window manager?

If you have full Gnome still, I would recommend uninstalling the Ubuntu-desktop package, and installing xubuntu-desktop as it will save you on some of the memory footprint.

Also you could try and run chromium, though I'm not sure you will get much out of it.

Also the ram for that PIII should be easy to get for pennies on ebay, unless your unlucky and got RDRAM.

---

### Post by drvista on 2009-07-22
nautilus have memoy leak too it takes up to 1 gb of ram to view a folder full of images already reported years ago and no body doing something

---

### Post by poubelle on 2009-07-23
T4thfavour, thanks for the favour! (sorry. i had to.)

You got it: the evil RAMBUS. When I was given this computer I figured it would be cheap to upgrade... what a rude awakening that was. I haven't had this little RAM since 1998 when I was still using a 486 and had a 2GB hard drive.

I was just using Firefox with the FireFTP extension for a couple of hours and got bogged down again. If I reboot regularly it's OK. I guess the problem really is Firefox. 

I have tried XFCE but really disliked it. That was in March so I can't remember my exact reasons, but my conclusion was that I'm willing to sacrifice a little bit of performance to use Gnome... to be honest, I didn't find it to be such a huge difference anyway. If there's another WM you'd recommend I'd be willing to give it a try, but back then it seemed XCFE was the de facto standard for crappy computers, and it didn't really do it for me.

I've adapted as much as I can -- no previews of files in Nautilus, only run one application at a time when possible/when I'm patient, etc.

Is the Nautilus memory leak for real? There are other file managers, right? I could look into that. I do usually have a Nautilus window open at any given time.

---

### Post by mcduck on 2009-07-23
> **drvista said:**
> nautilus have memoy leak too it takes up to 1 gb of ram to view a folder full of images already reported years ago and no body doing something

Nope, doesn't do that for me, and based on the fact that "nobody's doing anything about it" it sounds more like a problem with your particular setup and definitely not like a common Nautilus bug. :)

(just browsing through a directory with 800 images, in thumbnail view, and no problems apart from the fact that it took a couple of seconds to load all the thumbnails..)

---

### Post by trwww on 2009-07-23
> **poubelle said:**
> 256MB on a Pentium III

This is not much resources at all for any contemporary OS. To be honest, my choice of OS for this system would be Windows XP, or probably even Win2k, or Redhat 9 Linux.

Thats probably the oldest "full service" OSes I would run on that machine.

Puppy Linux would be my first choice.

---

### Post by michy99 on 2009-07-23
> **trwww said:**
> This is not much resources at all for any contemporary OS. To be honest, my choice of OS for this system would be Windows XP, or probably even Win2k, or Redhat 9 Linux.

Thats probably the oldest "full service" OSes I would run on that machine.

Puppy Linux would be my first choice.

I'm using the same set-up, and apart from bogging down if I try to do too many things at one time, Ubuntu works fine.

---

### Post by trwww on 2009-07-24
> **michy99 said:**
> I'm using the same set-up, and apart from bogging down if I try to do too many things at one time, Ubuntu works fine.

Indeed. But with those specs, just having firefox loaded to a page with flash on it can be considered too many things at one time.

How big is your swap partition? Perhaps thats the OPs problem; not enough swap.

---

### Post by poubelle on 2009-08-08
> **trwww said:**
> This is not much resources at all for any contemporary OS. To be honest, my choice of OS for this system would be Windows XP, or probably even Win2k, or Redhat 9 Linux.

Well, here's a big old "duh" from me. :) There's a reason this computer was being thrown out. But it is what I have to deal with, so... here I am.

Windows 2000 was on the machine when I got it. Ubuntu works *significantly* better. I have no plans to experiment with other Windows (I hate Windows) nor to muck around with other Linux distros... I did a bit of that in the beginning and decided I like Ubuntu fine. I do observe memory leaks though.

> **trwww said:**
> Indeed. But with those specs, just having firefox loaded to a page with flash on it can be considered too many things at one time.

Yeah. I can't browse freely, but that's probably healthier for me. I'm annoyed by extraneous Flash anyway, and I just don't watch online video much now. (Youtube is far more taxing than most of the other video-sharing sites.) I use Flashblock and Noscript to help weed out the cruft.

> **trwww said:**
> How big is your swap partition? Perhaps thats the OPs problem; not enough swap.

I can't remember because, not being familiar with partitioning, I just used the installer's default. Is there a command that will tell me?

Oh, is this it?

```
df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G   12G  5.2G  70% /
tmpfs                 123M     0  123M   0% /lib/init/rw
varrun                123M  108K  123M   1% /var/run
varlock               123M     0  123M   0% /var/lock
udev                  123M  140K  123M   1% /dev
tmpfs                 123M   76K  123M   1% /dev/shm
lrm                   123M  2.2M  121M   2% /lib/modules/2.6.28-14-generic/volatile
/dev/sr0              529M  529M     0 100% /media/cdrom0
```

---

### Post by XCan on 2009-08-08
Use 
```
 free 
```
instead.

---

