---
title: "Kworld PVR-TV 300U USB TV-tuner"
date: 2006-04-29
forum: General Help
---

### Post by ewoox on 2006-04-29
Hi, i have a Kworld PVR-TV 300U USB tv-tuner and can't get it to work :confused: 

dmesg :
 usb 1-1: new full speed USB device using ohci_hcd and address 2 

I tried to use bttv but it doesn't seem to be working... 
 [4295859.745000] Linux video capture interface: v1.00
 [4295859.880000] bttv: driver version 0.9.16 loaded
 [4295859.881000] bttv: using 8 buffers with 2080k (520 pages) each for capture

I would like to know what drivers should I use???


any help would be great!

---

### Post by c-m on 2006-10-11
does anyone have the answer to this yet, or know what chopset it uses, as I want a cheap USB box for DVB-T

---

### Post by no_one on 2006-10-17
i just bought that usb tv tuner. ill do some work this week to try to get it working.

---

### Post by c-m on 2006-10-19
awesome, keep us posted with how you get on. I just bought one and I much prefer it to my compro dvb-t200. 

Once we get it working in linux it will be sweet for the price.

What chipset does this use?

---

### Post by DE Charmer on 2006-10-20
Could one of you email me the drivers for winxp? [email]eknight@hotmail.com[/email], my drver cd stopped working and i formatted my system, this dongle works soo good i got to get it back working. The manufacturer website has issues when i try to access the drivers for download.

Thanks for anyhelp provided

---

### Post by c-m on 2006-10-29
has anyone had any luck with this yet? What chipset does it use?

---

### Post by darkteckno on 2006-11-07
> **c-m said:**
> has anyone had any luck with this yet? What chipset does it use?


