---
title: "How can I SUCCESSFULLY Burn a Video DVD?"
date: 2009-11-11
forum: General Help
---

### Post by Xalticus on 2009-11-11
I have been trying at this for several days now, and have road block, after road block, after road block, I have browsed the forum for previously answered topics, and nothing I have found has helped significantly.

I am using Ubuntu Intrepid Ibex the most recent kernel.(As of this post)

```
The following commands will be run:
=========================================
makedvd -quiet -author -burn -device /dev/sr0 /tmp/Untitled_disc.xml
------------------------
Running command: makedvd -quiet -author -burn -device /dev/sr0 /tmp/Untitled_disc.xml
--------------------------------
makedvd
A script to create a DVD-Video file structure and burn it to DVD
Part of the tovid suite, version 0.31
http://www.tovid.org
--------------------------------
Authoring disc from file: /tmp/Untitled_disc.xml
=========================================================
Creating disc structure with the following command:
dvdauthor -x "/tmp/Untitled_disc.xml"
=========================================================
DVDAuthor::dvdauthor, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: Locale=en_CA.UTF-8
INFO: Converting filenames to UTF-8
INFO: dvdauthor creating VTS
STAT: Picking VTS 01

STAT: Processing /tmp/Untitled_menu_1.mpg...
STAT: VOBU 16 at 1MB, 1 PGCS
STAT: VOBU 32 at 3MB, 1 PGCS
STAT: VOBU 48 at 5MB, 1 PGCS 
STAT: VOBU 64 at 7MB, 1 PGCS 
STAT: VOBU 80 at 9MB, 1 PGCS
STAT: VOBU 96 at 11MB, 1 PGCS
STAT: VOBU 112 at 13MB, 1 PGCS
STAT: VOBU 128 at 15MB, 1 PGCS
STAT: VOBU 144 at 17MB, 1 PGCS
........**Continues like this for a few pages worth of text**....
STAT: fixing VOBU at 1546MB (18385/18384, 100%) STAT: fixed 18384 VOBUS                         
INFO: dvdauthor creating table of contents
INFO: Scanning /tmp/Untitled_disc/VIDEO_TS/VTS_01_0.IFO
=========================================================
Authoring completed.
=========================================================
Found blank DVD-R.
=========================================================
Burning with growisofs 7.1 using the following command:
growisofs -use-the-force-luke=dao -dvd-compat  -Z /dev/sr0 -dvd-video -V "UNTITLED_DISC" "/tmp/Untitled_disc"
=========================================================
Executing 'genisoimage -dvd-video -V UNTITLED_DISC /tmp/Untitled_disc | builtin_dd of=/dev/sr0 obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.62% done, estimate finish Wed Nov 11 16:17:27 2009
  1.23% done, estimate finish Wed Nov 11 16:16:06 2009
  1.84% done, estimate finish Wed Nov 11 16:15:39 2009
/dev/sr0: engaging DVD-R DAO upon user request...
:-[ PERFORM OPC failed with SK=3h/POWER CALIBRATION AREA IS FULL]: Input/output error
genisoimage: Broken pipe. cannot fwrite 32768*1
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
makedvd encountered an error during the DVD creation process:
Could not burn the disc to /dev/sr0
See if anything in the above output helps you diagnose the
problem, and please file a bug report at tovid.org (_not_
the dvdauthor list) containing the above output.
Sorry for the inconvenience!
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

```I have no idea what any of that means or is in reference to, all I know is that my DVD did not Burn successfully and it is yet another program that hasn't worked.

So far I've used K3B, Varsha, ToVid, ToDisc, and DVDAuthor none have worked, and I'm not looking for any other Burner program as all of those -Should- work.  The problem is not with the file either as I've tried and failed with Multiple versions of the media file.

