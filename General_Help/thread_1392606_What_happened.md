---
title: "What happened?"
date: 2010-01-28
forum: General Help
---

### Post by Jerriy on 2010-01-28
I updated my ubuntu (regular update that happenes every couple of days) and suddenly everything is extremely slow. Too slow to play video like youtube for example. 

No idea what happened (I wasn't running a new program or tinkering with anything) I was going through my old routine but today it turned out to be anything but routine.

How does one revert updates that already happened? I need to do that ASAP!

---

### Post by skymera on 2010-01-28
First we should see what is using all your CPU (Which i assume is making your PC slow).

```
 htop 
``` (Htop is nicer than top and you can sort in order of CPU usage)

How much disk space have you got free? Post output of

```
 df -h 
```

---

### Post by Jerriy on 2010-01-28
> **skymera said:**
> First we should see what is using all your CPU (Which i assume is making your PC slow).

```
 htop 
``` (Htop is nicer than top and you can sort in order of CPU usage)```
The program 'htop' is currently not installed.  You can install it by typing:
sudo apt-get install htop
bash: htop: command not found
```> 


How much disk space have you got free? Post output of

```
 df -h 
``````
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              28G   11G   16G  42% /
tmpfs                 1.7G     0  1.7G   0% /lib/init/rw
varrun                1.7G  320K  1.6G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G  172K  1.6G   1% /dev
tmpfs                 1.7G   76K  1.6G   1% /dev/shm
lrm                   1.7G  2.2M  1.6G   1% /lib/modules/2.6.28-17-generic/volatile

```

---

### Post by skymera on 2010-01-28
> **strAlan said:**
> snip

QFT
This person is clearly new, this post is unnecessary and harsh.

@Jerriy ```
 sudo apt-get install htop 
```
Now htop should work from the terminal.

---

### Post by Jerriy on 2010-01-28
He should've first explained why I don't have htop before rediculously resorting to warnings... Amazing! It's like as if I have signed a contract to install a command-line program that I have never ever heard before. Some people are utterly clueless when it comes to human interaction.  

Anyway here is it:```

  1  [|||                                    5.2%]     Tasks: 186 total, 1 running
  2  [|                                      0.6%]     Load average: 0.16 0.18 0.15 
  3  [||||                                   6.4%]     Uptime: 00:35:16
  4  [||                                     1.1%]
  Mem[||||||||||||||                   467/3276MB]
  Swp[                                      0/0MB]

  PID USER     PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command                                      
 3198 root      20   0  330M 35896 12572 S  2.0  1.1  0:33.09 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/l
 6015 mypc      20   0  391M  128M 27756 S  5.0  3.9  0:51.11 /usr/lib/firefox-3.5.7/firefox-3.5
 3794 mypc      20   0 20784 11492  8592 S  1.0  0.3  0:02.87 /usr/bin/metacity --replace --replace
10230 mypc      20   0  2608  1260   964 R  1.0  0.0  0:00.26 htop
 3012 haldaemo  20   0  6680  4488  3688 S  0.0  0.1  0:00.24 /usr/sbin/hald
 3015 root      20   0 17380  2604  1792 S  0.0  0.1  0:00.04 /usr/sbin/console-kit-daemon
 3908 mypc      20   0 21880  8528  6984 S  0.0  0.3  0:02.67 /usr/lib/gnome-applets/multiload-applet-2 --o
10028 mypc      20   0 34016 14808  9960 S  1.0  0.4  0:00.68 gnome-terminal
 4037 mypc      20   0 16676  2620  1428 S  1.0  0.1  0:04.55 gnome-screensaver
 3778 mypc      20   0 50876 22344 16340 S  0.0  0.7  0:07.48 /usr/bin/mobloquer -session 10858916454448064
    1 root      20   0  3084  1884   564 S  0.0  0.1  0:06.44 /sbin/init
 1010 root      16  -4  2352   604   320 S  0.0  0.0  0:00.06 /sbin/udevd --daemon
 2354 root      20   0  1808   524   460 S  0.0  0.0  0:00.00 /sbin/getty 38400 tty4
 2355 root      20   0  1808   532   460 S  0.0  0.0  0:00.00 /sbin/getty 38400 tty5
 2358 root      20   0  1808   528   460 S  0.0  0.0  0:00.00 /sbin/getty 38400 tty2
 2359 root      20   0  1808   528   460 S  0.0  0.0  0:00.00 /sbin/getty 38400 tty3
 2360 root      20   0  1808   532   460 S  0.0  0.0  0:00.00 /sbin/getty 38400 tty6
 2398 messageb  20   0  2992  1392   812 S  0.0  0.0  0:00.12 /bin/dbus-daemon --system
 2494 root      25   5 59896 58908   604 S  0.0  1.8  0:08.50 /usr/bin/moblock -p /var/lib/blockcontrol/gua
 2499 root      39  19  2004   712   468 S  0.0  0.0  0:00.00 /bin/sh /usr/bin/blockcontrol.wd
 2727 clamav    20   0 98736 88184   516 S  0.0  2.6  0:00.00 /usr/sbin/clamd
 2728 clamav    20   0 98736 88184   516 S  0.0  2.6  0:00.00 /usr/sbin/clamd
 2829 clamav    20   0  3248  1372  1068 S  0.0  0.0  0:00.06 /usr/bin/freshclam -d --quiet
 2952 privoxy   20   0  2764   988   556 S  0.0  0.0  0:00.00 /usr/sbin/privoxy --pidfile /var/run/privoxy.
F1Help  F2Setup F3SearchF4InvertF5Tree  F6SortByF7Nice -F8Nice +F9Kill  F10Quit                            


```

---

### Post by skymera on 2010-01-28
ok well that shows CPU usage relatively normal.

Is the computer still slow? What graphics card do you hagve?

---

### Post by Jerriy on 2010-01-28
Nvidia

Did somethig happened with that?

---

### Post by skymera on 2010-01-28
Possibly.

How did you install the Nvidia driver?
I suggest using Envy opposed to Jockey.

```
 sudo apt-get install envyng-core 
```
then run using
```
 sudo envyng -t 
```
Follow the instructions to install the Nvidia driver and then restart.

See if that helps.

---

### Post by Jerriy on 2010-01-28
What is jockey? do I have that now?

---

### Post by t4thfavor on 2010-01-28
Flash has been slow on all my Ubuntu PC's since a while ago. I just learned to hate Adobe more. 

I bet that there was an update to Firefox that made the existing flash plugin even slower.

I know if you run flash on firefox on 64bit (like I do) it's disgustingly slow.

Jockey:

[http://www.google.com/search?q=ubuntu+jockey&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=ubuntu+jockey&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

default driver manager in Ubuntu.

---

### Post by Jerriy on 2010-01-28
What concerns me is that I was ok the way things were until yesterday. What on earth happened today? That is a mystery

---

### Post by Jerriy on 2010-01-28
> **t4thfavor said:**
> Flash has been slow on all my Ubuntu PC's since a while ago. I just learned to hate Adobe more. 

I bet that there was an update to Firefox that made the existing flash plugin even slower.

I know if you run flash on firefox on 64bit (like I do) it's disgustingly slow.

Jockey:

[http://www.google.com/search?q=ubuntu+jockey&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=ubuntu+jockey&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

default driver manager in Ubuntu.So did something definitely happen recently then (just saw another thread right here in this forum where someone else also run into memory problems)

---

### Post by Jerriy on 2010-01-28
Now that I think about it. I noticed that the last update lasted literally more than half an hour (i left my desk so I don't know how long it lasted on top of that)

Usually a normal update takes less than 5 minutes. A firefox upgrade a little longer. But I don't remember if i ever had an auto-update that lasted more than 30 or so minutes. So something is up.

---

### Post by Jerriy on 2010-01-28
> **skymera said:**
> Possibly.

How did you install the Nvidia driver?
I suggest using Envy opposed to Jockey.

```
 sudo apt-get install envyng-core 
```
then run using
```
 sudo envyng -t 
```
Follow the instructions to install the Nvidia driver and then restart.

See if that helps.Just done all that. 

But nothing seems to have improved as far as watching video is concerned

---

### Post by Jerriy on 2010-01-28
Is there a quick solution? Right now it's the best way for me to go 'back to square one' and repeat what I did last year (I took the time to set up the sound and video - something which seems to be the most prominent problem one gets when one installs Ubuntu).

By quick I mean for example simply reverting updates or something like that.

---

### Post by t4thfavor on 2010-01-28
I just followed this tut
[http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/](http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/)
With this flash player plugin (x64)
[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

and it appears to work a bit better, I don't have stopped video with ongoing sound, and it seems altogether smoother.

---

### Post by Jerriy on 2010-01-28
> **t4thfavor said:**
> I just followed this tut
[http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/](http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/)
With this flash player plugin (x64)
[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

and it appears to work a bit better, I don't have stopped video with ongoing sound, and it seems altogether smoother.


Is that also the same for non-Koala people?(as you can see under my nick I'm still on Jaunty)
.

---

### Post by t4thfavor on 2010-01-28
I can never trust the OS listed, I always forget to update mine. I supose this will work on Jaunty, you may want to backup the dir before you put the new .so in place, just in case.

---

### Post by Jerriy on 2010-01-28
I did what was on that site: [http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/](http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/)

Adobe tells me "You have version 10,0,42,34 installed"

---

### Post by MaindotC on 2010-01-28
> **Jerriy said:**
> wtf?

You don't understand English instructions?

---

### Post by Jerriy on 2010-01-28
Right now the weirdest things are happening

When I go here: [http://www.10mg.nl/](http://www.10mg.nl/) (url suggested by that 64-flash install tip of yours, t4thfavor) I get the message that the required flash plugin **7 or higher was not found** on my system!!!

---

### Post by t4thfavor on 2010-01-28
By far the sickest/funniest thing I have ever seen.

your /usr/lib/mozilla/plugins$ ls -lah
total 9.5M
drwxr-xr-x 2 root root 4.0K 2010-01-28 08:15 .
drwxr-xr-x 4 root root 4.0K 2009-10-27 14:06 ..
-rwxr-xr-x 1 root root 9.2M 2010-01-28 11:29 libflashplayer.so
-rw-r--r-- 1 root root 6.0K 2010-01-16 11:32 librhythmbox-itms-detection-plugin.so
-rw-r--r-- 1 root root 100K 2009-11-11 04:15 libtotem-cone-plugin.so
-rw-r--r-- 1 root root 104K 2009-11-11 04:15 libtotem-gmp-plugin.so
-rw-r--r-- 1 root root  72K 2009-11-11 04:15 libtotem-mully-plugin.so
-rw-r--r-- 1 root root  80K 2009-11-11 04:15 libtotem-narrowspace-plugin.so
chance@chance-laptop:/usr/lib/mozilla/plugins$ 
should look something like this. Perhaps you are still missing a plugin.

---

### Post by Jerriy on 2010-01-28
Now we're on to something cuz mine is definitely different: it has got "alternatives" whatever the hell they are:```
total 9.6M
drwxr-xr-x 2 root root 4.0K 2010-01-28 18:19 .
drwxr-xr-x 4 root root 4.0K 2008-10-30 00:02 ..
lrwxrwxrwx 1 root root   37 2010-01-28 16:53 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
-rw-r--r-- 1 root root  79K 2009-02-09 16:42 gecko-mediaplayer-dvx.so
-rw-r--r-- 1 root root  79K 2009-02-09 16:42 gecko-mediaplayer-qt.so
-rw-r--r-- 1 root root  79K 2009-02-09 16:42 gecko-mediaplayer-rm.so
-rw-r--r-- 1 root root  79K 2009-02-09 16:42 gecko-mediaplayer.so
-rw-r--r-- 1 root root  79K 2009-02-09 16:42 gecko-mediaplayer-wmp.so
-rwxr-xr-x 1 root root 9.2M 2010-01-28 18:19 libflashplayer.so
lrwxrwxrwx 1 root root   39 2009-05-31 17:26 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 root root   39 2009-08-16 22:58 nphelix.so -> /opt/real/RealPlayer/mozilla/nphelix.so
lrwxrwxrwx 1 root root   40 2009-08-16 22:58 nphelix.xpt -> /opt/real/RealPlayer/mozilla/nphelix.xpt

```

---

### Post by t4thfavor on 2010-01-28
Well you should probably look into synaptic for how to remove that alternative one. I don't think it's as easy as just deleting the symlink.

---

### Post by Jerriy on 2010-01-28
Speculation: maybe this is a flash problem exasterbated by one notorious Jaunty-specific issue: the Shiretoko affair

---

### Post by MaindotC on 2010-01-28
I ran into a similar problem viewing video on NHL.com.  What I had to do was, using Synaptic (System -> Administration -> Synaptic Package Manager for those that can't figure it out) mark adobe-flashplugin and flashplugin-nonfree for COMPLETE REMOVAL.  Then I downloaded the .deb for flashplayer from the Adobe website and installed.  After I installed, I got an update notification saying it would upgrade that package from 10.0.42.34-1 to 10.0.42.34-2 and followed the prompts.  Granted, this for 8.04 not 9.04 and above.

---

### Post by Abekonge on 2010-01-28
I think I have the same problem - or at least the experience: Suddenly two or three days ago - everything is slow: minimizing and maximizing is slow - maybe 3 sec. lag - something which have been very fast up till then. Shifting between windows is also slow. I have changed nothing - only updated according to the usual updates. 

Flash works fine though.

---

### Post by Jerriy on 2010-01-28
I removed flash completely from synaptic. But nothing changed (obviously there is still some kind of flash since youtube isn't going "blank" and asking me to install flash but instead loading and buffering for dozens of seconds, followed by 3 seconds of run, then interruption.... (this goes on forever)

But as can be seen below there is no flash in /usr/lib/mozilla/plugins

drwxr-xr-x 2 root root 4.0K 2010-01-28 20:36 .
drwxr-xr-x 4 root root 4.0K 2008-10-30 00:02 ..
-rw-r--r-- 1 root root  79K 2009-02-09 16:42 gecko-mediaplayer-dvx.so
-rw-r--r-- 1 root root  79K 2009-02-09 16:42 gecko-mediaplayer-qt.so
-rw-r--r-- 1 root root  79K 2009-02-09 16:42 gecko-mediaplayer-rm.so
-rw-r--r-- 1 root root  79K 2009-02-09 16:42 gecko-mediaplayer.so
-rw-r--r-- 1 root root  79K 2009-02-09 16:42 gecko-mediaplayer-wmp.so
lrwxrwxrwx 1 root root   39 2009-05-31 17:26 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 root root   39 2009-08-16 22:58 nphelix.so -> /opt/real/RealPlayer/mozilla/nphelix.so
lrwxrwxrwx 1 root root   40 2009-08-16 22:58 nphelix.xpt -> /opt/real/RealPlayer/mozilla/nphelix.xpt

---

### Post by Jerriy on 2010-01-28
> **Abekonge said:**
> I think I have the same problem - or at least the experience: Suddenly two or three days ago - everything is slow: minimizing and maximizing is slow - maybe 3 sec. lag - something which have been very fast up till then. Shifting between windows is also slow. I have changed nothing - only updated according to the usual updates. 

Flash works fine though.Something is definitely going on. The absolute proof of that is, as I said earlier, the extraordinary amount of time the last general update required: ususally this takes less than 3 (as in THREE) minutes - the latest auto update took more than 30 (as in THIRTY) minutes.

---

### Post by Abekonge on 2010-01-28
more details: my bookmarks-menu in firefox takes 3 seconds to load!! and switching between tabs is also markedly slower.

Isn't anyone else having similar experiences? It is very serious for me. My Ubuntu system just went from being blazingly fast to being slower than vista.

---

### Post by MaindotC on 2010-01-28
> **Jerriy said:**
> I removed flash completely from synaptic. But nothing changed (obviously there is still some kind of flash since youtube isn't going "blank" and asking me to install flash but instead loading and buffering for dozens of seconds, followed by 3 seconds of run, then interruption.... (this goes on forever)

But as can be seen below there is no flash in /usr/lib/mozilla/plugins

drwxr-xr-x 2 root root 4.0K 2010-01-28 20:36 .
drwxr-xr-x 4 root root 4.0K 2008-10-30 00:02 ..
-rw-r--r-- 1 root root  79K 2009-02-09 16:42 gecko-mediaplayer-dvx.so
-rw-r--r-- 1 root root  79K 2009-02-09 16:42 gecko-mediaplayer-qt.so
-rw-r--r-- 1 root root  79K 2009-02-09 16:42 gecko-mediaplayer-rm.so
-rw-r--r-- 1 root root  79K 2009-02-09 16:42 gecko-mediaplayer.so
-rw-r--r-- 1 root root  79K 2009-02-09 16:42 gecko-mediaplayer-wmp.so
lrwxrwxrwx 1 root root   39 2009-05-31 17:26 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 root root   39 2009-08-16 22:58 nphelix.so -> /opt/real/RealPlayer/mozilla/nphelix.so
lrwxrwxrwx 1 root root   40 2009-08-16 22:58 nphelix.xpt -> /opt/real/RealPlayer/mozilla/nphelix.xpt

Why don't you try completely removing firefox and starting over from scratch?  If you want to save your web history and so forth just do the following:
```

mv .mozilla .mozilla.bak

# and when you are done reinstalling, move it right back:
mv .mozilla.bak .mozilla

```

---

### Post by wojox on 2010-01-28
> **Abekonge said:**
> I think I have the same problem - or at least the experience: Suddenly two or three days ago - everything is slow: minimizing and maximizing is slow - maybe 3 sec. lag - something which have been very fast up till then. Shifting between windows is also slow. I have changed nothing - only updated according to the usual updates. 

Flash works fine though.

Sounds like your video driver. What does:

```
lspci | grep VGA
```

produce? And does System > Administration > Hardware Drivers show an active driver?

---

### Post by DoubleDown on 2010-01-28
> **Abekonge said:**
> more details: my bookmarks-menu in firefox takes 3 seconds to load!! and switching between tabs is also markedly slower.
 
Isn't anyone else having similar experiences? It is very serious for me. My Ubuntu system just went from being blazingly fast to being slower than vista.
 
Actually sounds more like a potential trojan.  Be sure to change your administrative password to something complex.  Disable all remote access, and install anitvirus called clamav:
```

sudo apt-get install clamav

```

---

### Post by Abekonge on 2010-01-28
Installed clamav and I'm now running it - will report any results ...

somehow I do not think it is a trojan - it does very much feel like the video driver [but on the other hand: why would firefox bookmarks menu lag - it has no desktop effects - it just a simple menu ...?)

> abekonge@Skaerm:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M76 [Radeon Mobility HD 2600 Series]
Is the result... yes my hardware driver is active - I had serious lag problems when first instaling karmic koala (described here: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all) - but I fixed it using this : [https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill ]("https://edge.launchpad.net/%7Eubuntu-x-swat/+archive/xserver-no-backfill")

... could something have changed that reverted my old problems?

Thanks for the help, being a total newbie to ubuntu and to this forum - it is very cool that you are nice to me.

---

### Post by Abekonge on 2010-01-29
OK, it was the video driver all along ... so nothing related to what this thread was originally about - sorry about that. 

When I remove the prop. ATI driver everything is fine again (except of course no compiz). So the original fix must have stopped working ... oh well

---

### Post by screaminfakah on 2010-01-29
I have the same Radeon Mobility HD 2600 Series and I use the drivers Ubuntu lists under Hardware Drivers and they work fine. Can use compiz, ect. I have however tried to install drivers directly from ATI site and it borked my whole system,  had to start over.  

And to DoubleDown,  I heard those Linux viruses were pretty bad!

:P

Ha....  Yeah right!!

---

### Post by Abekonge on 2010-01-29
The original fix to the ATI video-lag stopped working - or was overwritten by a newer update of the x-server. It was fixed by this [https://launchpad.net/~k0ekk0ek/+archive/ppa ]("https://launchpad.net/%7Ek0ekk0ek/+archive/ppa")

So Halleluja - back to blazingly fast ubuntu.

---

### Post by no2498 on 2010-01-29
i had this for a week
its in usb 
it has to do with a bad unmount
hope this helps
had an update today
had something to do with mounting
i hope it was a fix for it

---

### Post by Jerriy on 2010-01-29
> **strAlan said:**
> Why don't you try completely removing firefox and starting over from scratch?Just done that... Went to synaptic - wiped my browser... but to no avail.

Online streaming videos like youtube are still not playing.

---

### Post by screaminfakah on 2010-01-29
You should try to purge the flash you have then

```
sudo apt-get install flashplugin-nonfree
```

To purge the original flash whether it be open source or Adobe has to be determined by you.  I think there is a code that can do both software types but dont know what it is.

Peace

---

### Post by MaindotC on 2010-01-29
> **screaminfakah said:**
> You should try to purge the flash you have then

```
sudo apt-get install flashplugin-nonfree
```

To purge the original flash whether it be open source or Adobe has to be determined by you.  I think there is a code that can do both software types but dont know what it is.

Peace

Please see post #26.

---

