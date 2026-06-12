---
title: "Mplayer and a Matrox card"
date: 2005-02-04
forum: General Help
---

### Post by darkoptix on 2005-02-04
Hey, I'm using Mplayer right now and i want to use the xmga/mga video outputs, but when I try to compile i get lots of errors. Mplayer compiles and makes fine, however the drivers give these errors:

grep: /lib/modules/2.6.8.1-3-386/build/include/linux/version.h: No such file or directory
grep: /lib/modules/2.6.8.1-3-386/build/include/linux/version.h: No such file or directory
grep: /lib/modules/2.6.8.1-3-386/build/include/linux/version.h: No such file or directory
grep: /lib/modules/2.6.8.1-3-386/build/include/linux/version.h: No such file or directory
make: Nothing to be done for `mga_vid.c'.

Any suggestions?

---

### Post by kultuur on 2005-02-05
Did you install the appropriate version of kernel-headers with apt-get ?  

*locate /include/linux/version.h*
gives on my computer (hoary) 
*/usr/src/linux-headers-2.6.10-2/include/linux/version.h*

---

### Post by darkoptix on 2005-02-05
I installed kernel-headers for my pc, but it still gives me those errors.
Also, when I locate /include/linux/version.h
It finds it in /usr/locate/linux/version.h
I'm on Warty if that helps.

---

### Post by kultuur on 2005-02-05
Oops, it's not kernel-headers, but linux-headers.

*sudo apt-get install linux-headers-686* for Intel Pentium, or
*sudo apt-get install linux-headers-k7* for AMD Athlon

Afterwards, *ls -l /usr/src* should list a directory *linux-headers-2.6.8xxxx* (warty).

The *locate* command is very fast, but gives only correct output after you update the database with *sudo updatedb*.  
*find /usr/src -name version.h* is a better, but slower alternative.

---

### Post by miho on 2005-02-05
Why are you using mplayer? There are many better media players out there. Surely one could just download the codec for Totem and have fun with that. :confused:

---

### Post by darkoptix on 2005-02-05
I really like MPlayer because it's the fastest so far that I've tried. I've tried Xine, but it is slow. Totem just sucks IMO. Ogle doesn't work for the same reason as MPlayer.

Thanks for quick reply. I am just going to try to apt-get linux headers.

---

### Post by darkoptix on 2005-02-07
I installed the linux-headers, and I still get the same issues when tring to compile. 

I found a mga-vid package on sympatic, It is a source for the mplayer mga and xmga. Should I use this?

---

### Post by lothar_m on 2005-02-08
hi,

i'm having the same problem.
when i try to install the mga_vid module i always get 

/lib/modules/2.6.8.1-3-386/build/include/linux/version.h: No such file or directory

i'm running warty and already installed linux-headers and mga-vid package via synaptic.

---

### Post by darkoptix on 2005-02-09
Sucess... well kinda.
I found why it wasn't finding the version.h files. It was because I had different linux headers than my kernel version.
After that happened, i then later found out that mga_vid can not compile in a 2.6 kernel, however there are patchs for this. I found a patch, and applied it. To my wonders it compiled. So i compiled and reinstalled Mplayer again. After thats done, I had to add the /dev/mga_vid and modprobe mga_vid to get Mplayer to use xmga.
This was all great but this could only be done when i run mplayer in root, not by any other user.
Also, when I reboot the /dev/mga_vid and loaded module mga_vid disappear.

Any suggestions.

---

### Post by darkoptix on 2005-02-11
bump...

---

### Post by kultuur on 2005-02-12
Good to hear you got it working.
[QUOTE=darkoptix]This was all great but this could only be done when i run mplayer in root, not by any other user.[/QUOTE]Perhaps a permission problem with /dev/mga_vid
*ls -l /dev/mga_vid* could give you a hint.
> Also, when I reboot the /dev/mga_vid and loaded module mga_vid disappear.Adding *mga_vid* to /etc/modules will load the module at startup.

---

### Post by darkoptix on 2005-02-14
Alright, getting a bit more closer now.
Putting the mga_vid in /etc/modules file fixed having to load it.
Unfortunally, when loading the dev with:
mknod /dev/mga_vid c 178 0
That is from the Mplayer Documentation to make the dev.
Also btw what are the c 178 and 0 for, maybe it would let me make more sence of what they do.
I have to:
chmod 777 /dev/mga_vid
to get the average user able to use.
However after a boot the /dev/mga_vid isn't there anymore.

I've been watching Star Trek: Voyager episodes, and right now i'm watching Ninja Scroll, and it's running great. Also dvds work great now, under mplayer, but xine and ogle have trouble playing them, but I don't care because Mplayer owns them anyways.

---

### Post by mindhaq on 2005-06-16
[QUOTE=darkoptix]However after a boot the /dev/mga_vid isn't there anymore.[/QUOTE]
Did you find a solution for this problem by now? I'm having exactly the same...

BTW, for other users searching the forums, some useful links and infos regarding mplayer and Matrox cards:

Patches for mga_vid to compile it with a 2.6 Kernel:
[http://attila.kinali.ch/mga/](http://attila.kinali.ch/mga/)

Install the package mga_vid_common for a testing tool, some docs, and an automatic entry for loading the module during boot.
After that, there is /usr/share/doc/mga-vid-common/README.Debian, but it seems to be a bit dated (4 Apr 2002). In there is talk about devfs, which I have no clue what it is.
But it says this on how to generate the device node - still, mine keeps vanishing after each reboot :(

```
  # mknod /dev/mga_vid c 178 0
  # chown root:video /dev/mga_vid
  # chmod 0660 /dev/mga_vid