Here's info on my DVD drive that I've procured.
```
jason@jason-desktop:~$ sudo hdparm -I /dev/sr0

/dev/sr0:

ATAPI CD-ROM, with removable media
    Model Number:       BENQ    DVD DD DW1620                   
    Serial Number:      
    Firmware Revision:  B7L9    
Standards:
    Likely used CD-ROM ATAPI-1
Configuration:
    DRQ response: 50us.
    Packet size: 12 bytes
Capabilities:
    LBA, IORDY(cannot be disabled)
    DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
HW reset results:
    CBLID- above Vih
    Device num = 1

```Also:
```
jason@jason-desktop:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-14-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jason/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jason)
```Any help that can be offered is appreciated.

---

### Post by Xalticus on 2009-11-11
Even if you can identify the issue it is having/make sense of the posted information, I will be grateful.  I am still relatively new to Linux and not every thing is clear to me.

---

### Post by 824957q on 2009-11-11
ok make sure you have a good dvd burning program then make sure you have the following dvd+r data video 4gigabytes or higher then make sure you have a burner then you should be all set and dont forget to mark your post as solved

---

### Post by imtheguru on 2009-11-11
> Executing 'genisoimage -dvd-video -V UNTITLED_DISC /tmp/Untitled_disc | builtin_dd of=/dev/sr0 obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.62% done, estimate finish Wed Nov 11 16:17:27 2009
  1.23% done, estimate finish Wed Nov 11 16:16:06 2009
  1.84% done, estimate finish Wed Nov 11 16:15:39 2009
/dev/sr0: engaging DVD-R DAO upon user request...
:-[ PERFORM OPC failed with SK=3h/POWER CALIBRATION AREA IS FULL]: Input/output error
genisoimage: Broken pipe. cannot fwrite 32768*1

This doesn't seem to be an Ubuntu-related issue; more of a hardware problem.

