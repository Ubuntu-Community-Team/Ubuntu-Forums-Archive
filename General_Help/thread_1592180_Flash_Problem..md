---
title: "Flash Problem."
date: 2010-10-10
forum: General Help
---

### Post by Roasted on 2010-10-10
I have Ubuntu 64 bit, and I always had luck with the "SevenComputers" version of Flash, which allowed me to *gasp* close YouTube ads, and fast forward, and other fun stuff. The regular version of flash never allowed me to click on the video on the buttons or anything - everything was just non responsive. With this version, things are great though.

However, I just got a larger hard drive and did a fresh install of Ubuntu. I have the same .deb package saved that I used before, so I shouldn't have any issues. However, when I'm on YouTube, things are INCREDIBLY slow. When I search for something, it shows me 1 letter I type at a time in 3 second increments. So it literally takes 30 seconds just for the search bar to reveal "Pearl Jam" or whatever else I just typed in.

Any ideas? It's raging me. :(

---

### Post by Vaphell on 2010-10-10
doesn't sound like a flash issue - search bar is html/jscript
what does top run in terminal say?
what does about:****plugins typed in firefox address bar show?
do you have gfx drivers installed properly?

either way you can try the FLASH-AID addon for firefox created by lovinglinux, it should automate the installation process of flash in correct version.

---

### Post by linux4me on 2010-10-10
There's also the Adobe Flash installer in Software Center to install/remove Adobe Flash 10.

---

### Post by Roasted on 2010-10-10
> **linux4me said:**
> There's also the Adobe Flash installer in Software Center to install/remove Adobe Flash 10.

That's the one that doesn't allow me to click on anything. Anything on the video is nonclickable. I can't pause, change volume, full screen, nothing. I posted about it before and somebody linked me to a .deb which is Flash for 64 bit that basically doesn't royally suck. It worked flawlessly and a ton of users commended it. But a fresh install and the same .deb doesn't seem to yield the same response as I had last time... *shrug*

---

### Post by linux4me on 2010-10-10
> **Roasted said:**
> That's the one that doesn't allow me to click on anything. Anything on the video is nonclickable. I can't pause, change volume, full screen, nothing. I posted about it before and somebody linked me to a .deb which is Flash for 64 bit that basically doesn't royally suck. It worked flawlessly and a ton of users commended it. But a fresh install and the same .deb doesn't seem to yield the same response as I had last time... *shrug*
Weird. I just tried it (Maverick 64-bit, nouveau nvidia driver) and YouTube works fine for me. I can full-screen, adjust volume, and pause and restart the video. Are you using Firefox? Maybe it's a Firefox extension you're running that's interfering? Are you really still using 9.10 like your signature says? Maybe it's time for an upgrade.

---

### Post by oldos2er on 2010-10-10
> **linux4me said:**
> There's also the Adobe Flash installer in Software Center to install/remove Adobe Flash 10.

For 64-bit?

---

### Post by linux4me on 2010-10-10
> **oldos2er said:**
> For 64-bit?

Yep.

---

### Post by Roasted on 2010-10-10
> **linux4me said:**
> Weird. I just tried it (Maverick 64-bit, nouveau nvidia driver) and YouTube works fine for me. I can full-screen, adjust volume, and pause and restart the video. Are you using Firefox? Maybe it's a Firefox extension you're running that's interfering? Are you really still using 9.10 like your signature says? Maybe it's time for an upgrade.

Ah - no. I've been on 10.04 64 bit for a long time. Guess I just suck at updating my info here on the forums. :P 

Where in the software center is the exact 64 bit version you speak of? I can see an official Adobe Flash plugin option, but I always thought that was the 32 bit version with some sort of wrapper to make it work on 64 bit - which is where it bombed out on me... It seems as if you're on 10.10 already... perhaps the 10.10 software center yields different results than what I'm seeing on 10.04??

---