```
Maybe one can compile the driver with package mga-vid-source as well (didn't try that yet).

---

### Post by amias on 2005-10-06
I'm trying to do the same thing , i got the module to compile using the
2.6 patched version of mga_vid , but i cant load the module at all , i just get this .

FATAL: Error inserting mga_vid (/lib/modules/2.6.12-9-386/kernel/drivers/video/mga_vid.ko): Invalid module format

my modutils are up to date as are all the rest of my packages , i'm using
breezy on an stable Athlon. oh and i did depmod -a to get the module dependencies upto date.

[QUOTE=darkoptix] Also btw what are the c 178 and 0 for, maybe it would let me make more sence of what they do.[/QUOTE]

they are the major and minor device numbers which are used to catalogue the devices behind the device nodes in /dev.
The actual name of the file could be anything its what the major and minor numbers point to that counts.
They are listed in the kernel documentation that comes with the sources (linux/Documentation/devices.txt) or just google
for devices.txt .

as an afterthought :

Is there i reson i for not distributing this as a binary module ? 
it would make things so much easier.

Toodle-pip
Amias

---

### Post by bowerymarc on 2007-02-12
questions:
1. is there a patch for the current 6.10 edgy kernel - 2.6.17.11 (or 2.6.17.10)?  Or will the '18 or '12 patch work from [http://attila.kinali.ch/mga/](http://attila.kinali.ch/mga/) 
<rant>
2. why is mga_vid_source even in Synaptic when it won't compile against the kernel in the release?  Either dump it or fix it I say!
3. in fact why isn't there binary for it?  Is it that much of an orphan?
</rant>

---

### Post by supermarchino on 2007-04-07
> **bowerymarc said:**
> questions:
1. is there a patch for the current 6.10 edgy kernel - 2.6.17.11 (or 2.6.17.10)?  Or will the '18 or '12 patch work from [http://attila.kinali.ch/mga/](http://attila.kinali.ch/mga/) 
<rant>
2. why is mga_vid_source even in Synaptic when it won't compile against the kernel in the release?  Either dump it or fix it I say!
3. in fact why isn't there binary for it?  Is it that much of an orphan?
</rant>

I agree. :(

---

### Post by pandan on 2007-05-18
[B]Hi,

when i issue the following compile command:[/B]

/usr/src/linux-source-2.6.20# fakeroot make-kpkg modules_image

**i get the following error: **

The UTS Release version in include/linux/version.h
     "" 
does not match current version:
     "2.6.20.3-ubuntu1" 
Please correct this.
make: *** [modules_image] Error 2

[B]I'm using a pentium3 computer with a Matrox G200 build into the mother board. by HP.

Anyone able to help?

Thanks,   Phil.[/B]

---