May be worth asking here: [http://tech.groups.yahoo.com/group/KWORLD-TV/](http://tech.groups.yahoo.com/group/KWORLD-TV/)

---

### Post by rarstar on 2007-01-02
hi, i've recently gotten this working under ubuntu 6.10

the driver is already included in the install, it just needs a firmware

download the firmware from here....
[http://thadathil.net:8000/dvb/fw/dvb-usb/dvb-usb-adstech-usb2-02.fw](http://thadathil.net:8000/dvb/fw/dvb-usb/dvb-usb-adstech-usb2-02.fw)

then copy into the /lib/firmware/your-kernal directory, eg...
> sudo cp dvb-usb-adstech-usb2-02.fw /lib/firmware/2.6.17-10-generic/

you can then use it with kaffeine

---

### Post by c-m on 2007-01-05
sounds good, though mine died some time ago. Now using a Starbox DVB-S in windows though.

---

### Post by OO7TDD on 2007-01-19
I'm new to Linux in general and I have my system up and running.  The link posted for the firmware was down so I found an RPM and got the firmware from that using alien.  I copied the file to the firmware directory.  I'm guessing theres more to do than that as I have no idea how to get it working.

I'm running Feisty(64bit) and the 2.6.20-5-generic kernel.  I installed and started up Kaffine, no DVB option was available.

Thank you for any help and/or guidance you guys can provide.  I appreciate it.

---

### Post by benshead on 2007-01-25
I am going to try this tonight to see if I can get anywhere. I noticed [this post from May of 2006]("http://ubuntuforums.org/showthread.php?t=182788"), which deals with a similar problem on a different USB DVB stick. 

The solution? "Recompiling the [USB unit]'s kernel modules using the latest Video4Linux/DVB-T source."

Looks worth a try, if it can be adapted for the 300u.

Rarstar, can you comment on any other things you did to make it work?

---

### Post by rarstar on 2007-03-28
hi, sorry i've not been on the site for a while

did anyone get anywhere with this?

it's a while back and as far as i can remember all i did was copy the firmware to the correct directory... /lib/firmware/2.6.17-10-generic/ (obviously, if you're using a kernel other than 2.6.17-generic, you'll use that directory

i remember reading another thread on here, maybe just general instructions for tv cards under ubuntu...i think you can use the command dmesg to see if you're card is recognised and it's drivers are installed (sorry, still a bit of a linux noob!)

anyway, i've just bought another of these cards and am going try and setup mythtv with them, so i'll post back in the next week or so, and let you know how i get on

cheers,
rar

---

### Post by rarstar on 2007-03-28
btw, the original link i posted seems to be dead now, but i think you can get it from the package on this page...
[http://rpm.pbone.net/index.php3/stat/4/idpl/3597773/com/dvb-firmware-usb-20061120-1plf2007.0.noarch.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/3597773/com/dvb-firmware-usb-20061120-1plf2007.0.noarch.rpm.html)

---

### Post by asmugone on 2007-04-20
OK gang, let me lay it out for you. Long story short, windows guru, tried linux mint, fell in love, have gone over the hill. back to noob status for me.

I have the kworld 300u usb stick. I have downloaded the firmware listed here, followed all relevant directions. installed v4l, couldnt find the usb stick so just compiled it flat.

Now according to what I have gathered here I should see the little light turn on as the firmware is loaded on restart with the stick plugged in, but alas, the kworld tasks me! KAHN!!!

on dmesg it spits out this.
[17179880.364000] usb 4-6: new high speed USB device using ehci_hcd and address 2
[17179880.500000] usb 4-6: configuration #1 chosen from 1 choice

lsusb spits out this
Bus 004 Device 002: ID eb1a:e300 eMPIA Technology, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

in device manager it lists the device as:
usb 2861 device
info.udi = /org/freedesktop/Hal/devices/usb_device_eb1a_e300_noserial
usb device vendor = eMPIA Technology inc.

im running linux mint upgraded to newest ubuntu distro. FIesty fawn
I have been battling with this usb stick for going on 3 months off and on!!
some one PLEASE smack me and explain to me where I am screwing up!

The humble *unix noob:
Smug

---

### Post by liljoe76 on 2007-05-14
bump bump

---

### Post by linuksman on 2007-05-21
where can I find the drivers for this card?  I see the firmware being linked in this thread.  I just installed feisty and i'm trying to get this working

---

### Post by norberto on 2007-06-04
Hi,
In order to build the drivers, follow next instructions
 
# go to admin console
sudo su

# install some stuffs for compilation
apt-get install mercurial linux-headers-$(uname -r) linux-source build-essential

# we can make next at /lib/firmware folder
cd /lib/firmware

# download the firmware
wget [http://konstantin.filtschew.de/v4l-firmware/firmware_v4.tgz](http://konstantin.filtschew.de/v4l-firmware/firmware_v4.tgz)

# decompress it on the folder
tar xvzf firmware_v4.tgz

# sync with the experimental v4l project
hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-experimental](http://mcentral.de/hg/~mrec/v4l-dvb-experimental)

# go to the new folder
cd v4l-dvb-experimental

# compile it ( see note )
make

# install it
make install

# and reboot it
reboot

# Tested on kernel 2.6.20 and xawtv, tvtime and mythtv

# NOTE: if your card is PAL-N (Argentina / Uruguay / Paraguay) before to make
# the compilation you must add the following lines under the PAL-M norm line ~765
# of ~/linux/drivers/media/video/em28xx/em28xx-cards (card .tvnorms array),
# and the card will work under PAL-N and PAL-Nc norms

# ~line 762 - For reference
    }, {
        .name = "PAL-M",
        .id = V4L2_STD_PAL_M,

# ~line 765 - Add this lines
    }, {
        .name = "PAL-N",
        .id = V4L2_STD_PAL_N,
    }, {
        .name = "PAL-NC",
        .id = V4L2_STD_PAL_Nc,
# end

Install TvTime from Add Applications or Synaptic

Enjoy KWorld PVRTV 300U

---

### Post by liljoe76 on 2007-06-05
norberto, you complete me.
ahhahahahha
thank you SOOOOOOOOO MUCH. this must go in the wiki!

---

### Post by linuksman on 2007-06-06
I did essentially what you are describing Norberto, but I get video but no sound..

I will go over in detail and see if I missed something, thanks

---

### Post by liljoe76 on 2007-06-07
yea, i get no sound as well :( i'll post back if i get anywhere...

---

### Post by norberto on 2007-06-07
Hi guys, sorry but I'm very busy at this days.

For your sound problems make this command

cat /proc/asound/cards

This generated list enumerate by number your sound cards (one or many) including 2861 device of the kworld card

Take note about each card number and make the following command

sox -p -q -s -w -c 2 -r 48000 -t ossdsp /dev/dsp2 -t ossdsp /dev/dsp1 & tvtime && killall sox

Take note on this case that the first /dev/dsp2 device is the kworld capture sound card and the second /dev/dsp1 device is the play sound card where to redirect the sound.

The command make the sound redirection, launch tvtime (or any tv app) and when the tv application ends the sox process is killed.

Some times you must unplug/plug before to make the command, because a bug that I'm investigating.

Enjoy

---

### Post by liljoe76 on 2007-06-07
a huge thanks for your support thus far, this is the last hardware stumbling block i have in my transition.
 cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xc0000000 irq 22

the sox command shows; 
sox: Can't open input file '/dev/dsp2': No such file or directory
as an aside, i pooked around in /dev/ and i only have dsp (300U enabled/disabled) 
using clues from your post i found this thread
[http://www.mail-archive.com/em28xx@mcentral.de/msg00027.html](http://www.mail-archive.com/em28xx@mcentral.de/msg00027.html)
i tried many of the commands to find out more info.. but i'm not getting much further. i am thinking a clean install is called for in the next few days. anymore insight is appreciated.
thanks, 
joe

---

### Post by zlochko on 2007-06-08
Hallo, 
I am also trying to get this card working, but unfortunately without any success at all. :(
I've downloaded the firmware mentioned on page 1... then I've done the recompiling from page 2... installed the tvtime software... but I'll I get is a blue screen telling me:
No such file or directory
Cannot open capture device /dev/video0

I would really appreciate any helpful suggestions.
Thank you!

---

### Post by zlochko on 2007-06-08
Ok... In regards to my previous message I've put the screen output to files for:
lsusb
make
make install
and dmesg

I am doing the following procedure. Downloading the firmware v4.
extracting the files to /lib/firmware/
doing 'hg clone' by which a new directory is created called  ./v4l-dvb-experimental/
then make
then make install
then reboot
then modprobe em28xx
and then I start TVTime which gives me the message 'Cannon open capture device /dev/video0'

...please help since I am loosing my sanity with this. Thank you!

---

### Post by norberto on 2007-06-08
> **liljoe76 said:**
> a huge thanks for your support thus far, this is the last hardware stumbling block i have in my transition.
 cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xc0000000 irq 22

the sox command shows; 
sox: Can't open input file '/dev/dsp2': No such file or directory
as an aside, i pooked around in /dev/ and i only have dsp (300U enabled/disabled) 
using clues from your post i found this thread
[http://www.mail-archive.com/em28xx@mcentral.de/msg00027.html](http://www.mail-archive.com/em28xx@mcentral.de/msg00027.html)
i tried many of the commands to find out more info.. but i'm not getting much further. i am thinking a clean install is called for in the next few days. anymore insight is appreciated.
thanks, 
joe

please try:

sudo modprobe em28xx-audio

---

### Post by norberto on 2007-06-08
> **zlochko said:**
> Ok... In regards to my previous message I've put the screen output to files for:

then modprobe em28xx
and then I start TVTime which gives me the message 'Cannon open capture device /dev/video0'

...please help since I am loosing my sanity with this. Thank you!

please post lsmod file, because looks as you ar loading bttv modules and they are making some trouble.

norberto

---

### Post by liljoe76 on 2007-06-08
closer, warmer....
 cat /proc/asound/cards 
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xc0000000 irq 22
 1 [Em28xx Audio   ]: Empia Em28xx AudEm28xx Audio - Em28xx Audio
                      Empia Em28xx Audio
but
 sox -p -q -s -w -c 2 -r 48000 -t ossdsp /dev/dsp2 -t ossdsp /dev/dsp1 & tvtime && killall sox
[1] 6680
sox: Can't open input file '/dev/dsp2': No such file or directory
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/joe/.tvtime/tvtime.xml
Thank you for using tvtime.
[1]+  Exit 2                  sox -p -q -s -w -c 2 -r 48000 -t ossdsp /dev/dsp2 -t ossdsp /dev/dsp1
sox: no process killed
again i peeked in /dev/ and no other dsp's are there (300U enabled or disabled), if that means anything. i'll start fresh tomorrow, i hate to have someone help troubleshoot an 'unclean' machine. 
thanks again, 
joe

---

### Post by zlochko on 2007-06-11
> **norberto said:**
> please post lsmod file, because looks as you ar loading bttv modules and they are making some trouble.


Hallo norbero... and THANKS for your help.
You were right. I did load bttv drivers previously. I think that I found somewhere on the web that they are needed. Now, I have removed them from the modules script and recompile the package again. And I still get that darn blue screen in TvTime telling me that it can't find capture device /dev/video0

Following this message I'm also sending output of mod install, lsusb & lsmod. Hope it will give you a clue... 
I haven't mentioned this in my previous post, but I have an ATI card. Gnome is currently loaded with XGL (btw, Beryl rulez!) and I'm using the ATI restricted drivers. I don't know if this matters...

Thanks again,
Gjoko.

---

### Post by zlochko on 2007-06-11
> **liljoe76 said:**
> 
i tried many of the commands to find out more info.. but i'm not getting much further. i am thinking a clean install is called for in the next few days. anymore insight is appreciated.
thanks, 
joe

Hey liljoe, try the following link
[http://www.mail-archive.com/em28xx@mcentral.de/msg00037.ht]("http://www.mail-archive.com/em28xx@mcentral.de/msg00037.html")ml
...I beleave it might have a solution for your problem.

Regards,
Gjoko.

---

### Post by linuksman on 2007-06-14
> **liljoe76 said:**
> closer, warmer....
 cat /proc/asound/cards 
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xc0000000 irq 22
 1 [Em28xx Audio   ]: Empia Em28xx AudEm28xx Audio - Em28xx Audio
                      Empia Em28xx Audio
but
 sox -p -q -s -w -c 2 -r 48000 -t ossdsp /dev/dsp2 -t ossdsp /dev/dsp1 & tvtime && killall sox
[1] 6680
sox: Can't open input file '/dev/dsp2': No such file or directory
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/joe/.tvtime/tvtime.xml
Thank you for using tvtime.
[1]+  Exit 2                  sox -p -q -s -w -c 2 -r 48000 -t ossdsp /dev/dsp2 -t ossdsp /dev/dsp1
sox: no process killed
again i peeked in /dev/ and no other dsp's are there (300U enabled or disabled), if that means anything. i'll start fresh tomorrow, i hate to have someone help troubleshoot an 'unclean' machine. 
thanks again, 
joe

you're not alone =P, I'll let you know if I get mine working somehow...

---

### Post by Nikron on 2007-07-04
Alright guys!  
```


Device driver usbdev3.5_ep81 lacks bus and class support for being resumed.
Device driver usbdev3.5_ep82 lacks bus and class support for being resumed.
Device driver usbdev3.5_ep84 lacks bus and class support for being resumed.
em28xx #0: V4L2 device registered as /dev/video0
em28xx #0: Found KWorld PVRTV 300U[01:55:47][nikron@garblax ~]$
[01:56:13][nikron@garblax ~]$
[01:56:33][nikron@garblax ~]$
Device driver usbdev3.5_ep81 lacks bus and class support for being resumed.
Device driver usbdev3.5_ep82 lacks bus and class support for being resumed.

```

So, now I'm firmly stuck were you are...   no audio..

---

### Post by nowave7 on 2007-07-04
Hi everybody! I'm having the same problem as zlochko here, that is, I've done everything according to the instructions, but there is no /dev/video0 device, and the card is not working. The attached file contains various outputs, such as dmesg, lsusb, lsmod,... Any help is greatly appreciated!

---

### Post by liljoe76 on 2007-07-26
any new developments? anyone have any luck getting sound?

---

### Post by nowave7 on 2007-08-08
I've managed to get the video, but there is still no sound. I'm not sure whether it is a hardware or a software issue, since I have a laptop, that is based on sis chipset, and that's not a good thing :(

---

### Post by zlochko on 2007-08-08
> **nowave7 said:**
> I've managed to get the video, but there is still no sound. I'm not sure whether it is a hardware or a software issue, since I have a laptop, that is based on sis chipset, and that's not a good thing :(

Hallo nowave7. Since you've get the video to work, could you please post the procedure here. I am still having trouble to get it work... 

Thank you,
Zlochko.

---

### Post by nowave7 on 2007-08-08
Hi zlochko. I took a look at your lsusb, and I know why you have no video.
The experimental driver (found on the mcentral site) supports Kworld pvr-tv 300u with device ID e300, while yours and mine is e301, and is not recognized by the driver. The solution is to modify the driver, that is, to just copy/paste the existing parts for the e300 and then replace e300 with e301. You don't have to do this, since I've added my modified driver in the attached file. You need to copy the em28xx directory to where the original em28xx directory in the v4l source directory is situated. Then you just make && make install the v4l driver, and you should have video output.
As for the sound, I have no idea. I've tried the sox command, and it is not working for me. I've been trying for almost a month now to set the sound, but I'm not getting anywhere.
Hope this'll get your video working, at least.
Cheers!

---

### Post by nowave7 on 2007-10-15
Anyone had any luck with the sound on the e301 card?

---

### Post by alasombra on 2008-01-31
Sound works!!!!
Use command:
play -q -s -w -c 2 -r 48000 -t ossdsp /dev/dsp1  & tvtime && killall sox

---

### Post by nowave7 on 2008-02-04
Will try that today asap!!! :) Hope it works!!!

---

### Post by nowave7 on 2008-02-19
I'm afraid it is still not working. I'm starting to believe that this is a hardware issue.

---

### Post by fek on 2008-02-22
nowave7 I've same problem as you...

I also have a e301. And I can't get any sound aswell...

Hope some one will found a solution! :)

---

### Post by jdbausch on 2008-05-31
I hate to dig up an old thread - I hope someone in the know is watching...

I have a Kworld PVR-TV 300U (reporting in lsusb as: ID eb1a:e300 eMPIA Technology, Inc.)

I am running hardy.


I'm unclear on the firmware procedures listed in this thread.

Are norberto's posted steps the correct and current way to install?... What is the definitive procedure for getting this device running on Hardy?  Can anyone provide a step-by-step if the listed procedure is not correct?

(also many of the firmware links listed in this thread appear to be dead - where should one be getting the correct firmware now-a-days?)


thanks...

---

### Post by jdbausch on 2008-05-31
OK I ran through the process described by norberto, and it worked fine.

except now join the ranks of the many who have no audio.

I've tired the various sox related suggestions here with no luck.  I will experiment more and post results.

---

### Post by jdbausch on 2008-05-31
after some digging, I found the following links:

[http://www.mail-archive.com/em28xx@mcentral.de/msg01005.html](http://www.mail-archive.com/em28xx@mcentral.de/msg01005.html)

[http://www.mail-archive.com/em28xx@mcentral.de/msg01036.html](http://www.mail-archive.com/em28xx@mcentral.de/msg01036.html)

[http://mcentral.de/pipermail/em28xx/2007-June/000482.html](http://mcentral.de/pipermail/em28xx/2007-June/000482.html)

(these look to be archived emails between the EM2880 project lead, and a PVR 300U user, discussing audio issues)

[http://mcentral.de/wiki/index.php5/Em2880/Todo](http://mcentral.de/wiki/index.php5/Em2880/Todo)
(this is the EM2880 todo list)


The upshot (appears to be) that audio on the kworld PVR-TV 300U with the EM2880 is NOT reliably working.  even the experimental firmware does not get this working.  I'll be honest, I'm not really following everything in these archived mails.  But it  would appear that folks that do have it working have some other USB audio device that causes this to work?

I very well could be reading these mails incorrectly.  

And there also may be enough info in these various links to figure out a way to get it working.  but that would take someone smarter (and having more time) than me.

I will check back, though.  on the last link, you can see that as of March '08 audio support for the Kworld pvr-TV 300u is on the todo list.



But if someone finds a reliable workaround, could you please post?

---

### Post by nowave7 on 2008-06-10
Hello jdbausch,

I find it a bit strange that you don't have sound working on your card, since yours is eb1a:e300. The ones that are not working, as far as I can see, are eb1a:e301. Maybe you've missed something, or maybe you've got the wrong firmware?

---

### Post by jdbausch on 2008-06-10
> **nowave7 said:**
> Hello jdbausch,

I find it a bit strange that you don't have sound working on your card, since yours is eb1a:e300. The ones that are not working, as far as I can see, are eb1a:e301. Maybe you've missed something, or maybe you've got the wrong firmware?

Since I went through this a week ago I had actually sort of written it off... I got that tuner for like $10 so no big loss!

I think I followed the procedure correctly, but I'm not 100% sure on that now - the memory is not as good as it used to be, and I'm at work now.

But I certainly only get images and no sound, that much is for sure.

I have windows machines at my disposal, so I will load the tuner up on one of those to make sure it is not a hardware issue on my end (if I can find windows drivers!)

Can you tell me where should I go to make sure I've got the correct firmware?

---

### Post by nowave7 on 2008-06-13
For all empia based device you should definitely check [HTML]www.mcentral.de[/HTML]. There you should be able to find everything you  need to get this card working. It is possible, however, that you have some new revision, and that sound is just not yet implemented correctly for it. Anyway, the sound problem should be addressed soon enough, according to the em28xx driver mailing list .

---

### Post by krbrownz on 2008-06-17
hello, I have a "AC97 audio codec"  I can't seem to get my sound working
I was wondering if I can redirect my audio out my TV card? the sound on it works.
thank you for any help....

---

### Post by roykoe on 2008-07-18
Dear All,
I am Newbie using Hardy.

Can anyone guide me how to use this TV tuner works. 

I, have not sure what i am doing.

Thanks

---

### Post by jfernandez on 2008-07-22
> **nowave7 said:**
> Hi zlochko. I took a look at your lsusb, and I know why you have no video.
The experimental driver (found on the mcentral site) supports Kworld pvr-tv 300u with device ID e300, while yours and mine is e301, and is not recognized by the driver. The solution is to modify the driver, that is, to just copy/paste the existing parts for the e300 and then replace e300 with e301. You don't have to do this, since I've added my modified driver in the attached file. You need to copy the em28xx directory to where the original em28xx directory in the v4l source directory is situated. Then you just make && make install the v4l driver, and you should have video output.
As for the sound, I have no idea. I've tried the sox command, and it is not working for me. I've been trying for almost a month now to set the sound, but I'm not getting anywhere.
Hope this'll get your video working, at least.
Cheers!

hi nowave7

i am too sad becouse my kworld doesn't work. it's a 303u and i believe that there aren't drivers for it. please help me! (excuse me but i dont speak english but i'm trying to be clear as possible)

---

### Post by zlochko on 2008-07-24
Some more troubles with this driver... After upgrading the kernel through the System Update software in ubuntu (8.04 btw) to versions 2.6.24-19-generic and 2.6.24-20-generic I found out that I had to redo the whole procedure of rebuilding the kernel.
Unfortunately, make informs me of the following errors:
‘MOD_INC_DEC_COUNT’ undeclared (first use in this function)
‘MOD_INC_USE_COUNT’ undeclared (first use in this function)

So... since I am a complete idiot in C and kernel programming, I simply edit the em28xx/em28xx-i2c.c file... comment out everything that uses those constants and simply re-make everything. So far so good... the tvtuner is working... 
...now lets brag about it to my linux friends over Skype... oh... ups... Skype won't connect any more... no no... it won't even turn off... skype gets zombificated... kill -9 won't work eather... :lolflag:

Hm... downgrade the kernel (2.6.24-18-generic)... skype works... kworld won't... re build again  by repeating the above procedure... kworld works... skype ain't working.
Argh...

---

