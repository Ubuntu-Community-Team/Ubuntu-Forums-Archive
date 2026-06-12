---
title: "libGLU.so.1 + wrong elf class"
date: 2010-06-25
forum: General Help
---

### Post by Meepz on 2010-06-25
Hey guys, I got a problem with running a game (Tibia).

It worked fine earlier this day with my ubuntu 9.10, but after I upgraded to 10.4, I get following:



meepz@rat:~/Downloads/Tibia$ ./StartTibia.sh
./Tibia: error while loading shared libraries: libGLU.so.1: wrong ELF class: ELFCLASS64


I've downloaded libGLU.so.1 and copied it via 'sudo nautilus' into /lib (same as /lib64) , where it already has existed (I've exchanged it with the new one).

this gave me another error msg:

./Tibia: error while loading shared libraries: libGLU.so.1: cannot open  shared object file: No such file or directory 			 		

copying back brings me back to first error.

I would appreciate any advice, coz I've already used up all my ideas. 

(I've upgraded the system coz youtube vids wouldnt work on youtube itself, but through other webpages, tho only extremely laggy, even after i've installed adobe flash player. Well, now i got neither youtube, nor tibia and am kinda desperate >.< )

---

### Post by Meepz on 2010-06-25
I got the feeling my computer is playing with me now.
first I've tried to download libc6 (have read it on some board) from 

