---
title: "how to uninstall an update or go back to a previous config"
date: 2009-07-15
forum: General Help
---

### Post by blackened07 on 2009-07-15
hi, I'm here with this little problem, I just installed ubuntu 9.04 and compiled the alsa driver for my sound card ( ca0106 ) it doesn't get along very well with my ubuntu, so anyway I installed some updates and some of them included alsa plugins, and when I restarted I realized I didn't have sound anymore, guess they entered in conflict...

I've been trying to look how to uninstall the updates but I really have no clue I don't even know how to look for, plus I don't know the name of the packages...

If anyone has an idea of how to remove them or go back to a previous configuration would be really apreciated, any tip or help

I'd like to try possible solutions instead of reinstalling it, but if there's no solution, I got no choice...

Greetings, and thanks in advance

---

### Post by Kraut~salat on 2009-07-15
if you used a GUI tool (like synaptic) to make your updates you can use the "history" entry ind the "file" menu to see which packets where updated.

btw: 
tim@pc:dpkg-query -S /lib/modules/2.6.28-13-generic/kernel/sound/pci/ca0106/snd-ca0106.ko
linux-image-2.6.28-13-generic: /lib/modules/2.6.28-13-generic/kernel/sound/pci/ca0106/snd-ca0106.ko

tells me, that your ca0106 Kernel module came with a new linux kernel. maybe you still have an older version installed which you can start from your boot loader

---

### Post by CatKiller on 2009-07-15
Also, once you've found the package that you wish to put to an older version, you can use Synaptic to force the version, and then lock the package so that it won't be updated in the future.

---

### Post by blackened07 on 2009-07-16
> **CatKiller said:**
> Also, once you've found the package that you wish to put to an older version, you can use Synaptic to force the version, and then lock the package so that it won't be updated in the future.
hello guys, thank you both for ask back...

I checked both suggestions, first the one of synaptic and I could see the packages, so now I'm not very sure which one I should uninstall, so I tried a reboot and at the grub I chose an older kernel to boot, and bingo it worked!!! I have my 5.1 back again.

However I'm having some troubles to identify which one I should uninstall, so I'd like to try it but it's not very clear for me how to put a package to an older version, I mean if i have to uninstall it first, or sth else that I'm missing, or if you guys could give me a tip or clue to start would be great. 

By the way this were the packages that synaptic shows at the history:
Commit Log for Mon Jul 13 21:54:56 2009


Actualizó los paquetes siguientes:

