---
title: "Major issues - wrong processor &amp; overheating"
date: 2010-09-12
forum: General Help
---

### Post by rwonder on 2010-09-12
Hello Everyone!
I NEED HELP!!!

Okay so here's what is happening...
So i wanted to download the latest version of (Ubuntu 10.04), but it keeps trying to download the amd version.  My computer is knows it has an intel, but the site keeps on trying to download the amd version (clarification the 64 bit). I cleared my browser cache, and same issue. I ended up getting the intel version manually, but i think this issue ties into my other issues.

Okay so i finally installed it on my usb key using the "Universal USB Installer" software. Great, so i load up and try and download chrome. But it downloads the amd version, so it can't install. I try updating my video card drivers, and...you guessed it it downloads the amd version.


okay so that is major problem 1...which i believe ties into problem 2.

WHILE I'M NOT DOING ANYTHING ON MY LAPTOP THE PROCESSOR IS GOING CRAZY!!!! I have the Intel Core 2 Duo P8600, my second processor is running at 100% while my first processor is running at 4%.  My fan is going crazy, and this thing is getting crazy hot.  I mean i can run Star Craft II on my laptop using Windows 7 and it doesn't even get that hot.

if you need any additional info, reports, images, please let me know...

Thanks everyone

---

### Post by Alver on 2010-09-12
> **rwonder said:**
> Hello Everyone!
I NEED HELP!!!

Okay so here's what is happening...
So i wanted to download the latest version of (Ubuntu 10.04), but it keeps trying to download the amd version.  My computer is knows it has an intel, but the site keeps on trying to download the amd version (clarification the 64 bit). I cleared my browser cache, and same issue. I ended up getting the intel version manually, but i think this issue ties into my other issues.

Okay so i finally installed it on my usb key using the "Universal USB Installer" software. Great, so i load up and try and download chrome. But it downloads the amd version, so it can't install. I try updating my video card drivers, and...you guessed it it downloads the amd version.


okay so that is major problem 1...which i believe ties into problem 2.

WHILE I'M NOT DOING ANYTHING ON MY LAPTOP THE PROCESSOR IS GOING CRAZY!!!! I have the Intel Core 2 Duo P8600, my second processor is running at 100% while my first processor is running at 4%.  My fan is going crazy, and this thing is getting crazy hot.  I mean i can run Star Craft II on my laptop using Windows 7 and it doesn't even get that hot.

if you need any additional info, reports, images, please let me know...

Thanks everyone
If your computer has a 64 bits architecture amd64 is fine. This version functions well on Intel based machines. For what  it is worth I have a Toshiba L505-10M 64 bits Intel based  and it runs happily (or almost) after using the amd64 installation files to install a dual boot U 10.04/W7. Hope this helps.

Alver

---

### Post by Lateralis on 2010-09-12
I have an Intel Core2Duo and have the AMD64 version.  It works fine.  =) 

As for why you're processor is going crazy, you can see which processes are running in the System Monitor: System -> Administration -> System Monitor.  You can sort the list of processes by %CPU to findout what is going mad.  Or you can use the command line: type "top" to see a list of processes currently running, ordered automagically by CPU %age.

---

### Post by rwonder on 2010-09-12
**REPLY TO Alver:**
First of thanks for the replies...

Hmmm...Is that my only solution, to install the amd version? And if so, why doesn't the intel version work, this doesn't make sense.  This is a beta, so if this needs to be fixed i'm more than willing to try and explain more on the issue.

Also, if i do install the amd version how do i install flash?
No matter what i tried i couldn't install flash when i had the amd version.

And finally, why was my processor going nuts? I wanna use ubuntu, but if it's gonna max out my processor while i do nothing it's going to kill my pc's life time.

---

### Post by rwonder on 2010-09-12
> **Lateralis said:**
> I have an Intel Core2Duo and have the AMD64 version.  It works fine.  =) 

As for why you're processor is going crazy, you can see which processes are running in the System Monitor: System -> Administration -> System Monitor.  You can sort the list of processes by %CPU to findout what is going mad.  Or you can use the command line: type "top" to see a list of processes currently running, ordered automagically by CPU %age.


That is what i did do...my second processor was jumping between 94% and 100%, while processor 1 was at 4% to 10%...all i had open was firefox and gmail within that...and this wasn't a spike...it stayed like this for a while...then my computer got ridiculously hot

---

### Post by Lateralis on 2010-09-12
OK, you said that.  My post was implicitly asking for details of some description of the running processes.  

Open up the System Monitor, click the Processes tab and order the %CPU column descending, so the most CPU intensive processes are at the top.  What processes do you see near the top?  

