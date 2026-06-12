---
title: "can't install realtek ac'97 driver"
date: 2011-11-13
forum: General Help
---

### Post by MissBaksel on 2011-11-13
[SIZE=2]Hello,

I just installed ubuntu 11.10 on my pc and I wanted to install all the drivers.
I managed to install my nvidia driver, this was really easy because I could find it in the softwarecentre but I couldn't find my audio driver over here. I searched on the web why this is and it seemed that my audio card wasn't ALSA supported (or something like that). My audio card is : realtek ac'97

I also read a thread on this forum but because this was posted in 2005 I will reply in a new thread 
(sum forums don't like if you reply on old threads)

In the thread you could read this:[/SIZE]
[SIZE=1]                                  [/SIZE][SIZE=1]**Howto: Driver installation for Asrock motherboad integrated realtek AC'97 soundcard**             [/SIZE]
                                                                [SIZE=1]Hello. I explain  here how to install a driver for realtek AC'97 soundcard, since Ubuntu  has some problems recognizing this sound card when it is integrated in  the motherboard Asrock K8 upgrade 760GX. First of all, you have to  download the driver from 
[http://www.realtek.com.tw/downloads/...8Unix%20(Linux]("http://www.realtek.com.tw/downloads/dlac97-2.aspx?lineid=5&famid=12&series=8&Software=True#8Unix%20%28Linux") [/SIZE][SIZE=1])

Once you have downloaded the linux_r32.zip file, you have to unzip it.  One of the unzipped files is azx.tar.bz2 . Unzip this file too, and you  will get a directory called alsa-driver-1.0.9rc4a. [/SIZE]     [SIZE=1]

Before compiling and installing, you will probable to get some  applications with Synaptic. Open Synaptic and search for "gcc" ,  "linux-source" and "linux-headers" and install them.  Don't forget to  update Ubuntu before doing this. Once you have this packages installed,  you can go on: open a root terminal and write the following commands.  After rebooting Ubuntu, your integrated ac'97 soundcard will be working.  [/SIZE] [SIZE=1]

 ./configure [/SIZE][SIZE=1]

 make [/SIZE][SIZE=1]

 make install [/SIZE][SIZE=1]

 ./snddevices [/SIZE]
                                                                                         [SIZE=1]         [/SIZE][SIZE=1]                                                
[SIZE=2]
I tried to do all of this but I still had some problems. 
If I type ./configure in my terminal it says that it couldn't find the file.
I also don't know where to unzip the driver file. Is this important?

You can find the whole thread over here: [http://ubuntuforums.org/showthread.php?t=51123](http://ubuntuforums.org/showthread.php?t=51123)

This is my first time I installed ubuntu so I'm a total noob in this os. ](*,):)
Thanks
 
[/SIZE][/SIZE]                                                                 [SIZE=2]
[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=267298")[/SIZE]

---

### Post by Cyclane on 2011-11-13
I'm sorry to bypass your direct question but because this is your first time installing Ubuntu, could you post the output of:
```
lspci | grep Audio
sudo lshw -c multimedia
```

This will tell us what audio device you have exactly.

And by the way, on linux it's not a good idea to follow dated posts. They can be guidelines but most of the time they're outdated.

---

### Post by MissBaksel on 2011-11-14
[SIZE=2]This was the result:[/SIZE]

john@john-desktop:~$ lspci | grep Audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
02:0b.0 Multimedia audio controller: Ensoniq 5880B [AudioPCI] (rev 02)
john@john-desktop:~$ sudo lshw -c multimedia
[sudo] password for john: 
  *-multimedia            
       description: Multimedia audio controller
       product: 5880B [AudioPCI]
       vendor: Ensoniq
       physical id: b
       bus info: pci@0000:02:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ENS1371 latency=64 maxlatency=128 mingnt=12
       resources: irq:23 ioport:df00(size=64)
  *-multimedia
       description: Multimedia audio controller
       product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0
       resources: irq:17 ioport:e800(size=256) ioport:ee80(size=64) memory:f7fff800-f7fff9ff memory:f7fff400-f7fff4ff
john@john-desktop:~$ 

[SIZE=2]Thanks[/SIZE]

---

### Post by Cyclane on 2011-11-14
Ok I believe you have 2 audio output devices. 1 Is probably in your motherboard an the other one is a separate PCI card.

I believe that the realtek device should work out of the box, so why isn't it working for you?

Would you post the output of:```
aplay -L
``` This time please post the output between CODE brackets, using the '#' button.

---

### Post by 3rdalbum on 2011-11-14
Ubuntu already has this driver built-in, since about 2005 :-)

The previous poster cleverly got the information that you have two output chips in your computer, and I imagine the wrong one is currently being used.

If you go to the little speaker icon on your top panel and come down to Sound Settings, you'll see a window that contains a "Hardware" tab and an "Output" tab. These should list both sound cards and allow you to switch between them. In the "Profile" popup menu on the Hardware tab, Analogue Stereo Duplex should be the correct setting.

And in the Output tab, make sure the correct connector is selected.

Use the "Test Speakers" function to see if your changes are correct.

---

### Post by MissBaksel on 2011-11-14
[SIZE=2]Yeah, thanks a lot. 

The wrong sound card was selected in my settings.
Now I can hear everything with a high quality.

The result in my terminal was this, just in case sum other people are interested:[/SIZE]
    
```
john@john-desktop:~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    Front speakers
rear:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC1
    Rear speakers
surround40:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    4.0 Surround output to Front and Rear speakers
iec958:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    Direct sample mixing device
dmix:CARD=AudioPCI,DEV=1
    Ensoniq AudioPCI, ES1371 DAC1
    Direct sample mixing device
dsnoop:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    Direct sample snooping device
dsnoop:CARD=AudioPCI,DEV=1
    Ensoniq AudioPCI, ES1371 DAC1
    Direct sample snooping device
hw:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    Direct hardware device without any conversions
hw:CARD=AudioPCI,DEV=1
    Ensoniq AudioPCI, ES1371 DAC1
    Direct hardware device without any conversions
plughw:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    Hardware device with all software conversions
plughw:CARD=AudioPCI,DEV=1
    Ensoniq AudioPCI, ES1371 DAC1
    Hardware device with all software conversions
front:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    Front speakers
surround40:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    4.0 Surround output to Front and Rear speakers
surround41:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5 - IEC958
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    Direct sample mixing device
dmix:CARD=ICH5,DEV=4
    Intel ICH5, Intel ICH5 - IEC958
    Direct sample mixing device
dsnoop:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    Direct sample snooping device
dsnoop:CARD=ICH5,DEV=4
    Intel ICH5, Intel ICH5 - IEC958
    Direct sample snooping device
hw:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    Direct hardware device without any conversions
hw:CARD=ICH5,DEV=4
    Intel ICH5, Intel ICH5 - IEC958
    Direct hardware device without any conversions
plughw:CARD=ICH5,DEV=0
    Intel ICH5, Intel ICH5
    Hardware device with all software conversions
plughw:CARD=ICH5,DEV=4
    Intel ICH5, Intel ICH5 - IEC958
    Hardware device with all software conversions
john@john-desktop:~$
```[SIZE=2]Thank you too, cyclane[/SIZE]

---

### Post by Cyclane on 2011-11-14
Hehe I was gently trying to make the same point, have fun with your audio. :)

---

### Post by MissBaksel on 2011-11-15
It's funny because when I install my windows versions I also have to do this. 
Ubuntu is new for me so I think it just slipped my mind. 
I'm not used to work with terminals and when I use the terminal I just copy/paste without understanding what I'm doing. 

Next step: trying to copy the data on my damaged external hard drive.

Greetz.

---

### Post by Cyclane on 2011-11-15
I think you mean that you want to recover data FROM your damaged HD?

Method I always use for this is described on the following website: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
> 
First you copy as much data as possible, without retrying or splitting sectors:

ddrescue --no-split /dev/hda1 imagefile logfile 
Now let it retry previous errors 3 times, using uncached reads:

ddrescue --direct --max-retries=3 /dev/hda1 imagefile logfile 
If that fails you can try again but retrimmed, so it tries to reread full sectors:

ddrescue --direct --retrim --max-retries=3 /dev/hda1 imagefile logfile 

---

### Post by ezsit on 2011-11-15
Glad to hear you got this sorted out.

---

### Post by MissBaksel on 2011-11-17
Thanks for the advice but I'm using the commands based on example 2 of the manual:
```

Example 2: Rescue an ext2 partition in /dev/hda2 to /dev/hdb2.
Note: you need to create the hdb2 partition with fdisk first. hdb2
should be of appropiate type and size.

     ddrescue -f -n /dev/hda2 /dev/hdb2 logfile
     ddrescue -d -f -r3 /dev/hda2 /dev/hdb2 logfile
     e2fsck -v -f /dev/hdb2
     mount -t ext2 -o ro /dev/hdb2 /mnt
       (read rescued files from /mnt)

```If this doesn't work I will use your commands.
These are my results so far. I paused the commands because I wasn't sure my disks were unmounted.

```

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:     12288 B,  errsize:      1 TB,  errors:       1
Current status
rescued:     12288 B,  errsize:      1 TB,  current rate:        0 B/s
   ipos:   906314 kB,   errors:       1,    average rate:        0 B/s
   opos:   906314 kB,     time from last successful read:       1 h
^Clitting failed blocks...
Interrupted by user
john@john-desktop:~$ sudo umount /dev/sdc
[sudo] password for john: 
umount: /dev/sdc: niet aangekoppeld
john@john-desktop:~$ sudo umount /dev/sdb
umount: /dev/sdb: niet aangekoppeld
john@john-desktop:~$ sudo ddrescue -d -f -r3 /dev/sdc /dev/sdb logfile


Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:     12288 B,  errsize:      1 TB,  errors:       1
Current status
rescued:     12288 B,  errsize:      1 TB,  current rate:        0 B/s
   ipos:     4026 MB,   errors:       1,    average rate:        0 B/s
   opos:     4026 MB,     time from last successful read:    21.3 m
Splitting failed blocks...

```Thanks;)

---

### Post by Cyclane on 2011-11-17
If you are sure that the disk you are copying to has enough space this will do just as well.

by the way, the last command in the example you've posted will probably not work for you. You'll need to replace ext2 with the appropriate file system (probably ext4).

Ok so you first posted the command:
sudo ddrescue -f -n /dev/hdc /dev/sdb logfile
after that you issued the following command:
sudo ddrescue -d -f -r3 /dev/sdc /dev/sdb logfile
But you interrupted that command and reran it after making sure the disk was unmounted.

In that case It's not looking very good so far but it might turn around. If you want to try again later on and start from the beginning, make sure to delete the file logfile (or choosing a different name for your log file in the command).

---

### Post by MissBaksel on 2011-11-17
You're right it didn't work out;).

