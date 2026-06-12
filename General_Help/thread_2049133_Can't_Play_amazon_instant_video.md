---
title: "Can't Play amazon instant video"
date: 2012-08-28
forum: General Help
---

### Post by cadcam on 2012-08-28
so...  I'm a fairly proficient computer user.  I code c, I build hardware, etc...  BUT FOR THE LIFE OF ME I CANNOT GET AMAZON VIDEO TO WORK ANYMORE!!  I don't know what the *beezwax* is going on.  I have installed hal, updated chrome, and restarted a bunch. 

me:  
32 12.04 ubuntu
chrome (standard release)
11.3 flash (built into chrome)

amazon instant video just goes black, after it loads, and doesn't play.  Adobe claims it's drm bull*#@*, but I think something else is happening.  

here is what terminal spits out when I run chrome...

```
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
```

it says that about every two seconds...  I googled the error, but only found a ridiculous bug fix that I can't believe is the solution to such a basic problem.

help??? 

thanks,
---

---

### Post by papibe on 2012-08-28
Hi cadcam.

Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=2037242&highlight=amazon"). It looks like you can solve it by installing a package.

Regards.

---

### Post by cadcam on 2012-08-28
Thanks for the quick reply!

I attempted to install the old hal libraries, and received this:  

```
andromaeda@Ranger:~$ sudo apt-get install hal libhal1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hal is already the newest version.
libhal1 is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-26-generic python-mako libdiscid0
  linux-headers-3.2.0-26 libdirectfb-extra
  libdmapsharing-3.0-2 python-markupsafe
  linux-headers-3.2.0-26-generic-pae libmusicbrainz3-6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andromaeda@Ranger:~$ 

```

Amzn vid still doesn't work...  did I miss something?

thanks,
A.

---

### Post by cadcam on 2012-08-29
A little extra note.  Amazon instant video won't play on all three of my ubuntu machines, all which are on 12.04.  However it *will* play on both of my windows machines (which are the same computers).  This is so annoying.  Any more thoughts?  I wrote amazon and complained, but they just said they will forward the email to the developers.

thanks,

---

### Post by jparchem on 2012-08-29
> **cadcam said:**
> A little extra note.  Amazon instant video won't play on all three of my ubuntu machines, all which are on 12.04.  However it *will* play on both of my windows machines (which are the same computers).  This is so annoying.  Any more thoughts?  I wrote amazon and complained, but they just said they will forward the email to the developers.

thanks,

You can always disable the chrome version of Flash and use the older but more reliable Adobe version if you've got the HAL libraries installed.  See [THIS ]("http://ubuntuforums.org/showthread.php?t=2018645")post:

---

### Post by cadcam on 2012-08-29
Thanks, jparchem!  Sure enough, fuuuurfox works great.  Such fail on flash and amazon.  I will write them and tell them they code at an elementary school level and are corporate whores..  Funny, that 11.3 is too cool for amazon.  Kind of like how some sites and software still can't deal with 64 platforms...  Brilliant!  Thanks again.

A.

---

### Post by cadcam on 2012-08-29
I'm not marking this as solved because amazon instant video and chrome's adobe 11.3 are still incompatible, and they should be ashamed.

---

### Post by edcompsci on 2013-06-13
flash ended linux support again.  I wonder if totem or xine are working on something.

Also, maybe trying the adobe-flashplugin pacckage instead of the flashplugin-installer will work.  I am trying that now.

I might also try mplayer plugin

[http://sourceforge.net/projects/mplayerplug-in/files/mplayerplug-in/v3.55/mplayerplug-in-3.55.tar.gz/download?use_mirror=hivelocity&download=](http://sourceforge.net/projects/mplayerplug-in/files/mplayerplug-in/v3.55/mplayerplug-in-3.55.tar.gz/download?use_mirror=hivelocity&download=)


okay none of that worked. Got it working though, with:
sudo apt-get install hal

then once it installs:
hald

...then it works

---

