---
title: "SevenMachines ppa"
date: 2011-11-13
forum: General Help
---

### Post by Condor Cluster on 2011-11-13
When I try to update, I seem to get the following error message:

*Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found*

Could this ppa now be dead?

Thanks

---

### Post by dino99 on 2011-11-13
its easy to see the latest update time, dont you, and check if that url still exist.

[https://launchpad.net/ubuntu/+ppas?name_filter=sevenmachines](https://launchpad.net/ubuntu/+ppas?name_filter=sevenmachines)

---

### Post by sosaudio1 on 2011-11-13
> **Condor Cluster said:**
> When I try to update, I seem to get the following error message:

*Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found*

Could this ppa now be dead?

Thanks

Having the same problems here on both of my boxes 32 bit and 64 bit

---

### Post by alphacrucis2 on 2011-11-13
If you are just wanting flash. Probably just use the flashaid firefox addon.

---

### Post by riverfr0zen on 2011-11-15
Sadly none of the new versions of flash available on either the Ubuntu repositories (adobe-flashplugin, flashplugin-installer), nor the tarball directly from Adobe work well at all on my 64-bit ATI box.

In fact, they are practically unusable when viewing fullscreen video.

I'd been using flashplugin64-installer from this ppa, and it was totally great, but sadly I uninstalled it to try out these other new options.

Now the ppa is no longer available, and I can't re-install the older version. Sux :(

---

### Post by gandaran on 2011-11-15
> **riverfr0zen said:**
> Sadly none of the new versions of flash available on either the Ubuntu repositories (adobe-flashplugin, flashplugin-installer), nor the tarball directly from Adobe work well at all on my 64-bit ATI box.

In fact, they are practically unusable when viewing fullscreen video.

I'd been using flashplugin64-installer from this ppa, and it was totally great, but sadly I uninstalled it to try out these other new options.

Now the ppa is no longer available, and I can't re-install the older version. Sux :(
the flash-aid addon for firefox can install 64-bits flash on ubuntu for use with all browsers, all the other flash packages you have tried are 32-bits flash.
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by riverfr0zen on 2011-11-15
Well, the SevenMachines one wasn't.

I did try Flash Aid, but it's sadly broken because the source website domain has expired (trying going to [http://updates.webgapps.org](http://updates.webgapps.org))

I also actually tried doing manually what Flash Aid does with a 64bit tarball from Adobe, but no luck -- Flash still unbearably sluggish.

---

### Post by NESFreak on 2011-11-16
[http://get.adobe.com/nl/flashplayer/otherversions/](http://get.adobe.com/nl/flashplayer/otherversions/)

After removing flashplugin64-installer (and removing the sevenmachines ppa from my sources), then just selecting linux 64 bit and ubuntu in the above link. It asked me if i'd like to add the partner repository, followd by the question to install the flash package from adobe. It seems to be up to date for lucid (version 11,1,102,55) and working rather well (for me).

---

### Post by riverfr0zen on 2011-11-16
I have tried using the installer from Adobe (which is not very different than adobe-flashplugin, probably just more up to date). However, I think the problem is in fact with these new 64-bit Flash builds from Adobe. It's much slower for me, especially when viewing fullscreen video (choppy video, computer becomes unresponsive for ages).

Somehow the 64-bit betas that the PPA provided worked perfectly, and that has now changed (for me, at least). Ah well, anyway, that's a separate topic.

---

### Post by NESFreak on 2011-11-16
> **riverfr0zen said:**
> I have tried using the installer from Adobe (which is not very different than adobe-flashplugin, probably just more up to date). However, I think the problem is in fact with these new 64-bit Flash builds from Adobe. It's much slower for me, especially when viewing fullscreen video (choppy video, computer becomes unresponsive for ages).

Somehow the 64-bit betas that the PPA provided worked perfectly, and that has now changed (for me, at least). Ah well, anyway, that's a separate topic.

I don't have the old file anymore (Since I just updated). Maybe someone else still has it?

It might however not be wise to use an old versions of flash. Adobe isn't exactly known for creating things free of security issues.

Have you tried updating your video driver? On my nvidia card it works fine (full HD youtube without tearing or speedissues).

---

### Post by Condor Cluster on 2011-11-19
I wonder if SevenMachines for Lucid is down for good, or just temporarily?

I might try Flash Aid with Firefox, the only other browser I have is Chrome, which I believe has it's own built in flash or something.

EDIT: just tried FlashAid, but it wanted to remove plugins, which I wasn't sure was a safe thing to do.  Also, it only gives you a source choice between Ububtu repos (way out of date), Adobe Betas (unstable) or Google Chrome.

---

### Post by CaptainMark on 2011-11-19
The sevenmachines ppa is no longer needed as the native 64bit flash support has been rolled into the flashplugin-installer package, in other words if you have the package flashplugin-installer installed on a 64bit system then it is the same as if you used to have the sevenmachines ppa in use.  The flashaid is just tool that deletes conflicting flash plugins, you shouldnt need it unless youve installed extra plugins by accident. 

my system has native flash 64bit support with no extra ppa repos just the flashplugin-installer package

---

### Post by Condor Cluster on 2011-11-19
Well, I'm on a 32 bit system, and checked in synaptics, already have flashplugin-installer installed. 

So if I remove the SevenMachines ppa, flash will update itself?

---

### Post by CaptainMark on 2011-11-19
exactly

---

