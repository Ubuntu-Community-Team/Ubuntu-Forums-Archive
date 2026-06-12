---
title: "IEEE 1394 problem with Ubuntu 10.10"
date: 2010-10-31
forum: General Help
---

### Post by ejog on 2010-10-31
Is anyone having a problem with connecting via a IEEE 1394 ( Firewire ) cable on Ubuntu 10.10?

My scanner is a Nikon Coolscan 4000ED which worked perfectly through Vuescan on 10.04 and below, but after I upgraded to 10.10, Vuescan reports 'no scanner connected'. I've tried with Xsane and Simple Scan as well with the same result.

---

### Post by piponazo on 2010-11-23
Me and my colleagues are having problems with Ubuntu 10.10 and PCI Firewire cards for recording for monocular and stereo cameras. With previous versions of Ubuntu we didn't have these problems :S. It seems that is a consequence of new firewire modules.

---

### Post by no2498 on 2010-11-23
so you did an online upgrade
not a fresh install
that installs a new sources list
does not upgrade the old 1



sorry i cant help any more than that

---

### Post by no2498 on 2010-11-23
this may help you im not sure 

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by newindustar on 2011-01-05
Hi I am new to Ubuntu, justswitched from Kubuntu 10.04 64 bit. Installed 10.10 64-bit  clean.

 Really like 10.10 Ubuntu except for this Firewire scanner issue. I run a Minolta Multi Pro with firewire and a Nikon Coolscan with usb
 and an Epson 4800 works with usb but not firewire so this is definitely a firewire issue. Now same hardware, I have 2 firewire ports, both show up
under lspci and mod probe. I added an Adapted scsc card as well. The
scsi card shows up under Ubuntu's disk manager but neither firewire
port does.


I emailed Vuescan developer and received this:

I'm guessing it's a problem with device protections on /dev/sg* devices.

You can verify this by running VueScan as root and seeing if it
sees the scanner.

Regards,
Ed Hamrick

I am new to Linux not sure how to run Vuescan as root. Here's how I tried:
[sudo] password for industar: 
# cd \/home/industar/Software/  
ls
VueScan  vuex6490.tgz
     
# vuescan
sh: vuescan: not found
# run vuescan
sh: run: not found

# sudo apt-get install ia32-libs-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'ia32-libs' instead of 'ia32-libs-gtk'
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.


Can you help me run Vuescan as root to test Ed's theory? Thanks

PS I was able to use alt-f2 to run it but not sure if alt-f2 would be as root even though I am in terminal. Sorry for these basic Linux stumbles.

---

### Post by coldraven on 2011-01-05
Ctrl+Alt+T will open a terminal.
Try typing ```
sudo vuescan
```
or
```
gksudo vuescan
```

---

### Post by newindustar on 2011-01-07
I just needed a ./vuescan. I don't remember having to do that in other Linuxes if I was already in the directory with the app.

industar@industar:~/Software/VueScan$ sudo ./vuescan

It turns out this solved a permissions problem with   /dev/sg* . Vuescan will now mount the firewire scanners normally. Is there a way to permanetly fix   /dev/sg* permissions so I don't have to launch Vuescan in terminal with sudo ./vuescan?

Also I am confused as to if  /dev/sg* only pertains to Firewire. If you recall I was not having problems mounting scsi card or usb scanners. 
Thanks

---

### Post by torsionbar on 2011-11-11
I found this thread with a forum search. I'm using Ubuntu 10.04 AMD64.  My scanner works when connected via USB, but not via Firewire.  Scanning via USB is so slow it's horrible and painful, so I really wanted to get the firewire connectivity working.

I have an Epson Perfection 4870.  I plugged it in, and I got the following output from dmesg:

[FONT=Courier New][SIZE=2][128384.639659] firewire_core: skipped bus generations, destroying all nodes
[128385.130048] firewire_core: rediscovered device fw0
[128385.130066] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[128388.140967] firewire_core: created device fw1: GUID 0000480000254816, S400, 1 config ROM retries
[128388.361742] scsi9 : SBP-2 IEEE-1394
[128388.361895] firewire_sbp2: fw1.0: 127s mgt_ORB_timeout limited to 40s
[128388.562417] firewire_sbp2: fw1.0: logged in to LUN 0000 (0 retries)
[128388.569269] scsi 9:0:0:0: Processor         EPSON    GT-X700          1.18 PQ: 0 ANSI: 4
[128388.569449] scsi 9:0:0:0: Attached scsi generic sg9 type 3[/SIZE][/FONT]

Ok, this all looks promising.  But then when I run XSane or Simple Scan, I get an error that no scanners were found.  Next I looked at /dev/sg9 and there I found the problem!  Only root has access to this device, and no one else.
[FONT=Courier New][SIZE=2]
crw------- 1 root root 21, 9 2011-11-11 11:47 /dev/sg9[/SIZE][/FONT]

I corrected it with a chmod 666 /dev/sg9 so that anyone can read/write to this device, and now it works perfectly. ** Problem solved**.
[FONT=Courier New][SIZE=2]
crw-rw-rw- 1 root root 21, 9 2011-11-11 11:47 /dev/sg9[/SIZE][/FONT]

---

