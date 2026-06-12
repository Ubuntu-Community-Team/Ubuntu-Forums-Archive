---
title: "cannot view youtube, liveleak, etc., videos. YES flash is installed"
date: 2010-05-17
forum: General Help
---

### Post by jjloupe on 2010-05-17
I try with different browsers. I updated everything. I can view flash on websites...just not movies on sites such as youtube and liveleak.

Anyone?

---

### Post by SlidingHorn on 2010-05-17
Are you receiving an error message?  What happens when you try to load the videos?  Is it a blank whitespace?  Is there a placeholder for the flash object?  More information will be needed in order to attempt to help you out here...

---

### Post by jjloupe on 2010-05-17
Firefox black screen...Opera white screen. It's just flash videos that are affected. 

Ubuntu 10.04. nor error messages, it just doesn't work,

---

### Post by jarviser on 2010-05-17
> **jjloupe said:**
> Firefox black screen...Opera white screen. It's just flash videos that are affected. 

Ubuntu 10.04. nor error messages, it just doesn't work,

I finally got mine to work by installing the Adobe-flashplugin for Lucid in Synaptic rather than the usual flashplugin-nonfree or extras package.  I'm not sure which repository I found it on. As usual with Ubuntu (in comparison with Mint) you have to delve around in all sorts of repositories to get media working.

---

### Post by soltanis on 2010-05-17
Don't install flash from Synaptic, instead do

```

sudo apt-get install flashplugin-nonfree

```

I'm not sure if you have to enable the medibuntu repositories in order to do that. If all else fails go to the Adobe website and download the .deb package they have available for download there.

Also, if you are running a 64 bit system, Flash has always had teething problems on there with Linux. You might have more luck with the 32 bit version?

---

### Post by jjloupe on 2010-05-17
did the apt-get thing already...still nothing.

Got the update from Adobe...still nothing.

Using 32 bit.

As I said...FLASH works, on the adobe sites, flash website, etc. Ubuntu will just not allow me to watch flash videos..
This is all very frustrating.

---

### Post by lovinglinux on 2010-05-17
See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by lovinglinux on 2010-05-17
Duplicate. Sorry, the forum was not responding.

---

### Post by lovinglinux on 2010-05-17
Duplicate. Sorry, the forum was not responding.

---

### Post by jjloupe on 2010-05-17
I uninstalled everything as you said in the link, but that still didn't work. So I went back to youtube, and  it told me I needed to install flash (again). This time, instead of using the info bar at the top of the screen, I installed directly from the link inside the video window, and all works fine now.

---