As for flash, it isn't installed by default.  I think you need to get the ubuntu-restricted-extras package.

---

### Post by jmszr on 2010-09-12
rwonder,

This will help explain the AMD64 question: [http://blog.mypapit.net/2007/08/debian-amd64-is-not-limited-to-amd-machines-only.html](http://blog.mypapit.net/2007/08/debian-amd64-is-not-limited-to-amd-machines-only.html) . (Note:Ubuntu is a fork of Debian[in case you didn't already know].)

+1 for runnning "top" in the terminal. Alternately, you could install "Htop" (a GUI for top) so we can see what process(es) are causing you grief.

For flash I would recommend this Firefox addon: [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/) ,it's called FLASH-AID and it works very well.

There has been a problem with 64-bit flash as Adobe is temporarily not supporting it for Linux. This addon will install the 32-bit flash in a wrapper. Hopefully, Adobe will be forthcoming with the proper version.

---

### Post by rwonder on 2010-09-12
okay so i'm posting this while running ubuntu of my usb...

So here are images of what is happening

[ATTACH]169287[/ATTACH]

[ATTACH]169288[/ATTACH]

Both were running at 100% for about 3 or 4 minutes...then they calmed down
Right now the processors have calmed down to 20% a piece...

So i'm not sure what is causing the processors to jump to 100%

i'm off to go read that jmszr sent me...

---

### Post by Lateralis on 2010-09-12
OK, can you open up a terminal (Applications -> Accessories -> Terminal) and type in the following: 

```

top | head

```

and post the output of that into a new post please?

---

### Post by rwonder on 2010-09-12
top - 20:47:29 up 20 min,  8 users,  load average: 0.70, 0.57, 0.49
Tasks: 175 total,   1 running, 174 sleeping,   0 stopped,   0 zombie
Cpu(s): 13.7%us,  4.9%sy,  0.0%ni, 79.9%id,  0.9%wa,  0.2%hi,  0.4%si,  0.0%st
Mem:   3611288k total,  1187664k used,  2423624k free,   141520k buffers
Swap:        0k total,        0k used,        0k free,   740004k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4639 ubuntu    20   0 51948  19m  15m S   14  0.6   2:04.59 gnome-system-mo    
 3281 root      20   0 38132  20m 9352 S    8  0.6   1:49.37 Xorg               
 4650 ubuntu    20   0  339m  94m  28m S    2  2.7   0:56.44 firefox-bin 

again...it is pretty calm right now...should i wait for it to go up and then do this again?

---

### Post by rwonder on 2010-09-12
[ATTACH]169296[/ATTACH]

In case it was hard to make out what i copy and pasted

---

### Post by Lateralis on 2010-09-12
Yes.  It does look pretty sane at the minute.  If it starts to go crazy again, use that command.  If there is a process (or three) which is hogging the CPU it will stand out like a sore thumb.  If nothing obvious appears, then I'll be stumped.

Also, just for your info... That command I asked you to use invokes two different programmes.  The first one, **top** lists system processes.  If you type that in by itself you'll see a long list of things.  (To get out of "top" just hit 'q'.)  **head** is a programme which reads in data and reproduces to the terminal just the first 10 lines of the data.  (A corresponding programme **tail** reproduces the final 10 lines of the data.)  The upright symbol between the two is the "pipe" symbol.  What it does is "pipe" the output of **top** into **head**, so all you see in the terminal is the first 10 lines of the output from **top**.  This is all we need, as it shows the three most CPU intensive processes.  Hopefully, when the CPU is getting abused we'll be able to work out why it is.

---

### Post by rwonder on 2010-09-12
k i was able to reproduce the problem where it jumps to 100%
Every time i try and install my video card driver...it fails every time...

Sorry for that guys...
I made some print screens and top | head...in case you need info

I'm going to go and change my os to the amd64 version...Do you guys mind walking me through how to install flash please...
I went to their website, the ubuntu software center, and tried just installing strait out of firefox when it suggests to install it...and it never works.

---

### Post by Lateralis on 2010-09-12
What graphics card do you have?  How were you trying to install the graphics card?  Through System -> Administration -> Hardware drivers?  

According to the link on the website, you will need to first of all remove all flash plugins that you may have installed already.  Then install that Firefox addon.  You will need to restart Firefox for the changes to take effect.  

The addon though is of most interest to 64-bit users.  This is for the reason described by jmszr: Adobe don't currently support 64-bit flash for Ubuntu/Linux.  Which sucks and furthers my belief that Adobe are pants. :P  If you run 32-bit Ubuntu then the packages in the Ubuntu repositories should work fine.  To install them, open up a terminal and type:

```

sudo aptitude install ubuntu-restricted-extras

```

That (I think) installs the flashplugin for you, in addition to MP3 playback support, Java and a few other goodies.


+1 to jmszr for the Ubuntu add-on link too

---

### Post by arashiko28 on 2010-09-12
When you finish the installation, just download the 32 bit version of flash and then run this on terminal:
> sudo dpkg -i --force-architecture name-of-program

and you will install the 32 bit version of the software, but will never remember that :p

---

### Post by jmszr on 2010-09-12
rwonder,

If you do wish to use the 64-bit version (and I do) then the FLASH-AID addon will: "Remove conflicting flash plugins from Ubuntu Linux systems and install the appropriate version according to system architecture." It will for the 32-bit also, come to think of it. So you don't need to uninstall anything unless you want the practice.

@ Lateralis: The wording on the addon's website could be clearer.

---

### Post by rwonder on 2010-09-12
ATI Mobility Radeon HD 4300 Series

Yes through System -> Administration -> Hardware drivers and also through a lil icon at the top on that taskbar (i forget what linux calls it)

I couldn't install the firefox addon...so i tried doing it through ubuntu and that didn't work either.

Wait i'm confused...So do i have to install a 32 bit ubuntu in order to get flash or do i keep my 64 bit, and install ubuntu-restricted-extras and then download the 32 bit version of flash?

---

### Post by rwonder on 2010-09-12
> **jmszr said:**
> rwonder,

If you do wish to use the 64-bit version (and I do) then the FLASH-AID addon will: "Remove conflicting flash plugins from Ubuntu Linux systems and install the appropriate version according to system architecture." I guess it will for the 32-bit also, come to think of it. So you don't need to uninstall anything unless you want the practice.

I'm just installing the amd version of ubuntu and then i'll give it a shot

---

### Post by jmszr on 2010-09-12
rwonder,

When you install that addon it will put a little reddish icon down at the right on the status bar. Click on that icon and then click on "install" on the small menu that comes up and then sit back and watch. That should do it.

---

### Post by rwonder on 2010-09-12
> **jmszr said:**
> rwonder,

When you install that addon it will put a little reddish icon down at the right on the status bar. Click on that icon and then click on "install" on the small menu that comes up and then sit back and watch. That should do it.


Nope it didn't work.

---

### Post by rwonder on 2010-09-12
okay please help me!!!!

I don't understand...when i was running the i386 ubuntu version, adobe would download the amd version...now that i've installed the amd ubuntu version, adobe downloaded the i386 version!!!!

AHHHHHHHHHHHHHHHHHHHHH.....


> **Lateralis said:**
> What graphics card do you have?  How were you trying to install the graphics card?  Through System -> Administration -> Hardware drivers?  

According to the link on the website, you will need to first of all remove all flash plugins that you may have installed already.  Then install that Firefox addon.  You will need to restart Firefox for the changes to take effect.  

The addon though is of most interest to 64-bit users.  This is for the reason described by jmszr: Adobe don't currently support 64-bit flash for Ubuntu/Linux.  Which sucks and furthers my belief that Adobe are pants. :P  If you run 32-bit Ubuntu then the packages in the Ubuntu repositories should work fine.  To install them, open up a terminal and type:

```

sudo aptitude install ubuntu-restricted-extras

```

That (I think) installs the flashplugin for you, in addition to MP3 playback support, Java and a few other goodies.


+1 to jmszr for the Ubuntu add-on link too

---

### Post by jmszr on 2010-09-12
rwonder,

Have you tried the command in arishiko's post #15, yet?

---

### Post by rwonder on 2010-09-12
> **jmszr said:**
> rwonder,

Have you tried the command in arishiko's post #15, yet?

No i don't know what to put for the name of the program...

I also tried this tutorial: [http://www.youtube.com/watch?v=wHFtqy1mD24](http://www.youtube.com/watch?v=wHFtqy1mD24)
but command:sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
won't work

I tried to find out why and it's because i don't have the nspluginwrapper
I tried to find out why and it's because i don't have the mulitverse enabled
I tried to figure out how to enable it and i can't

thanks for the help

---

### Post by jmszr on 2010-09-12
rwonder,

To enable the multiverse repository: System > Administration > Software Sources > Ubuntu Software > and make sure all four (main, universe, restricted, multiverse) are checkmarked.

You will then need to run:

```
sudo apt-get update && apt-get upgrade
```

The method you are using is better, I think, than post #15's.

---