I have the following problems. Both of my disks are in NTFS format. What I tried to do is first to make an image of my old hard drive data in my new hard drive and then try to fix this image in real data. Oldfred also told me that ddrescue can't fix data in NTFS so I wanted to use chkdsk in windows for fixing this image. Is this possible or am I telling crazytalk?

My both external hard drives are 1TB and my ubuntu partition is 40G. The logfile I create always ends up in my personal document (in ubuntu partition) and has a size of 1,6MB. My new hard drive always stays empty. I think ddrescue needs the logfile to know what he has to do? But you're right, in the second line, the current rate stays zero and my new hard drive stays empty.
```

sudo ddrescue -d -f -r3 /dev/sdc /dev/sdb logfile

```I think this means that ddrescue copys the data from sdc to sdb and creates a logfile in my ubuntupartion?

I actually don't understand your code:
```
sudo ddrescue -n /dev/sdc data.img logfile 
```In my impression this means that the data on my old hard drive is set as an image and as a logfile on my ubuntu partition. My output device (new hard drive) isn't mentioned in this code. 

Thanks for helping me8)

---

### Post by Cyclane on 2011-11-19
Like I said in my previous post. My command is the same as the command you used. The only thing that's different is the output destination. In your case you directed your output to a device, but you can also direct the output to a file.

Like you mentioned the logfile is pretty important for ddrescue. That's why I wanted to know what exactly you did, especially because you interrupted the proces. Did the proces run completely the first time?

By the way ddrescue is completely unaware of filesystems so the disk using NTFS shouldn't be a problem. Where did Oldfred post this? I would like to see this for myself.

---

### Post by MissBaksel on 2011-11-19
Yes the proces run completely but he didn't rescue anything.

Oldfred posted this over here: [http://ubuntuforums.org/showthread.php?t=1881512](http://ubuntuforums.org/showthread.php?t=1881512)
I started a thread to know how you could learn how to work with ddrescue, but now I finally understand the "language" my broken hard drive isn't cooperating.

thanks for the advice dough, I might not have rescued my data but I did learn a lot. 
I will keep trying and if it does work, I will let you guys know.

---

### Post by Cyclane on 2011-11-20
Ahhh oldfred is refering to repairing NTFS filesystems and not to ddrescue. ddrescue just tries to copy as much as possible but it doesn't actually tries to fix anything. I believe it's always best to first ddrescue a disk and after that try to fix what is left. Repairing your disk can actually corrupt your files and make the situation worse so try to ddrescue first.

---