[http://www.google.com/search?rlz=1C1GGLS_enUS339US340&sourceid=chrome&ie=UTF-8&q=POWER+CALIBRATION+AREA+IS+FULL](http://www.google.com/search?rlz=1C1GGLS_enUS339US340&sourceid=chrome&ie=UTF-8&q=POWER+CALIBRATION+AREA+IS+FULL)

Here's a possible explanation.

> Power Calibration is controlled by the recorder. 

Before any write operation, all recorders must do a 15 step power test to determine the optimum power for writing to the CD; this is called "Optimum Power Calibration"(OPC). During the write, it continues to do this test to get the best write throughout the whole CD; this is called "Running Optimum Power Calibration" (ROPC).
This whole process is controlled by the recorder, though initiated by programs such as Nero. There is an area on the inner part of the CD for the test and test data info to be stored. You can use this area up to 999 times.

If you receive the "Power calibration error" or "Power calibration area is (amost) full" error message, the cause will be either poor media, poor power, or a defective recorder.

Please try the following solutions:
Update the firmware of your recorder. Please check the manufacturer's website for the latest version.
Try another brand of CD-R or CD-RW media.
Try different power connectors, and for recorders, do not share power with other devices. It needs its own power connector. If the error occurs with an external recorder, the power source in the chassis could be the cause. As a test, try to take the recorder out of the external chassis and connect it internal.
Try different configurations, such as taking the CD-ROM to the primary IDE bus as slave and have only the recorder connected to the secondary IDE bus as master.
Send the recorder in for service.

---

### Post by imtheguru on 2009-11-11
> **824957q said:**
> ok make sure you have a good dvd burning program then make sure you have the following dvd+r data video 4gigabytes or higher then make sure you have a burner then you should be all set and dont forget to mark your post as solved Completely pointless post.

What is the definition of a 'good dvd burning program'? The OP lists multiple applications and none has worked.

The OP is using a DVD-R. It's listed in the logs.

---

### Post by Imoen on 2009-11-11
I am also having issues with this but it tells me that program doesn't have permission to write to the disk. Maybe that is your problem too?

---

### Post by Xalticus on 2009-11-12
<snip>

**imtheguru:**
The information you provided helped me figure out a solution that resulted in a successfully recorded DVD!

```
Running dvdauthor to create the DVD filesystem
DVDAuthor::dvdauthor, version 0.6.14.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: Locale=en_CA.UTF-8
INFO: Converting filenames to UTF-8
INFO: dvdauthor creating VTS
STAT: Picking VTS 01

STAT: Processing /tmp/todisc-work.1/animenu1-1.mpg...

INFO: Video pts = 0.178 .. 2.146
INFO: Audio[0] pts = 0.178 .. 2.130
INFO: Audio[32] pts = 0.178 .. 0.178
STAT: VOBU 5 at 0MB, 1 PGCS
INFO: Generating VTSM with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: ntsc
INFO: Aspect ratio: 4:3
INFO: Resolution: 720x480
INFO: Audio ch 0 format: ac3/2ch, 48khz drc

STAT: Processing /tmp/todisc-work.1/1-1.mpg...
STAT: VOBU 17056 at 1737MB, 1 PGCS
INFO: Video pts = 0.500 .. 6904.563
INFO: Audio[0] pts = 0.500 .. 6904.628
STAT: VOBU 17065 at 1738MB, 1 PGCS
INFO: Generating VTS with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: ntsc
INFO: Aspect ratio: 16:9
INFO: Resolution: 720x480
INFO: Audio ch 0 format: ac3/2ch, 48khz drc

STAT: fixed 5 VOBUS                         
STAT: fixed 17065 VOBUS                         
INFO: dvdauthor creating table of contents
INFO: Scanning /home/jason/cbtm kohd/VIDEO_TS/VTS_01_0.IFO
INFO: Creating menu for TOC

STAT: Processing /tmp/todisc-work.1/dummy.mpg...

INFO: Video pts = 0.178 .. 1.145
INFO: Audio[0] pts = 0.178 .. 1.170
STAT: VOBU 3 at 0MB, 1 PGCS
INFO: Generating VMGM with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: ntsc
INFO: Aspect ratio: 4:3
INFO: Resolution: 720x480
INFO: Audio ch 0 format: ac3/2ch, 48khz drc

STAT: fixed 3 VOBUS                         
Cleaning up unwanted files in /home/jason/todisc-work.0
removed directory: `/tmp/todisc-work.1/animenu'
removed directory: `/tmp/todisc-work.1/pics/0'
removed directory: `/tmp/todisc-work.1/pics'

=========================================================
todisc took 00:07:20.000 to finish on  AMD Athlon(tm) 64 Processor 3000+ 1000.000 mhz
=========================================================
Your new DVD should be in /home/jason/cbtm kohd
You can preview them in gxine with this command:
    gxine "dvd://home/jason/cbtm kohd"
If you are satisfied with the results, you can burn a disc with:
    makedvd -burn "/home/jason/cbtm kohd"

Thanks for using todisc.

=========================================================

You have indicated you want to burn the DVD directory
Would you like to burn the DVD now ?
Type 'yes' to continue: yes

Proceeding to burn, continuing.

--------------------------------
makedvd
A script to create a DVD-Video file structure and burn it to DVD
Part of the tovid suite, version 0.31
http://www.tovid.org
--------------------------------
=========================================================
Please insert a blank DVD+/-R(W) disc into your DVD-recorder
(/dev/sr0) if you have not already done so.
expr: syntax error
(standard_in) 1: syntax error
=========================================================
Found no disc in /dev/sr0. Cannot burn to this disc!
Found  no disc. Please insert a usable DVD into /dev/sr0.
Trying again in  1 seconds...
Looking for usable media...
expr: syntax error
(standard_in) 1: syntax error
Found  DVD-R. Please insert a usable DVD into /dev/sr0.
Trying again in  1 seconds...
Looking for usable media...
=========================================================
Found blank DVD-R.
Using disk label "CBTM_KOHD"
=========================================================
Burning with growisofs 7.1 using the following command:
growisofs -use-the-force-luke=dao -dvd-compat -speed=1 -Z /dev/sr0 -dvd-video -V "CBTM_KOHD" "/home/jason/cbtm kohd"
=========================================================
Executing 'genisoimage -dvd-video -V CBTM_KOHD /home/jason/cbtm kohd | builtin_dd of=/dev/sr0 obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.56% done, estimate finish Thu Nov 12 17:33:07 2009
  1.12% done, estimate finish Thu Nov 12 17:31:37 2009
  1.68% done, estimate finish Thu Nov 12 17:31:08 2009
/dev/sr0: engaging DVD-R DAO upon user request...
/dev/sr0: reserving 890895 blocks
/dev/sr0: "Current Write Speed" is 2.5x1352KBps.
  2.25% done, estimate finish Thu Nov 12 17:40:32 2009
  2.81% done, estimate finish Thu Nov 12 17:40:14 2009
  3.37% done, estimate finish Thu Nov 12 17:40:02 2009
  3.93% done, estimate finish Thu Nov 12 17:39:54 2009
  4.49% done, estimate finish Thu Nov 12 17:39:47 2009
  5.05% done, estimate finish Thu Nov 12 17:39:43 2009
  5.61% done, estimate finish Thu Nov 12 17:39:39 2009
  6.17% done, estimate finish Thu Nov 12 17:39:35 2009
  6.74% done, estimate finish Thu Nov 12 17:39:33 2009
  7.30% done, estimate finish Thu Nov 12 17:39:30 2009
  7.86% done, estimate finish Thu Nov 12 17:39:41 2009
  8.42% done, estimate finish Thu Nov 12 17:39:39 2009
  8.98% done, estimate finish Thu Nov 12 17:39:36 2009
  9.54% done, estimate finish Thu Nov 12 17:39:34 2009
 10.10% done, estimate finish Thu Nov 12 17:39:33 2009
 10.66% done, estimate finish Thu Nov 12 17:39:31 2009
 11.23% done, estimate finish Thu Nov 12 17:39:30 2009
 11.79% done, estimate finish Thu Nov 12 17:39:28 2009
 12.35% done, estimate finish Thu Nov 12 17:39:27 2009
 12.91% done, estimate finish Thu Nov 12 17:39:26 2009
 13.47% done, estimate finish Thu Nov 12 17:39:33 2009
 14.03% done, estimate finish Thu Nov 12 17:39:32 2009
 14.59% done, estimate finish Thu Nov 12 17:39:30 2009
 15.15% done, estimate finish Thu Nov 12 17:39:29 2009
 15.72% done, estimate finish Thu Nov 12 17:39:28 2009
 16.28% done, estimate finish Thu Nov 12 17:39:28 2009
 16.84% done, estimate finish Thu Nov 12 17:39:27 2009
 17.40% done, estimate finish Thu Nov 12 17:39:26 2009
 17.96% done, estimate finish Thu Nov 12 17:39:25 2009
 18.52% done, estimate finish Thu Nov 12 17:39:25 2009
 19.08% done, estimate finish Thu Nov 12 17:39:24 2009
 19.64% done, estimate finish Thu Nov 12 17:39:28 2009
 20.21% done, estimate finish Thu Nov 12 17:39:28 2009
 20.77% done, estimate finish Thu Nov 12 17:39:27 2009
 21.33% done, estimate finish Thu Nov 12 17:39:26 2009
 21.89% done, estimate finish Thu Nov 12 17:39:26 2009
 22.45% done, estimate finish Thu Nov 12 17:39:25 2009
 23.01% done, estimate finish Thu Nov 12 17:39:25 2009
 23.57% done, estimate finish Thu Nov 12 17:39:24 2009
 24.13% done, estimate finish Thu Nov 12 17:39:24 2009
 24.70% done, estimate finish Thu Nov 12 17:39:23 2009
 25.26% done, estimate finish Thu Nov 12 17:39:27 2009
 25.82% done, estimate finish Thu Nov 12 17:39:26 2009
 26.38% done, estimate finish Thu Nov 12 17:39:26 2009
 26.94% done, estimate finish Thu Nov 12 17:39:25 2009
 27.50% done, estimate finish Thu Nov 12 17:39:25 2009
 28.06% done, estimate finish Thu Nov 12 17:39:24 2009
 28.62% done, estimate finish Thu Nov 12 17:39:24 2009
 29.19% done, estimate finish Thu Nov 12 17:39:34 2009
 29.75% done, estimate finish Thu Nov 12 17:39:33 2009
 30.31% done, estimate finish Thu Nov 12 17:39:33 2009
 30.87% done, estimate finish Thu Nov 12 17:39:32 2009
 31.43% done, estimate finish Thu Nov 12 17:39:35 2009
 31.99% done, estimate finish Thu Nov 12 17:39:34 2009
 32.55% done, estimate finish Thu Nov 12 17:39:34 2009
 33.11% done, estimate finish Thu Nov 12 17:39:33 2009
 33.68% done, estimate finish Thu Nov 12 17:39:33 2009
 34.24% done, estimate finish Thu Nov 12 17:39:32 2009
 34.80% done, estimate finish Thu Nov 12 17:39:32 2009
 35.36% done, estimate finish Thu Nov 12 17:39:31 2009
 35.92% done, estimate finish Thu Nov 12 17:39:31 2009
 36.48% done, estimate finish Thu Nov 12 17:39:30 2009
 37.04% done, estimate finish Thu Nov 12 17:39:30 2009
 37.60% done, estimate finish Thu Nov 12 17:39:32 2009
 38.17% done, estimate finish Thu Nov 12 17:39:32 2009
 38.73% done, estimate finish Thu Nov 12 17:39:31 2009
 39.29% done, estimate finish Thu Nov 12 17:39:31 2009
 39.85% done, estimate finish Thu Nov 12 17:39:31 2009
 40.41% done, estimate finish Thu Nov 12 17:39:30 2009
 40.97% done, estimate finish Thu Nov 12 17:39:30 2009
 41.53% done, estimate finish Thu Nov 12 17:39:30 2009
 42.09% done, estimate finish Thu Nov 12 17:39:29 2009
 42.65% done, estimate finish Thu Nov 12 17:39:29 2009
 43.22% done, estimate finish Thu Nov 12 17:39:28 2009
 43.78% done, estimate finish Thu Nov 12 17:39:30 2009
 44.34% done, estimate finish Thu Nov 12 17:39:30 2009
 44.90% done, estimate finish Thu Nov 12 17:39:30 2009
 45.46% done, estimate finish Thu Nov 12 17:39:29 2009
 46.02% done, estimate finish Thu Nov 12 17:39:29 2009
 46.58% done, estimate finish Thu Nov 12 17:39:29 2009
 47.14% done, estimate finish Thu Nov 12 17:39:28 2009
 47.71% done, estimate finish Thu Nov 12 17:39:28 2009
 48.27% done, estimate finish Thu Nov 12 17:39:28 2009
 48.83% done, estimate finish Thu Nov 12 17:39:34 2009
 49.39% done, estimate finish Thu Nov 12 17:39:33 2009
 49.95% done, estimate finish Thu Nov 12 17:39:33 2009
 50.51% done, estimate finish Thu Nov 12 17:39:39 2009
 51.07% done, estimate finish Thu Nov 12 17:39:38 2009
 51.63% done, estimate finish Thu Nov 12 17:39:38 2009
 52.20% done, estimate finish Thu Nov 12 17:39:38 2009
 52.76% done, estimate finish Thu Nov 12 17:39:37 2009
 53.32% done, estimate finish Thu Nov 12 17:39:37 2009
 53.88% done, estimate finish Thu Nov 12 17:39:36 2009
 54.44% done, estimate finish Thu Nov 12 17:39:36 2009
 55.00% done, estimate finish Thu Nov 12 17:39:38 2009
 55.56% done, estimate finish Thu Nov 12 17:39:37 2009
 56.12% done, estimate finish Thu Nov 12 17:39:37 2009
 56.68% done, estimate finish Thu Nov 12 17:39:37 2009
 57.25% done, estimate finish Thu Nov 12 17:39:36 2009
 57.81% done, estimate finish Thu Nov 12 17:39:36 2009
 58.37% done, estimate finish Thu Nov 12 17:39:36 2009
 58.93% done, estimate finish Thu Nov 12 17:39:35 2009
 59.49% done, estimate finish Thu Nov 12 17:39:35 2009
 60.05% done, estimate finish Thu Nov 12 17:39:35 2009
 60.61% done, estimate finish Thu Nov 12 17:39:34 2009
 61.17% done, estimate finish Thu Nov 12 17:39:36 2009
 61.74% done, estimate finish Thu Nov 12 17:39:35 2009
 62.30% done, estimate finish Thu Nov 12 17:39:35 2009
 62.86% done, estimate finish Thu Nov 12 17:39:35 2009
 63.42% done, estimate finish Thu Nov 12 17:39:35 2009
 63.98% done, estimate finish Thu Nov 12 17:39:34 2009
 64.54% done, estimate finish Thu Nov 12 17:39:34 2009
 65.10% done, estimate finish Thu Nov 12 17:39:34 2009
 65.66% done, estimate finish Thu Nov 12 17:39:33 2009
 66.23% done, estimate finish Thu Nov 12 17:39:33 2009
 66.79% done, estimate finish Thu Nov 12 17:39:33 2009
 67.35% done, estimate finish Thu Nov 12 17:39:34 2009
 67.91% done, estimate finish Thu Nov 12 17:39:34 2009
 68.47% done, estimate finish Thu Nov 12 17:39:34 2009
 69.03% done, estimate finish Thu Nov 12 17:39:33 2009
 69.59% done, estimate finish Thu Nov 12 17:39:33 2009
 70.15% done, estimate finish Thu Nov 12 17:39:33 2009
 70.72% done, estimate finish Thu Nov 12 17:39:33 2009
 71.28% done, estimate finish Thu Nov 12 17:39:32 2009
 71.84% done, estimate finish Thu Nov 12 17:39:32 2009
 72.40% done, estimate finish Thu Nov 12 17:39:32 2009
 72.96% done, estimate finish Thu Nov 12 17:39:32 2009
 73.52% done, estimate finish Thu Nov 12 17:39:33 2009
 74.08% done, estimate finish Thu Nov 12 17:39:33 2009
 74.64% done, estimate finish Thu Nov 12 17:39:35 2009
 75.21% done, estimate finish Thu Nov 12 17:39:35 2009
 75.77% done, estimate finish Thu Nov 12 17:39:35 2009
 76.33% done, estimate finish Thu Nov 12 17:39:34 2009
 76.89% done, estimate finish Thu Nov 12 17:39:34 2009
 77.45% done, estimate finish Thu Nov 12 17:39:35 2009
 78.01% done, estimate finish Thu Nov 12 17:39:35 2009
 78.57% done, estimate finish Thu Nov 12 17:39:35 2009
 79.13% done, estimate finish Thu Nov 12 17:39:35 2009
 79.70% done, estimate finish Thu Nov 12 17:39:34 2009
 80.26% done, estimate finish Thu Nov 12 17:39:34 2009
 80.82% done, estimate finish Thu Nov 12 17:39:34 2009
 81.38% done, estimate finish Thu Nov 12 17:39:34 2009
 81.94% done, estimate finish Thu Nov 12 17:39:34 2009
 82.50% done, estimate finish Thu Nov 12 17:39:33 2009
 83.06% done, estimate finish Thu Nov 12 17:39:33 2009
 83.62% done, estimate finish Thu Nov 12 17:39:34 2009
 84.19% done, estimate finish Thu Nov 12 17:39:34 2009
 84.75% done, estimate finish Thu Nov 12 17:39:34 2009
 85.31% done, estimate finish Thu Nov 12 17:39:34 2009
 85.87% done, estimate finish Thu Nov 12 17:39:33 2009
 86.43% done, estimate finish Thu Nov 12 17:39:33 2009
 86.99% done, estimate finish Thu Nov 12 17:39:33 2009
 87.55% done, estimate finish Thu Nov 12 17:39:33 2009
 88.11% done, estimate finish Thu Nov 12 17:39:33 2009
 88.68% done, estimate finish Thu Nov 12 17:39:32 2009
 89.24% done, estimate finish Thu Nov 12 17:39:32 2009
 89.80% done, estimate finish Thu Nov 12 17:39:33 2009
 90.36% done, estimate finish Thu Nov 12 17:39:33 2009
 90.92% done, estimate finish Thu Nov 12 17:39:33 2009
 91.48% done, estimate finish Thu Nov 12 17:39:33 2009
 92.04% done, estimate finish Thu Nov 12 17:39:32 2009
 92.60% done, estimate finish Thu Nov 12 17:39:32 2009
 93.17% done, estimate finish Thu Nov 12 17:39:32 2009
 93.73% done, estimate finish Thu Nov 12 17:39:32 2009
 94.29% done, estimate finish Thu Nov 12 17:39:32 2009
 94.85% done, estimate finish Thu Nov 12 17:39:32 2009
 95.41% done, estimate finish Thu Nov 12 17:39:31 2009
 95.97% done, estimate finish Thu Nov 12 17:39:32 2009
 96.53% done, estimate finish Thu Nov 12 17:39:32 2009
 97.09% done, estimate finish Thu Nov 12 17:39:32 2009
 97.66% done, estimate finish Thu Nov 12 17:39:35 2009
 98.22% done, estimate finish Thu Nov 12 17:39:35 2009
 98.78% done, estimate finish Thu Nov 12 17:39:34 2009
 99.34% done, estimate finish Thu Nov 12 17:39:34 2009
 99.90% done, estimate finish Thu Nov 12 17:39:34 2009
Total translation table size: 0
Total rockridge attributes bytes: 0
Total directory bytes: 4096
Path table size(bytes): 42
Max brk space used 0
890895 extents written (1740 MB)
/dev/sr0: flushing cache
=========================================================
Done. You should now have a working DVD. Please visit
the tovid homepage: http://www.tovid.org
=========================================================
Thanks for using makedvd!
Your DVD should be ready

Cleaning up...
Removing /home/jason/todisc-work.0
Removing the symlink in /tmp . . . 
removed `/tmp/todisc-work.1'


```

Basically what I need to remember to do from now on is not place the Blank-DVD into the drive until prompted to, otherwise it  perpetually reads the blank disc, thus resulting in Power Failure and loss of functionality of the drive.

I also turned down the Copy speed from the Default of 8x, down to 2x it only took about 10-15 minutes to complete.

Cheers

---

### Post by imtheguru on 2009-11-17
> **Xalticus said:**
> <snip>

**imtheguru:**
The information you provided helped me figure out a solution that resulted in a successfully recorded DVD!

Basically what I need to remember to do from now on is not place the Blank-DVD into the drive until prompted to, otherwise it  perpetually reads the blank disc, thus resulting in Power Failure and loss of functionality of the drive.

I also turned down the Copy speed from the Default of 8x, down to 2x it only took about 10-15 minutes to complete.

Cheers

That's an interesting problem you discovered.
Happy to be of assistance.

Cheers.

---