[http://packages.debian.org/de/etch/amd64/libc6/download](http://packages.debian.org/de/etch/amd64/libc6/download)

but the error page
**Not Found**

 The requested URL  /debian/pool/main/g/glibc/libc6_2.3.6.ds1-13etch10_amd64.deb was not  found on this server.


let me discard the option with libc6 for now.
Instead i've reinstalled that libGLU.so.1 file using synaptic (libglu1-mesa)


then i've tried my ./StartTibia.sh command again and now i got this line:


./Tibia: ./libc6/libc.so.6: version `GLIBC_2.11' not found (required by /usr/lib32/libGLU.so.1)



reinstalled libc6 with synaptic, but i still get the msg 'glibc_2.11 not found...'

its so annoying to be a noob >.<

---

### Post by Meepz on 2010-06-27
bump

still couldnt find a solution..
at least i've made  youtube run (by pasting libflashplayer.so into  /home/meepz/.mozilla/plugins)

just found a 'new' command in  another thread, maybe this would also help: 

lddmeepz@rat:~$ ldd  -v /bin/sh
    linux-vdso.so.1 =>  (0x00007fffc9dff000)
     libc.so.6 => /lib/libc.so.6 (0x00007f55e994f000)
     /lib64/ld-linux-x86-64.so.2 (0x00007f55e9cf2000)

    Version  information:
    /bin/sh:
        libc.so.6 (GLIBC_2.4) =>  /lib/libc.so.6
        libc.so.6 (GLIBC_2.3) => /lib/libc.so.6
         libc.so.6 (GLIBC_2.3.4) => /lib/libc.so.6
        libc.so.6  (GLIBC_2.11) => /lib/libc.so.6
        libc.so.6 (GLIBC_2.2.5)  => /lib/libc.so.6
    /lib/libc.so.6:
         ld-linux-x86-64.so.2 (GLIBC_PRIVATE) => /lib64/ld-linux-x86-64.so.2
         ld-linux-x86-64.so.2 (GLIBC_2.3) => /lib64/ld-linux-x86-64.so.2

pls,  i dont know what to search for anymore

---

### Post by dino99 on 2010-06-27
remember one important thing: if ubuntu devs fine tuned packages and scripts, well its not for nothing :mad:

so, mixing and installing package(s)/settings from untrusted location(s) or other distro (debian in your case) will drop you into troubles if your skills are not proved.

---

### Post by dragos240 on 2010-06-27
Type this in a terminal:
uname -a

For some reason it seems you upgraded to 32 bit, and you were previously using 64 bit, that's what it's saying here, I'm not entirely sure why, but it looks like that's what happened. Please post the result.

---

### Post by Meepz on 2010-06-27
meepz@rat:~$ uname -a
Linux rat 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux


ty for replies

---

### Post by Meepz on 2010-06-27
> **dino99 said:**
> remember one important thing: if ubuntu devs fine tuned packages and scripts, well its not for nothing :mad:

so, mixing and installing package(s)/settings from untrusted location(s) or other distro (debian in your case) will drop you into troubles if your skills are not proved.


i'm completely new with ubuntu (got the installation cd from friends and gotta deal with everything else alone)
so i've read forum entries and did what seemed to help in my case. All these terms are new to me, but i'm trying to learn =S

---

### Post by dragos240 on 2010-06-27
> **Meepz said:**
> meepz@rat:~$ uname -a
Linux rat 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux


ty for replies

Thats very interesting. Wrong elf-class 64 usually means that you're on a 32 bit system, trying to run a 64 bit app. Very strange. I hate to say this, but if you have all those issues with libs, you might want to consider a reinstall, backup your things, and start fresh.

---

### Post by Meepz on 2010-06-27
My system has been installed fresh.. 
anyways, would i need to backup any system files? Or would it be enough to just save my personal data on my fat32 partition and format my main partition + reinstall ubuntu karmic koala with my iso cd?
I'm not even sure if thats the one that would fit my hardware, how can i find out?

I've also had problems with youtube, but solved that by downloading libflashplayer.so, creating a 'plugins' folder in .mozilla and pasting the .so file there.

---

### Post by dragos240 on 2010-06-27
> **Meepz said:**
> My system has been installed fresh.. 
anyways, would i need to backup any system files? Or would it be enough to just save my personal data on my fat32 partition and format my main partition + reinstall ubuntu karmic koala with my iso cd?
I'm not even sure if thats the one that would fit my hardware, how can i find out?

I've also had problems with youtube, but solved that by downloading libflashplayer.so, creating a 'plugins' folder in .mozilla and pasting the .so file there.

No need to backup any system files, just backup personal ones. You should be fine now. Sorry about the problem, we at ubuntuforums.org will always help with your problem, whatever it may be. Don't be afraid to ask! :popcorn:

---

### Post by Meepz on 2010-06-27
ty (=

it already helps to know theres some completely screwed up problem thats bothering me @.@
I guess i should keep 9.10 then instead of upgrading.. 
well, i'll do that now, thx again

---

### Post by dragos240 on 2010-06-27
> **Meepz said:**
> ty (=

it already helps to know theres some completely screwed up problem thats bothering me @.@
I guess i should keep 9.10 then instead of upgrading.. 
well, i'll do that now, thx again

Upgrading has really always been a problem for many people here. I say stick with a LTS release, but stick to what you have for now.

---

### Post by Meepz on 2010-06-27
meepz@rat:~/Games/Tibia$ ./StartTibia.sh
./Tibia: error while loading shared libraries: libGLU.so.1: wrong ELF class: ELFCLASS64

Reinstallation didnt rlly help... I also got another error report about a kernel problem.. It says 'Your system might become unstable now and might need to be restarted'

I'm running update manager right now for package files and will see if that helps.

---

### Post by Meepz on 2010-06-27
okay, I'm getting desperate... after I've installed all the packages (285) with Update Manager and the program asked for reboot, my comp wouldnt boot at all.. instead i've had a blackscreen with these lines:

fsck from util-linux-ng 2.16
dev/sda4(the part where ubuntu got installed): clean, 5436/536378 files, 5363/433226 blocks (i didnt note the exact numbers, these are random)


are there packages which i shouldnt install? or was it just my harddisk that got too hot?
anyway, i've reinstalled ubuntu again and didnt download anything so far.
maybe i should get a completely new computer >.<

ps: still says wrong elf class when i try to run Tibia

./Tibia: error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS64

---

### Post by Meepz on 2010-06-27
Hahaha this is crazy
I've done nothing but downloading wine with software manager + opened libc6 folder in the tibia folder, then i've typed ./StartTibia.sh, which actually opened a window where i could login into the game.. but the startscreen has been upside down and here's a screen shot of how the game itself looked like:

[http://www.speedyshare.com/files/23155306/Linux.png](http://www.speedyshare.com/files/23155306/Linux.png)

also in the graphics options u usually could choose between opengl and directx, which just doesnt exist now :confused::confused::confused:



fine, with a graphics driver it seems to work. sry for all the inconvenience

---

### Post by CedricMC on 2010-12-08
If you reinstall libc6, maybe [this]("http://forum.tibia.com/forum/?action=thread&threadid=3242386") will help:

I get the following message from the GNU/Linux client:

```
./Tibia: ./libc6/libc.so.6: version `GLIBC_2.11' not found (required by /usr/lib/libGLU.so.1)
```

Checked on Ubuntu 10.04 i386 & amd64. There is some kind of conflict between Tibia's libc and system's libc. An easy fix is to edit ``StartTibia.sh'' and change the last line from

```
./libc6/ld-linux.so.2 --library-path ./libc6 ./Tibia
```

to

```
/lib/ld-linux.so.2 --library-path /lib ./Tibia
```

in order to fully use system's libc.

---