app-install-data-partner (11.9.04.1) to 11.9.04.2
cups (1.3.9-17ubuntu3.1) to 1.3.9-17ubuntu3.2
cups-bsd (1.3.9-17ubuntu3.1) to 1.3.9-17ubuntu3.2
cups-client (1.3.9-17ubuntu3.1) to 1.3.9-17ubuntu3.2
cups-common (1.3.9-17ubuntu3.1) to 1.3.9-17ubuntu3.2
firefox (3.0.10+nobinonly-0ubuntu0.9.04.1) to 3.0.11+build2+nobinonly-0ubuntu0.9.04.1
firefox-3.0 (3.0.10+nobinonly-0ubuntu0.9.04.1) to 3.0.11+build2+nobinonly-0ubuntu0.9.04.1
firefox-3.0-branding (3.0.10+nobinonly-0ubuntu0.9.04.1) to 3.0.11+build2+nobinonly-0ubuntu0.9.04.1
firefox-3.0-gnome-support (3.0.10+nobinonly-0ubuntu0.9.04.1) to 3.0.11+build2+nobinonly-0ubuntu0.9.04.1
firefox-gnome-support (3.0.10+nobinonly-0ubuntu0.9.04.1) to 3.0.11+build2+nobinonly-0ubuntu0.9.04.1
gnome-do-plugins (0.8.1.3+dfsg-0ubuntu3) to 0.8.1.3+dfsg-0ubuntu3.1
gstreamer0.10-plugins-good (0.10.14-1) to 0.10.14-1ubuntu0.1
gstreamer0.10-pulseaudio (0.10.14-1) to 0.10.14-1ubuntu0.1
hal (0.5.12~rc1+git20090403-0ubuntu2) to 0.5.12~rc1+git20090403-0ubuntu4
libcompress-raw-zlib-perl (2.015-1) to 2.015-1ubuntu0.1
libcups2 (1.3.9-17ubuntu3.1) to 1.3.9-17ubuntu3.2
libcupsimage2 (1.3.9-17ubuntu3.1) to 1.3.9-17ubuntu3.2
libhal-storage1 (0.5.12~rc1+git20090403-0ubuntu2) to 0.5.12~rc1+git20090403-0ubuntu4
libhal1 (0.5.12~rc1+git20090403-0ubuntu2) to 0.5.12~rc1+git20090403-0ubuntu4
libperl5.10 (5.10.0-19ubuntu1) to 5.10.0-19ubuntu1.1
libpoppler-glib4 (0.10.5-1ubuntu2) to 0.10.5-1ubuntu2.2
libpoppler4 (0.10.5-1ubuntu2) to 0.10.5-1ubuntu2.2
libsasl2-2 (2.1.22.dfsg1-23ubuntu3) to 2.1.22.dfsg1-23ubuntu3.1
libsasl2-modules (2.1.22.dfsg1-23ubuntu3) to 2.1.22.dfsg1-23ubuntu3.1
libssl-dev (0.9.8g-15ubuntu3) to 0.9.8g-15ubuntu3.2
libssl0.9.8 (0.9.8g-15ubuntu3) to 0.9.8g-15ubuntu3.2
libtiff4 (3.8.2-11) to 3.8.2-11ubuntu0.9.04.1
libxcb-render0 (1.1.93-0ubuntu3) to 1.1.93-0ubuntu3.1
libxcb-render0-dev (1.1.93-0ubuntu3) to 1.1.93-0ubuntu3.1
libxcb-shape0 (1.1.93-0ubuntu3) to 1.1.93-0ubuntu3.1
libxcb-shm0 (1.1.93-0ubuntu3) to 1.1.93-0ubuntu3.1
libxcb-xv0 (1.1.93-0ubuntu3) to 1.1.93-0ubuntu3.1
libxcb1 (1.1.93-0ubuntu3) to 1.1.93-0ubuntu3.1
libxcb1-dev (1.1.93-0ubuntu3) to 1.1.93-0ubuntu3.1
linux-headers-2.6.28-13 (2.6.28-13.44) to 2.6.28-13.45
linux-image-2.6.28-13-generic (2.6.28-13.44) to 2.6.28-13.45
linux-libc-dev (2.6.28-13.44) to 2.6.28-13.45
openssl (0.9.8g-15ubuntu3) to 0.9.8g-15ubuntu3.2
perl (5.10.0-19ubuntu1) to 5.10.0-19ubuntu1.1
perl-base (5.10.0-19ubuntu1) to 5.10.0-19ubuntu1.1
perl-modules (5.10.0-19ubuntu1) to 5.10.0-19ubuntu1.1
poppler-utils (0.10.5-1ubuntu2) to 0.10.5-1ubuntu2.2
tzdata (2009f-0ubuntu1) to 2009j-0ubuntu0.9.04
tzdata-java (2009f-0ubuntu1) to 2009j-0ubuntu0.9.04
xulrunner-1.9 (1.9.0.10+nobinonly-0ubuntu0.9.04.1) to 1.9.0.11+build2+nobinonly-0ubuntu0.9.04.1
xulrunner-1.9-gnome-support (1.9.0.10+nobinonly-0ubuntu0.9.04.1) to 1.9.0.11+build2+nobinonly-0ubuntu0.9.04.1

As you can see there is not an "alsa plugin update" my mistake xD, however I see a few pulseaudio updates, and some of hal, which I think are the ones that might be causing the conflict but please correct me if I'm wrong.

I'll be reading about this because I know not much about this, so thanks again and if I find sth useful I'll post it back

Greetings

---

### Post by CatKiller on 2009-07-16
> **blackened07 said:**
>  I checked both suggestions, first the one of synaptic and I could see the packages, so now I'm not very sure which one I should uninstall, so I tried a reboot and at the grub I chose an older kernel to boot, and bingo it worked!!! I have my 5.1 back again.

However I'm having some troubles to identify which one I should uninstall, so I'd like to try it but it's not very clear for me how to put a package to an older version, I mean if i have to uninstall it first, or sth else that I'm missing, or if you guys could give me a tip or clue to start would be great.

...

```
linux-image-2.6.28-13-generic (2.6.28-13.44) to 2.6.28-13.45
```

Since it appears that the older kernel works for you when the new one doesn't (from your boot test) you could find the linux-image-2.6.28-13-generic package and select Package -> Force version to set it back to 2.6.28-13.44 and then select Package -> Lock version. You could probably do similar with the linux-generic metapackage.

---