### Post by Vaphell on 2010-10-10
but it flashplugin-installer wants to install a bunch of 32bit libs and a wrapper for 32bit apps. It's not a native 64bit version.
If you want native 64 bit and can't be bothered with manual management, install FLASH-AID plugin for firefox, it will do that for you.
[https://addons.mozilla.org/pl/firefox/addon/161939/](https://addons.mozilla.org/pl/firefox/addon/161939/)

---

### Post by 1ceblu3 on 2010-10-10
you can download adobe's 64bit flash support for linux here 
[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

---

### Post by linux4me on 2010-10-10
> **Roasted said:**
> Ah - no. I've been on 10.04 64 bit for a long time. Guess I just suck at updating my info here on the forums. :P 

Where in the software center is the exact 64 bit version you speak of? I can see an official Adobe Flash plugin option, but I always thought that was the 32 bit version with some sort of wrapper to make it work on 64 bit - which is where it bombed out on me... It seems as if you're on 10.10 already... perhaps the 10.10 software center yields different results than what I'm seeing on 10.04??

I just type "flash" in the search box in Software Center, then select the Adobe Flash plugin which it says downloads and installs the Adobe Flash Player plugin. I thought this was just a helper app to do what the others mention doing directly via the Adobe site, and what was documented in the old Flash HowTo in the 64-bit forum. I used to do the whole 64-bit download thing, but since 10.04, I've just been using the one in Software Center. I've used  it on four different installs of 10.10, three 64-bit and one 32-bit system, one with nvidia graphics and three with Intel, and no issues yet.

I did notice something weird though when I just looked. The machine I'm on now I did an upgrade from 10.04 (clean install) to 10.10 using the alternate disk, and Software Center shows the Adobe Flash plugin is not installed. I suspect that's because I installed it in 10.04 and it wasn't replaced during the upgrade, but it's still working. It might be interesting to purge the old installation and try the 10.10 one from Software Center to see if it breaks.

---

### Post by Vaphell on 2010-10-10
set plugin.expose_full_path to true in **about:config** (type that in ff address bar)
and open about:****plugins to see what is the path of flash plugin

if it's simple /something/libflashplayer.so -> it's native
if there is some wrapper mentioned -> 32bit in 64bit environment.

---

### Post by linux4me on 2010-10-10
> **Vaphell said:**
> set plugin.expose_full_path to true in **about:config** (type that in ff address bar)
and open about:****plugins to see what is the path of flash plugin

if it's simple /something/libflashplayer.so -> it's native
if there is some wrapper mentioned -> 32bit in 64bit environment.
It's:
File: /usr/lib/mozilla/plugins/libflashplayer.so
Version: Shockwave Flash 10.0 r45

---

### Post by Vaphell on 2010-10-10
so it's a native 64bit, last version before adobe suspended works on 64bit linux for a year or so. It has serious vulnerability, go to adobe website, dl newer one
[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz)
and unpack it to the same location. Alternatively use FLASH-AID for firefox, it will do that for you.
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

and yes, in case of native 64bit flash package manager doesn't know about it, as it was installed without its control.

---

### Post by linux4me on 2010-10-10
That seems to be the version in Software Center currently. I just used the helper app to install over the existing version and the path and file version remain the same. The controls still work.

---

### Post by drdos2006 on 2010-10-10
This is the version I have in Ubuntu 9.10 64bit.

Shockwave Flash

    File: libflashplayer.so
    Version: 
    Shockwave Flash 10.2 d161

regards

---

### Post by efflandt on 2010-10-10
Version: Shockwave Flash 10.0 r45 is an older version that was discontinued.  Current real 64-bit flash is 10.2 r161 mentioned by drdos2006.  That works in Lucid and Maverick with Firefox 3.6.10 and 64-bit Hulu Desktop (but you have to point ~/.huludesktop to it).

The flashplugin-installer with 32-bit 10.1 r85 and 32-bit wrapper seems to segfault for me, crashing npviewer.bin in Firefox.  But I did not really notice when it happened (just /var/log/messages in Lucid or crash reports in Maverick beta).

---

### Post by linux4me on 2010-10-10
I just downloaded the tar containing the 64-bit 10.2d161 version using the link provided by Vaphell, renamed the existing copy of usr/lib/mozilla/plugins/libflashplayer.so and replaced it with the one from the tar file, then made the file executable and restarted Firefox. I now have a working version of the 10.2d161 file--all the controls still work--and Software Center still reports that I have the one included in the repos installed. 

Hulu (the site, not Hulu Desktop) works too without any tweaks.

I don't know if this helps the original poster; I hope so. I didn't mean to hijack the thread.

---

### Post by oldos2er on 2010-10-10
> **linux4me said:**
> Yep.

I can't find any flash in the repos except for 32-bit + nspluginwrapper. Are you using a particular PPA, or?

---

### Post by lovinglinux on 2010-10-10
> **oldos2er said:**
> I can't find any flash in the repos except for 32-bit + nspluginwrapper. Are you using a particular PPA, or?

Is not in the repos.

Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture. If you choose the 64bit install, it will download from Adobe and install it for you.

---

### Post by linux4me on 2010-10-10
> **oldos2er said:**
> I can't find any flash in the repos except for 32-bit + nspluginwrapper. Are you using a particular PPA, or?
I don't think it's in the repos. What I was doing was going Applications -> Software Center, then entering "flash" in the search box. It finds an Adobe Flash plugin, which I believe is a helper application that downloads the file from somewhere; however, it installs version 10.0r45 on 64-bit Ubuntu 10.10, which apparently has some serious security vulnerabilities. Thus my previous post about replacing the libflashplayer.so it installs with the one from Vaphell's link.

---

### Post by Roasted on 2010-10-14
For what it's worth, Chromium does not experience these issues. Just Firefox. Let's just hope Chromium's insane memory leak I had before is fixed... I had my system running for only a few days and Chromium had eaten up 3.6gb of RAM just to run...

---

