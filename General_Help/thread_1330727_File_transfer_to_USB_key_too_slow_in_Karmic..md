---
title: "File transfer to USB key too slow in Karmic."
date: 2009-11-18
forum: General Help
---

### Post by bhishan on 2009-11-18
I am using Karmic 64 bit in my laptop. The time that takes to transfer files to my USB drives takes almost 20 times more than it used to take in Jaunty. Sometimes after waiting for a long time of transfering it will simply give a error message or the file will simply will not get transferred. Yesterday I tried to transfer a 700MB (90 mins) avi file, i had to wait for almost 20 minutes for it to get transferred and when I tried to watch it in another computer it played only the first 2 mins of the file. Is there any known bug that I can fix?

---

### Post by MidBSD on 2009-11-23
I'm having this problem too. It takes a long, long time to copy large files to a USB memory stick.

Anyone have any fixes for this?

I've also noticed that latency goes through the roof when the speed slows down.

---

### Post by bhishan on 2009-11-25
The transfer starts fast like at 20 MB/sec and slows down with time to around 50 KB/sec. So the first half of the file gets copied in 2 minutes and the second half takes another 15 minutes. Yesterday I tried copying it to a external hard drive and it works perfectly well.

---

### Post by guiwegian on 2009-11-28
I am using Ubuntu 9.10 32 bits.And When I copy a file from Pc to external Hard drive, the first 123 MO are really fast fast, theb it stops completely.
Any idea???
If i copy any file under 122/123 Mo is is fine but bigger than , it is just stop

---

### Post by CYD on 2009-11-28
I've got the same issue.  Sandisk Cruzer 8GB won't let me transfer any larger 100MB+ files without slowing to a crawl.

---

### Post by at016mx on 2009-11-29
I am experiencing exactly the same as you guys.

I had ubuntu jaunty on a Thinkpad T30 and USB file transfers were executed perfectly.

Recently I moved to Karmic (fresh install) and now USB file transfers are PAINFULLY slow.

I find it very frustrating :confused: and any help will be VERY WELCOMED.

Thanks.

---

### Post by efflandt on 2009-11-29
I don't think there is any general usb mass storage issue for 9.10.  Yesterday I transferred several iso files between laptop & usb and desktop & usb (WD Passport).  And I have been trying numerous Ubuntu variations from 4 GB USB stick.  I even put bootable 64-bit 9.10 on 2 GB Lexar microSD.

One thing I did notice is that the inexpensive **Sandisk Cruzer** that I normally leave on my BluRay player was incredibly slow to boot a live/install iso.  It took about twice as long as my HP USB stick.  It must have something to do with U3 encryption which is some sort of firmware psuedo CD that shows up as an additional sr device automounted as cdrom even if the stick is wiped and repartitioned and formatted.  So even microSD in a card reader boots much faster than a Cruzer.

So I would avoid using a Sandisk Cruzer for a bootable system.

---

### Post by Aperculum on 2009-12-02
I seem to experience similar problems. It might be have something to do with the ubuntu copy dialog system since this always happens when copying with nautilus. But when I copy with midnight commander or simply cp, I get nice and stable 15MB/s speed.

I'm using 64bit karmic too. I don't think I had this problem on jaunty.

---

### Post by e45cream on 2009-12-02
I'm also having this problem on 64  bit Karmic. It seems to have got worse recently. Today i tried different USB sticks and an SD card in a USB connected reader, all with speeds starting fast then slowing to a crawl. In the end I used Dolphin.

---

### Post by Eberbachl on 2009-12-04
Same problem here!

I must say it's infuriating trying to copy mass data at +/- 1MB/second.

It's obviously happening to a number of people - we're not dreaming it.

I have Transcend, Corsair and Kingston USB sticks. Same problem with all of them. Also, same problem with my Western Digital and Hitachi USB hard disks.

:(

---

### Post by fonque on 2009-12-06
I am having the same problem in 9.10. I did not have this issue in 9.04.
My 4GB microcenter usb drive takes a looong time to transfer files to or from the device.

---

### Post by mikeody on 2009-12-06
Intersting Issue.
I havnt experienced what has been described but I do use Clonezilla to back up entire drives to a USB Maxtor external hard drive [NTFS formatted].
5GB is taking about 14 minutes.

---

### Post by uvaio on 2009-12-07
I've got same problem, when I want to copy movie to usb stick of size 700Mb, first 200MB goes almost instantly, then it slows down dramatically and it is able to copy about 500Megs at all and that is after 10 minutes with load about 8 and computer almost not responding with high CPU. File transfer almost stuck.
Same behaviour when copying in Nautilus or using cp in console.
This wasn't happing to me on Jaunty.

---

### Post by svasilis on 2009-12-08
Hello!
Have had this problem in 9.04 and now in 9.10 too. I found this [http://ocaoimh.ie/89494886/ubuntu-linux-slow-external-usb-drive/](http://ocaoimh.ie/89494886/ubuntu-linux-slow-external-usb-drive/) and this [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/66115](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/66115) , pay attention to post number five on the second link. 
Being a noob, I am not sure how to make use of this information, any help would be appreciated and, of course, I hope this works for you.

Edit: Sorry, not such a noob after all! I figured out what I should do; now I need to find the time to do it! ;)

---

### Post by kahlil88 on 2009-12-08
I'm also getting sub-standard write speeds with my Cruzer drives. I've tested them with Mac OS X, Gentoo and Ubuntu (9.04/9.10). It starts to write at 3MB/s and then SLOWS! However, when I tested it with Windows, it surprisingly copied at 8MB/s and up!

---

### Post by svasilis on 2009-12-08
Hello again!
Tried my suggestion as explained on my previous post and it does not work. Note that I have this problem with both 9.04 and 9.10, and it affects SD memory card, usb sticks and external hard drives.

Help!

---

### Post by Linuxforall on 2009-12-08
If you can, turn off legacy mode for usb in BIOS and see if this issue goes away.

---

### Post by svasilis on 2009-12-08
> **Linuxforall said:**
> If you can, turn off legacy mode for usb in BIOS and see if this issue goes away.

Unfortunately, there is no such choice in the Bios.
Thank you anyway!

---

### Post by lamegaptop on 2009-12-11
Disabling legacy usb support in bios did not help here.

---

### Post by bhishan on 2009-12-11
Just to be sure its not nautilus problem, I installed PCMan File Manager and tried copying a 700MB file to my USB flash drive, it does the same thing: fast for the first few secs and then slows down to a crawling speed.

---

### Post by StuartN on 2009-12-11
> **CYD said:**
> I've got the same issue.  Sandisk Cruzer 8GB won't let me transfer any larger 100MB+ files without slowing to a crawl.

Buy another brand of USB flash memory.

The Sandisk Cruzer, and any other USB flash drive with U3 hardware, is just not worth the bother. There is a hardware CDROM emulation as part of the (Windows only) password mechanism, which seems to cause timing errors and remounts. Have a look in dmesg when a long copy either slows or fails.

See also [http://ubuntuforums.org/showthread.php?t=1351452](http://ubuntuforums.org/showthread.php?t=1351452)

---

### Post by raygj on 2009-12-11
this might be worth a try
[http://ubuntuforums.org/showpost.php?p=8466109&postcount=63]("http://ubuntuforums.org/showpost.php?p=8466109&postcount=63")

---

### Post by glasabri on 2009-12-11
[COLOR=black][FONT=&quot]Excellent  ! I like it very much
 
 [/FONT][/COLOR]




_______________________
 [COLOR=black][FONT=&quot][Simulation financement auto achat | ](http://financementautomobile.org/)
[Capacite financement automobile occasion | ](http://financementautomobile.org/)
[Calcul taux financement credit automobile neuve](http://financementautomobile.org/)
 
 [/FONT][/COLOR]

---

### Post by Primefalcon on 2009-12-12
Having the same issue myself, extrememly slow transfer speed

---

### Post by detroit/zero on 2009-12-12
You're not dreaming, and this issue for Ubuntu is as old as 8.04 Hardy Heron. If you search here (or Google) for slow usb file transfers, you'll come up with a bunch of my posts. I have cheap USB sticks, more high-end ones, external hard disks, you name it - it's the same on all of them. 

[I've been all over hell's half acre and back]("http://ubuntuforums.org/showpost.php?p=8010056&postcount=270") trying to fix this bug, and the closest I can come is to change the kernel I/O scheduler for the drive. I have a [small write-up I did here]("http://ubuntuforums.org/showpost.php?p=8124833&postcount=294"), though the steps will have changed for editing the elevator string in the new Grub menu.

Try it out and post back if you noticed any effect on your transfer speeds.

---

### Post by berte on 2009-12-17
> **CYD said:**
> I've got the same issue.  Sandisk Cruzer 8GB won't let me transfer any larger 100MB+ files without slowing to a crawl.

Exact same issue here! :confused:

---

### Post by nhasian on 2009-12-18
this issue is not limited to flash memory.  I have 3 separate external USB 2.0 hard disks and copy files to them are VERY slow.  one is a 2.5" and the other two are 7200 RPM 3.5" drives.  I get really slow file transfers of about 6 MB/sec.

uname -a says:

Linux Ubuntu 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux


also when doing a file copy my entire system slows to a crawl.  i have a dual 2.4Ghz intel cpu with 2 gigs of ram.

---

### Post by jmpmjmpm on 2009-12-18
yup have this problem too. Absolutely pathetic it has been around for so long and not fixed!

---

### Post by theBishop on 2009-12-22
I'm having the problem with karmic 64-bit.  Did not notice it on previous versions.

Really annoying.  I'll dmesg or lspci whatever is necessary if it will help.

---

### Post by Myxb on 2009-12-30
I have had the speed problem with my 120G external USB hard drive. Everything I tried (cp, Nautilus, rsync, mc, remounting with 'async') resulted in a peak initial speed of up to 43 Mb/sec with a later drop to about 2-3 Mb/s. I copied a 31G file. The "crawling" part of the copying started on, roughly, the 2nd G. Also the 'system load' would max out until the system would lose much of its responsiveness.

Then installed the 'mainline' kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.2/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.2/) and this disgrace of a speed is gone!

Now the speed looks roughly as this. It starts with ~21 Mb/s then grows to about 40 Mb/s. Then it drops slowly to about 20-23 Mb/s and stays at that level. Actually is continues to drop, but it is probably due to the target drive geometry (?). The actual speed dropped from 23.6 Mb/s at 10% to 19.5 Mb/s at 100% of the 31G file. The 'system load' as seen in gnome system monitor would not grow and stays here on 2-2.16 points.

So the problem is the Ubuntu 2.6.31 kernel itself, in the 2.6.32.2 the problem is gone.

Hope this will help.

---

### Post by danastasio on 2009-12-30
What file system are you all using? I know that ext4 works just fine for me. so does XFS and JFS (though JFS deleted my entire home folder after a power failure...)

---

### Post by Myxb on 2009-12-30
My system is 64bit. The 'from' FS is ext4, the 'to' FS is a USB external HD with NTFS (for compatibility reasons). With the standard kernel you probably won't notice any problem with copying files under 3 G in size. At least I did not.

UPDATE: I've just tried copying the same file to and from a 32-bit system with a standard 2.6.31-16 kernel. No speed drop. The overall speed is slower (it is an old Asus A3h) and the transfer rate stays at 15 Mb/sec after initial 21 Mb/sec and does not drop.

I guess, when I will be switching to Lucid, I will also switch to a 32-bit system.

---

### Post by OpenSourceOfAwesomeness on 2009-12-31
Yeah same issues here. Some guys in another thread said they were actually having issues with their usb mouse and keyboards. thankfully i'm ok in that department, but my data transfer rates are crazy slow.

Copying to and from my external HD - usb 2.0 - is noticeably slower than windows. And copying music to my droid phone is ridiculous, < 500 KB/s

I remember thinking that jaunty was slower than windows, but I don't think it was this bad.

Anyone have any ideas?

---

### Post by G4MAC on 2010-01-06
I am having the same issue as everyone else, I have a 1TB external and I keep movies and stuff on it.  When I transfer anything to it, it starts off between 10MB/s and 20MB/s and quickly drops to about 2MB/s.

---

### Post by StuartN on 2010-01-06
> **G4MAC said:**
> it starts off between 10MB/s and 20MB/s and quickly drops to about 2MB/s.

If you run dmesg in a terminal, is there any warning or error related to the USB transfer?

@Myxb: I doubt switching from 64 to 32 bit would fix the problem, but try booting with the 32-bit Live CD and test your transfer rates.

---

### Post by bhishan on 2010-01-06
> **StuartN said:**
> If you run dmesg in a terminal, is there any warning or error related to the USB transfer?

I do not see any error message.

---

### Post by HeadHunter00 on 2010-01-08
Never mind me. Just ignore this post.

---

### Post by HeadHunter00 on 2010-01-09
> **danastasio said:**
> What file system are you all using? I know that ext4 works just fine for me. so does XFS and JFS (though JFS deleted my entire home folder after a power failure...)
Note: ext4 is fast overall. but xfs is only useful in transferring big files. a folder that takes up a lot of space doesn't count as a huge file. jfs is very unstable. so, use ext4.

---

### Post by bhishan on 2010-01-09
> **danastasio said:**
> What file system are you all using? I know that ext4 works just fine for me. so does XFS and JFS (though JFS deleted my entire home folder after a power failure...)

I was using ext4 in Jaunty and am also using ext4 in Karmic. There was no problem in Jaunty but is a pain in Karmic.

---

### Post by MidBSD on 2010-01-10
Some more info - After reading someone's response about using the shell to copy files, this does seem to work for me but during testing I noticed something.

When a file first transfers, latency shoots all the way up (this we know). The space on the USB device is allocated out piece by piece until it looks as if it's all done BUT the latency stays maxed out for a long while after.

This was the case for a 550MB file which appeared to finish but hung for over 30 seconds before the cp command finally freed up.

Between the time that the space finished allocating and the UI freeing up was about 30 seconds and in all that time, not one more byte was written to the USB device.

---

### Post by djmarty on 2010-01-11
I have had this "slow copy/move to/from USB" for many previous versions of Kubuntu and it persists for me in Karmic.  I also get the same very slow to copy from CD or DVD to HDD in Kubuntu.

For me using a different file manager or using command line makes no difference, the copy always starts fast (15-20Mbps) then slows to a crawl - sometimes stalling altogether.
 
However, I have another machine with XBMC installed.  On it the same slow to a crawl file copy (or move) happens using (K)Ubuntu (same in both gnome and kde) but if I use the file manager in XBMC the copy or move zooms along at 15-22Mbps or there abouts and stays at that speed.

Why it is fast using XBMC I have no idea but maybe this will give someone else a clue on how to fix this issue.  It is very frustrating.

---

### Post by nhasian on 2010-01-12
I can confirm the same problem running karmic 64bit with the 2.6.31 kernel.  yesterday i installed the 2.6.33RC3 kernel and the USB file transfer problems disappeared.

> **Myxb said:**
> I have had the speed problem with my 120G external USB hard drive. Everything I tried (cp, Nautilus, rsync, mc, remounting with 'async') resulted in a peak initial speed of up to 43 Mb/sec with a later drop to about 2-3 Mb/s. I copied a 31G file. The "crawling" part of the copying started on, roughly, the 2nd G. Also the 'system load' would max out until the system would lose much of its responsiveness.

Then installed the 'mainline' kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.2/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.2/) and this disgrace of a speed is gone!

Now the speed looks roughly as this. It starts with ~21 Mb/s then grows to about 40 Mb/s. Then it drops slowly to about 20-23 Mb/s and stays at that level. Actually is continues to drop, but it is probably due to the target drive geometry (?). The actual speed dropped from 23.6 Mb/s at 10% to 19.5 Mb/s at 100% of the 31G file. The 'system load' as seen in gnome system monitor would not grow and stays here on 2-2.16 points.

So the problem is the Ubuntu 2.6.31 kernel itself, in the 2.6.32.2 the problem is gone.

Hope this will help.

---

### Post by detroit/zero on 2010-01-12
Do you guys even glance at any of the old threads on this issue before you tap out these replies?

It's not the kernel. Even if putting a new kernel happens to work for you, it doesn't work for everyone, and that means that the kernel isn't the problem and changing it isn't a fix.

Back when the issue hit the big time with 2.6.24-16, there were people saying that, "2.6.26 is the fix".

Unfortunately, USB2.0 transfer speed issues date all the way back to the introduction of USB2.0 and kernel 2.4.xx

If you want to see a real change in how your USB device performs, change your default I/O scheduler in the boot string in GRUB. Alternatively, ditch the Ubuntu kernels altogether and build your own kernel with packages from kernel.org

---

### Post by bhishan on 2010-01-12
> **detroit/zero said:**
> Do you guys even glance at any of the old threads on this issue before you tap out these replies?

It's not the kernel. Even if putting a new kernel happens to work for you, it doesn't work for everyone, and that means that the kernel isn't the problem and changing it isn't a fix.

Back when the issue hit the big time with 2.6.24-16, there were people saying that, "2.6.26 is the fix".

Unfortunately, USB2.0 transfer speed issues date all the way back to the introduction of USB2.0 and kernel 2.4.xx

If you want to see a real change in how your USB device performs, change your default I/O scheduler in the boot string in GRUB. Alternatively, ditch the Ubuntu kernels altogether and build your own kernel with packages from kernel.org

But it was perfectly fine with Jaunty in this same computer. I could not find any solutions in any old threads. Can you post some links please.

---

### Post by mantaor on 2010-01-13
Hi guy, I have 9.10 recently updated. I have the same problem like all of you (with Win, usual transfer rate; with ubuntu 9.10 slow transfer rate). With lpci command, I have:

lpci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)

It's a very strange situation because I have 4 2.0 e 1.1. I think we need a serious fix from ubuntu developer and I hope quickly because this problem impacts a lot of people in a very common and stupid action. But if anyone has a solution.... a beer:D

I used 8Gb pendrive Kingston DT mini slim, under win 22Mb read / 14Mb write

---

### Post by stevenmansour on 2010-01-14
Same problem here, Karmic 64-bit on a Thinkpad T500, high-quality Lexar 32Gb USB drive. Transferring a 1gb file is very fast for the first 500mb, and then slows to a crawl for the rest of the time.

---

### Post by Cklein on 2010-01-15
Same problem with a Kingston DataTraveler 16GB. I haven't tried before Karmic. In windows it works perfect. Disabling the 'USB legacy' compatibility at the BIOS doesn't help. Putting the line pci=acpi at grub doesn't help.
I'm thinking about formatting the usb using linux and filesystem fat32, as it is now, but changing some of the mkfs.vfat options to change the sectors-per-cluster or any other parameter...

---

### Post by mantaor on 2010-01-15
New situation: if I boot with pendrive already connected, speed is correct like Win :confused:

---

### Post by tuberculo on 2010-01-28
elevator=noop is better for me. Not perfect, but better.

---

### Post by no2498 on 2010-01-28
ok i did not read a thing 
but was having a slow webcam on usb
just started like 2 weeks ago
think  what did i do
i had plunged in a diff cam an un mounted it
2 3 days later try webcam .7 fps not good was at 10 fps
ok today unplug webcam
plug in card reader with card in it
restart computer
card reader come up ok close  fspot unmount card reader
plug in webcam ok 10 fps not .7
usb's are working now
it looks like its in the unmount 
??????????????????
can any 1 help

---

### Post by GuiGuy on 2010-02-03
> **no2498 said:**
> 
can any 1 help

As I sit here near my MythTV media center telling me it will take 6 hours to copy a 1.5G file to a USB stick, it occurs to me that the solution has been around for awhile. 

It's called Windows ;)

---

### Post by mantaor on 2010-02-15
This is the third time I have to write for this problem. Is it possibile that any administrator or ubuntu developer can't reply us? A lot of people has more than 2 pendrives, it's incredible! Are we alone in this world? :p I kid but it's a pity.

---

### Post by ljpp on 2010-02-15
+1 from here.

Karmic 64bit in a brand new ASUS Pundit P5N9300 and a SanDisk Cruzer USB pen drive. I mainly use it to copy some [AVCHD videos to PS3]("http://http://www.bitburners.com/articles/guides/convert-mkv-to-avchd-for-ps3-using-linux/4460/") for playback, and I just noticed the slow speed when copying a file of approx 1GB.

After the first few hundred megs go flying, but then the file transfer somewhat stalls and becomes abnormally slow.

Clearly something is wrong here - the pen drive performs way faster in Windows. I also have a 320GB Western Digital MyBook USB HD, and the performance is fine.

---

### Post by Linuxforall on 2010-02-17
Turn off usb legacy mode in BIOS if its enabled, most likely you are transferring at usb 1.1 rates.

---

### Post by ljpp on 2010-02-17
> **Linuxforall said:**
> Turn off usb legacy mode in BIOS if its enabled, most likely you are transferring at usb 1.1 rates.

Hardly, if an external HD can transfer 20-30MB/s. Also legacy support is quite essential if you have a wireless keyboard and grub.

---

### Post by GuiGuy on 2010-02-17
> **Linuxforall said:**
> Turn off usb legacy mode in BIOS if its enabled, most likely you are transferring at usb 1.1 rates.

Hah! Even slower when off... :(

---

### Post by bek on 2010-02-22
I have the same problems, today tried to copy 250 MB from desktop to external hard drive Seagate, very slow, very slow,

---

### Post by ljpp on 2010-02-22
> **ljpp said:**
> Karmic 64bit in a brand new ASUS Pundit P5N9300 and a SanDisk Cruzer USB pen drive. I mainly use it to copy some [AVCHD videos to PS3]("http://http://www.bitburners.com/articles/guides/convert-mkv-to-avchd-for-ps3-using-linux/4460/") for playback, and I just noticed the slow speed when copying a file of approx 1GB.

I am just copying, or rather trying to do that, a 4gig AVCHD to the Sandisk Cruzer. The behavior is really strange - file operation stalled, showing 600+ kb/sec and some 1h30min left to copy.

I opened the stick with nautilus to have a look how it progresses, and came back - now it seems to be recovering as speed goes up and time down.

---

### Post by Tarkim on 2010-02-22
Same issue here. When I try to transfer files into my simple 1 gb mp3 player, things go very fast at first, then everything stops. 

I really like Ubuntu system and crawling back to Win is not an option. But I tried everything I've read at this topic and nothing helped. One big MINUS to Ubuntu.

---

### Post by Ctulhu on 2010-02-22
Same problem here with 9.10 on a 64 bity system. I think, however, it makes a difference what size the target drive is compared to what file size I'm moving. Transfer of a 1.7GB movie to a 2GB drive is pathetically slow for what claims to be a serious alternative to Windoze, but moving it to my my 1TB external hard drive seems to be faster. Anyway, this HAS to be fixed if Ubuntu claims to be a serious OS

---

### Post by Tarkim on 2010-02-23
Found out that if I copy one song at the time, it jumps into an mp3 player almost immediately. Well, still lame, but better then anything...

---

### Post by GuiGuy on 2010-02-23
> **Tarkim said:**
> Found out that if I copy one song at the time, it jumps into an mp3 player almost immediately. Well, still lame, but better then anything...

hmmm... does that include the time to unmount the USB drive?

---

### Post by Tarkim on 2010-02-23
It does. I've managed to fill my player carefully song by song (it took some time though:)) and unmounted it with no problem. Maybe it's my lucky day. :)

Folder transfer still not possible.

---

### Post by Healey on 2010-03-03
Hi

I dont know if it will help any one but I too had very slow data transfer to USB devices. 

It was odd that the problem only started happening after I put a new graphics card in which meant that I had to make some changes in BIOS (It was all ok with the old graphics card !!)

I was unable to find a solution that I could understand so as a last resort I decided to clear the CMOS using CLR_CMOS pins on the motherboard.(After detaching the mains lead)

I then set up the correct date and time and the boot sequence I required and now it works ok.  

I only hope the problem does not come back

Hope it helps

Healey

---

### Post by GuiGuy on 2010-03-05
I'm starting to think this may actually be a file system format issue. To explain;

I have been plagued by slow USB performance for a couple of years now to the point that I am continuously thinking of dropping Linux and going back to Windows. I'll stop my rant here other than to say that it is a pathetic situation when that most common of modern computer devices, the USB2 device, cannot be used to advantage on a Linux (Ubuntu) computer. 

**Anyway, I recently reformatted a couple of portable USB/eSATA HDDs from NTFS to EXT4. Transfer rates from the (Ubuntu) PC to the portable device using either USB or eSATA is right up there where I expect to be.  **   

Just now I had to transfer a bunch of video files from the server to a  NTFS formatted HDD in an eSATA docking station. I had about 20 x 2G files to transfer. It started off OK but then rapidly slowed down. It's telling me the transfer will complete in "days"!!??

OK, so I ripped out the NTFS drive and stuck an EXT4 drive in. I tried the transfer again. Now it was going to take minutes, not days.

I put the NTFS back, tried the transfer again and we're back to several days!

So, given I can consistently demonstrate the problem at least now I know the cause. But I suppose it's unlikely that anyone gives a tinker's curse anymore given we've had to put up with this so long. 

Finally, since I do have to transfer these files to an NTFS formatted HDD I guess I'll just have to find a Windows machine so I can copy the files from the server to the HDD that way. Thankfully I have a Gigabit network <sigh>.

Cheers

---

### Post by ljpp on 2010-03-06
> **GuiGuy said:**
> **Anyway, I recently reformatted a couple of portable USB/eSATA HDDs from NTFS to EXT4. Transfer rates from the (Ubuntu) PC to the portable device using either USB or eSATA is right up there where I expect to be.  **

Well, I am suffering from the USB performance issues with a SanDisk Cruzer pen drive, but my WD LifeBook 320GB is formatted to NTFS and it has, in my opinion, reasonable transfer rates of around 20-30MB/s.

---

### Post by StuartN on 2010-03-06
> **ljpp said:**
> Well, I am suffering from the USB performance issues with a SanDisk Cruzer pen drive, but my WD LifeBook 320GB is formatted to NTFS and it has, in my opinion, reasonable transfer rates of around 20-30MB/s.

I gave up on the SanDisk Cruzer and have perfectly acceptable performance with a range of devices including Iomega, Maxell and various unbranded / unknown brand pendrives. The inbuilt Windows-only password hardware makes the SanDisk devices unusable.

---

### Post by detroit/zero on 2010-03-06
I'm not going to call you a liar, but those are statements are pretty well unfounded.

It's not the make or model of USB device. I have several SanDisk thumbdrives - some FAT32, some EXT3, and some NTFS - they all perform well below expectations. So do my Toshiba drives, my Kingstons, and my Iomegas. Sandisk drives can be easily reformatted to whatever filesystem you choose, and the CDFS partition that contains the SanDisk U3 software is not a permanent part of the drive.

The file system does play a role, only insofar as NTFS support in Linux is pretty bad these days. Stick with FAT32 for cross-platform access, or go with EXT2 or 3 for Linux-only usage unless you want to install Ext2IFS or EXT2FSD on your Windows computers.
[URL="http://ubuntuforums.org/showpost.php?p=8124833&postcount=294"]
If you want a USB transfer performance gain, try changing the kernel I/O scheduler.[/URL] You can do it on a per-device basis to test which works best for you, and you can make it a system wide change if/when you find one you like.

I don't mean to sound harsh, but I've been in the middle of threads named "USB Transfers Too Slow in {Hardy|Intrepid|Jaunty|Karmic}" since Summer of 2008, and it kind of burns my britches to see people re-hashing the same tired and false theories of what does what and why it does it. And then, here you are telling someone that SanDisk drives are this and that, when I have several of them and know from first hand experience that they work fine. 

It's not Nautilus. It's not GVFS. It's not a sync/async mount option. Legacy USB support in your BIOS doesn't make a difference. It has nothing to do with ehci/uhci/ahci modules. Changing kernels won't make a difference, unless you compile with a different I/O scheduler.

Before anybody comes in here half-cocked talking about "this is why it's working like this", I would suggest doing a little research and reading up on what you're telling people. You might want to start with reading this very thread from the beginning, where you'll see [my post from December 13th]("http://ubuntuforums.org/showpost.php?p=8488429&postcount=25") where I highlight an [earlier post in a different thread]("http://ubuntuforums.org/showpost.php?p=8010056&postcount=270") from a couple months before.

---

### Post by StuartN on 2010-03-07
> **detroit/zero said:**
> It's not the make or model of USB device. I have several SanDisk thumbdrives - some FAT32, some EXT3, and some NTFS - they all perform well below expectations.

I was responding to ljpp's specific issue with a Sandisk Cruzer. The Sandisk Cruzer range contain U3 hardware that presents as a separate USB device causing severe slowdowns and file failures (whatever filesystem is used) for some hardware configurations that handle other brands and other Sandisk ranges without any issue. Removing the U3 driver ([http://kb.sandisk.com/app/answers/detail/a_id/2550](http://kb.sandisk.com/app/answers/detail/a_id/2550)) does not prevent these slowdowns and failures.

---

### Post by detroit/zero on 2010-03-07
> **StuartN said:**
> I was responding to ljpp's specific issue with a Sandisk Cruzer. The Sandisk Cruzer range contain U3 hardware that presents as a separate USB device causing severe slowdowns and file failures (whatever filesystem is used) for some hardware configurations that handle other brands and other Sandisk ranges without any issue. Removing the U3 driver ([http://kb.sandisk.com/app/answers/detail/a_id/2550](http://kb.sandisk.com/app/answers/detail/a_id/2550)) does not prevent these slowdowns and failures.
So, I guess that's for all the SanDisk Cruzers in the world except for the few I have. Is that what you're telling me? I have four SanDisk Cruzers, of varying sizes, bought over a span of 3.5 years, and I only ever removed the U3 software on one of them. Even on that one, I installed the PortableApps start-menu thingy and it still works fine on Linux and in Windows.

What is that link supposed to prove? I know how to remove U3 software - with Gparted. Where does it say anything about slowdowns or "file failures"? What, exactly, is a "file failure"?

You don't know what you're talking about, and you're giving people bad advice.

The U3 password protection bit is only a problem if the user has enabled password protection from the U3 preferences menu. If it's causing a problem in someone's Linux setup, it's as easy as rebooting to Windows (or even in a VM) and unsetting the password!

---

### Post by slumbergod on 2010-03-09
I just tried the anticipatory scheduler with my usb flash drive (/dev/sdb/) and experimented with the transfer of a 1.4Gb file. 

What I did NOT get was the stalling for ages that I get with the default cfq scheduler. So "Detroit" may indeed have found the culprit for the crappy transfer speeds.

What did NOT improve, however, was the transfer rate. It fluctuated all over the place between 1 and 7 Mb/s. So while it did indeed transfer the file faster, it was only because it didn't stall part way through as it usually does. 

I suppose you can argue this is an improvement but if I consider how much faster the same transfer is under Windoze (XP, Vista, & 7) then this is still an issue. So for now when I transfer multimedia presentations to a Windoze user's flash drive I'll have to continue using the apology: "Oh, sorry, but I use Linux and USB file transfer speeds are super crap in Linux :("

---

### Post by detroit/zero on 2010-03-09
> **slumbergod said:**
> I just tried the anticipatory scheduler with my usb flash drive (/dev/sdb/) and experimented with the transfer of a 1.4Gb file. 

What I did NOT get was the stalling for ages that I get with the default cfq scheduler. So "Detroit" may indeed have found the culprit for the crappy transfer speeds.

What did NOT improve, however, was the transfer rate. It fluctuated all over the place between 1 and 7 Mb/s. So while it did indeed transfer the file faster, it was only because it didn't stall part way through as it usually does. 

I suppose you can argue this is an improvement but if I consider how much faster the same transfer is under Windoze (XP, Vista, & 7) then this is still an issue. So for now when I transfer multimedia presentations to a Windoze user's flash drive I'll have to continue using the apology: "Oh, sorry, but I use Linux and USB file transfer speeds are super crap in Linux :("
Try the 'noop' scheduler. I've had my most noticeable results with that one, it's just been a while since I wrote that post and never updated it. Even 'deadline' has striking improvements over 'cfq', but you may notice a serious system wide performance hit while you're transferring.

Thing about all this is: CFQ has been the default I/O scheduler for a while now. I never had USB transfer problems until kernel 2.6.24-18 (along with headers & modules) came out for Hardy. So, I'm not entirely sure the scheduler is the culprit.

It seems to work, though, so whatever gets you by................

---

### Post by philinux on 2010-03-15
Ok this is a pain.

Only copying the .mozilla folder (120meg) to a 4gig usb stick. 

Starts of at 3.5 meg and stops then slows down to kbs/sec. Tried the remount thing but same result.

What is going on takes blooming ages.

---

### Post by nitstorm on 2010-03-15
I have the same problem too !!! I thought it was a hardware issue on my side but seems like a whole lotta people have this !! first it runs through the transfer and then slows down slower than a tortoise and takes ages to transfer stuff into my external HDD and everything else i connect by USB. A solution to this thread would be nice. Cheers fellas :)

---

### Post by philinux on 2010-03-15
> **nitstorm said:**
> I have the same problem too !!! I thought it was a hardware issue on my side but seems like a whole lotta people have this !! first it runs through the transfer and then slows down slower than a tortoise and takes ages to transfer stuff into my external HDD and everything else i connect by USB. A solution to this thread would be nice. Cheers fellas :)

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/197762?comments=all](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/197762?comments=all)

I tried adding elevator=noop and no change.

First 46 meg transfer in an instant then the transfer rate slows down from 3.5 Meg/sec continually to 500 KB/sec.

---

### Post by slumbergod on 2010-03-18
Nope, no noticeable difference with the other schedulers. So far changing the scheduler is the only thing that has actually made an appreciable difference even if performance is still not what it should be.

Actually, just today transferring directories with lots of small multimedia files failed. I wasn't able to unmount successfully on two attempts. It seems like my laptop+ubuntu hates Kingston 8Gb flash drives because this is not the first time for these drives.

I love linux but I really find USB a disaster. I hope USB 3.0 won't be plagued with all these issues.

[update] it doesn't really matter whether you use noop or anticipatory, either are faster than the the default because they don't lock up or hang in the same way. So with this in mind it is the best solution we have for now. Not entirely acceptable but that is one of the negatives of open source - it can take for ever to get a non-critical issue resolved. Others should try these and post feedback too. One day we might even get USB fixed.

---

### Post by roachkazy on 2010-03-27
Same problem here, it starts off faster then can be and then slows to a fraction of that speed.

Has anyone come up with anything to solve this problem?

---

### Post by GuiGuy on 2010-03-27
> **roachkazy said:**
> Same problem here, it starts off faster then can be and then slows to a fraction of that speed.

Has anyone come up with anything to solve this problem?

Yea, it's called windows. Whenever I need to copy large or many files to a USB device from a Ubuntu PC I connect to it via Windows and to the USB transfer across the network. At least that way I get a consistent and reasonable speed. 

It really is a shameful situation that this hasn't been given the highest priority on the "must fix" list. 

PS: I forgot, the transfer across the network works well on my daughter's MacBook as well ;)

Cheers

---

### Post by nhasian on 2010-03-27
I think its just a problem with the older Linux 2.6.31 kernel (default kernel in karmic).  I've resolved the problem on my system when i was using karmic by using the Linux 2.6.33 kernel.  Since then I've upgraded to Ubuntu 10.04 Lucid Lynx Beta1 and I still have fast USB transfer speeds with the default 2.6.32 kernel in Lucid.

---

### Post by GuiGuy on 2010-03-27
> **nhasian said:**
> I think its just a problem with the older Linux 2.6.31 kernel (default kernel in karmic).  I've resolved the problem on my system when i was using karmic by using the Linux 2.6.33 kernel.  Since then I've upgraded to Ubuntu 10.04 Lucid Lynx Beta1 and I still have fast USB transfer speeds with the default 2.6.32 kernel in Lucid.

It's been two years since this problem began for me. On every kernel re-incarnation I say to myself, maybe this time. 

We live in hope...

---

### Post by robertm43 on 2010-04-05
Thanks for posting this..a great help and solved the issue of slow usb transfer and playback of video in vlc.Very pleased

---

### Post by drewsus on 2010-05-01
> **nhasian said:**
> I think its just a problem with the older Linux 2.6.31 kernel (default kernel in karmic).  I've resolved the problem on my system when i was using karmic by using the Linux 2.6.33 kernel.  Since then I've upgraded to Ubuntu 10.04 Lucid Lynx Beta1 and I still have fast USB transfer speeds with the default 2.6.32 kernel in Lucid.

Im using 2.6.32 and my speeds are ~7mb/s

---

### Post by rsroxxx on 2010-05-01
I'm using 2.6.32 and my speeds(while copying from hd to pen drive) are less than 1mbps

It starts with 7mbps+, but eventually bites the dust..!
i've JUST started using ubuntu, n this is really irritating. i dont want to boot Win7 again n again just to copy files..!
Inspite of the fact that this forum has been very helpful to me, in learning a lot about ubuntu; Its a shame, that such an important issue has not been solved yet. :(

---

### Post by darkshines87 on 2010-05-01
Hi people!

I think it is really frustrating that a major operating system feature is not working properly. This issue has been around for a long time and there is no solution to this. I tried some random solutions but none did help. When I upgraded to Lucid, I hoped it would vanish, since it uses the more updated Kernel. But jokes on me! It didn't help a bit. I just got this really really fast USB Stick and the packaging says it can read up to 30 Mbps and with my test on Ubuntu it does even write with 30 Mbps, but just for 10 seconds. Then it drops to 1 Mbps. That is just not fair ](*,)

Next thing I am gonna participate whining at launchpad :D :D

Greets, Darkshines

---

### Post by GuiGuy on 2010-05-04
> **darkshines87 said:**
> I think it is really frustrating that a major operating system feature is not working properly. This issue has been around for a long time and there is no solution to this. I tried some random solutions but none did help. When I upgraded to Lucid, I hoped it would vanish, since it uses the more updated Kernel. But jokes on me! It didn't help a bit. I just got this really really fast USB Stick and the packaging says it can read up to 30 Mbps and with my test on Ubuntu it does even write with 30 Mbps, but just for 10 seconds. Then it drops to 1 Mbps. That is just not fair ](*,)


I can confirm that the problem continues with Lucid. It is a shameful travesty. 

NB: I am looking at 27 hours to copy a 1.4G file!!??

---

### Post by roguetoad on 2010-05-05
Upgraded to Lucid but still plagued with slow USB speeds on my external USB HDD as well. Tried the noop and deadline schedulers and remounting with async and noatime options. Didn't change the overall transfer rate. Changing these changed the initial burst of speed I get on starting a transfer, but over time the speed quickly decreased to the same rate (for me about ~9.8MB/s in Lucid compared with 3.9MB/s in Karmic) as default. 

I also tried this on the 2.6.33 kernel from the kernel ppa. Still no dice. Behaves the same

---

### Post by drewsus on 2010-05-11
> **nhasian said:**
> I think its just a problem with the older Linux 2.6.31 kernel (default kernel in karmic).  I've resolved the problem on my system when i was using karmic by using the Linux 2.6.33 kernel.  Since then I've upgraded to Ubuntu 10.04 Lucid Lynx Beta1 and I still have fast USB transfer speeds with the default 2.6.32 kernel in Lucid.

How do you safely upgrade the kernel in Karmic?

**update**: [http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/)

---

### Post by GuiGuy on 2010-05-11
> **nhasian said:**
> I think its just a problem with the older Linux 2.6.31 kernel (default kernel in karmic).  I've resolved the problem on my system when i was using karmic by using the Linux 2.6.33 kernel.  Since then I've upgraded to Ubuntu 10.04 Lucid Lynx Beta1 and I still have fast USB transfer speeds with the default 2.6.32 kernel in Lucid.


I'm running  2.6.32-22. It makes no difference. Any file xfer larger than 300 megabytes will slow to a crawl, generally taking hours to complete.

---

### Post by drewsus on 2010-05-11
I just updated to 2.6.32-22 and wow its so much SLOWER now. Speed is half it was before

---

### Post by svaens on 2010-05-19
very slow in lucid, update to date updates (as of may 2010). 
which is why I am here, looking for other sufferers. 

I get about 1 meg per second transfer.

---

### Post by pizza-is-good on 2010-05-19
My lucid works fine (64 bit).

My transfer to my cruzer 4GB (with U3 uninstalled) is an average of 7 MB/s, but peaks at 10 MB/s.

I personally think that is good. But for some of the comments on this thread, you guys are expecting these things to just copy instantly. It's not USB 3.0 yet.

I look forward to USB 3.0. I already have the kernel that supports it, all I now need is the hardware.:lolflag:

---

### Post by Failboat88 on 2010-05-24
I think I'm going to upgrade to 10.04 and see if it helps my transfers. I have mythbuntu 9.1 on another pc and it transfers fine. Maybe this has something to do with gnome 9.1.

---

### Post by drewsus on 2010-05-24
> **pizza-is-good said:**
> I personally think that is good. But for some of the comments on this thread, you guys are expecting these things to just copy instantly. It's not USB 3.0 yet.

Considering that on my same computer using the same ports and same external media I get speeds of 6-12MB/s using Lucid and speeds of 30+ MB/s using Windows I would say that is not good speeds. 

Im not asking to ride a Unicorn, Im asking for my hardware to perform. And it has performed in the past. And does with different software. And sure, 7-10 MB/s is 'good' if you are transferring a gig, but not if I am transferring 500+ GB.

---

### Post by Hated On Mostly on 2010-06-01
This is an old linux bug that no one cares to try to fix. There are bug reports on several distributions and the kernel itself going back years. I don't think anyone has even touched this problem. This bug made me switch to Windows 7. Slow USB transfers is unacceptable for me.

Some of you can try this guy's fix:

[http://ubuntuforums.org/showpost.php?p=8822080&postcount=157](http://ubuntuforums.org/showpost.php?p=8822080&postcount=157)

> **MGR1 said:**
> Amazing! It works! 

```
 pci=routeirq elevator=as
```The above as kernel parameters did the trick on a HP/Compaq NX8220 running Ubuntu 8.10. Transfer speed with a Sandisk Cruzer 8GB now reaches 16-20 MB/s, tested with a 560MB sized file. Previously the speed started around 6MB/s and slowed down to 1MB/s or virtually halted after 100MB had been transferred.

Hope it works for some of you. I have never tried it. Switched to Windows before he posted it and won't come back until the slow usb bug is fixed once and for all. Given that the bug has been around and ignored for several years I will probably have to wait until USB 3.0 becomes standard on hardware before using linux outside of a virtual machine. Assuming there are no problems with USB 3.0 transfers that is...

---

### Post by Hated On Mostly on 2010-06-02
The other thing you can try as a workaround is to use a powered USB hub. In one of the many bug reports, users reported getting normal USB 2.0 transfer speeds when connecting devices to a powered USB hub.

---

### Post by AintJoe on 2010-06-07
Just tried setting to the anticipatory scheduler in 10.04, and it hasn't helped at all.

My issue might be a little different. It appears to get to about 300MB, then pauses then goes another 300MB or so, and then a longer pause, and so on. 

This makes me think there is some buffer that is filling up at ~300MB. I've seen other people post this issue and complaining of other sizes around 100MB.

---

### Post by philinux on 2010-06-07
> **pizza-is-good said:**
> My lucid works fine (64 bit).

My transfer to my cruzer 4GB (with U3 uninstalled) is an average of 7 MB/s, but peaks at 10 MB/s.

I personally think that is good. But for some of the comments on this thread, **you guys are expecting these things to just copy instantly**. It's not USB 3.0 yet.

Err. No, just consistent speeds.

Copying say 600MB it starts at about 6MB/s but then slows down to a crawl of less that 100KB/sec. See post #3

[edit] looks like the mainline kernel is a good workaround.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by darkshines87 on 2010-06-07
philinux: What does that mean "Mainline kernel"? I followed that link and there were tons of kernel versions. Which one should I install, so the issue is solved? 

Furthermore I noticed something funny: Whenever I start copying a 4 Gig file to my USB flash drive, my memory slowly fills up to 100%. As soon as it hits the limit (I have 4 gigs of RAM.. unbelievable it can be full..) it has copied around 500 MB and the speed drops to 100 KB/s. Why, linux kernel, why do you hate me?

Anyway, if this "mainline" kernel works, be glad to install. I am just concerned that my fglrx driver won't work any more.

---

### Post by philinux on 2010-06-08
> **darkshines87 said:**
> philinux: What does that mean "Mainline kernel"? I followed that link and there were tons of kernel versions. Which one should I install, so the issue is solved? 

Furthermore I noticed something funny: Whenever I start copying a 4 Gig file to my USB flash drive, my memory slowly fills up to 100%. As soon as it hits the limit (I have 4 gigs of RAM.. unbelievable it can be full..) it has copied around 500 MB and the speed drops to 100 KB/s. Why, linux kernel, why do you hate me?

Anyway, if this "mainline" kernel works, be glad to install. I am just concerned that my fglrx driver won't work any more.

You'd pick the latest for your release. Stable then not rc's. I've not tried this yet.
Just been experimenting in Maverick which has the 2.6.35-1 ubuntu kernel.
Transferring 1 gig starts of at 12MB/sec then after about 250MB transferred slows down to 2.2MB/sec.

I've raised a new bug report. If someone could confirm it for me.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/591174](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/591174)

---

### Post by philinux on 2010-06-08
No need to confirm it's been triaged and set to medium. Guess it's gonna get some attention now hopefully.

---

### Post by sille777 on 2010-06-16
I too am suffering from Slow usb Transfers.

I benchmarked my thumb drive and attached screen-shot.
Also included a screen-shot of the drive info showing it supports usb2.0.
It shows as unknown and no partition so i could run the benchmarks. I will want to have a fat16 or fat32 file-system later for cross platform compatibility.


I don't know how to change "schedulers" So I haven't tried that.

output from "lsusb"

Bus 003 Device 002: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 017: ID 154b:6545 PNY 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Output from "lspci"

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
05:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller




I hope there is something I can do to fix this.  I'm a newbie still to linux and ubuntu.

---

### Post by GuiGuy on 2010-06-20
Just came across this

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541937](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541937)

Interesting (and encouraging NOT) that the status is "undecided"

Jeezzz....

---

### Post by LakesideLoafer on 2010-06-20
After reading one of the earlier replies to this thread I restarted with my USB pen drive already plugged in and the behaviour is totally different. I can now read from the drive at around 45 MB/sec.

Writing to the drive is at 2.7 MB/sec but is steady at this rate when previously it would write around 100 MB almost instantaneously and then hang for up to 30 seconds.

Having just shelled out for an external hard drive I am hoping that this is solved soon.

---

### Post by bhishan on 2010-06-21
> **GuiGuy said:**
> Just came across this

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541937](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541937)

Interesting (and encouraging NOT) that the status is "undecided"

Jeezzz....

Freaking ridiculous!

---

### Post by LakesideLoafer on 2010-06-30
Stranger and stranger - new external hard drive connected by the same USB slot achieves speeds of 18MB/s with no slow down whatsoever even on large transfers.

---

### Post by GuiGuy on 2010-06-30
> **LakesideLoafer said:**
> Stranger and stranger - new external hard drive connected by the same USB slot achieves speeds of 18MB/s with no slow down whatsoever even on large transfers.

I have also noticed that a recently purchased WD 320G external (USB Powered) HDD works fine with good transfer speeds.

However, with 16G and 32G flash memory sticks becoming fairly common, the situation remains extremely unsatisfying. If I have large files to copy to these devices I need to find a Windows or Apple computer.

---

### Post by dnguyen1963 on 2010-06-30
> **mantaor said:**
> This is the third time I have to write for this problem. Is it possibile that any administrator or ubuntu developer can't reply us? A lot of people has more than 2 pendrives, it's incredible! Are we alone in this world? :p I kid but it's a pity.

Goto Ubuntu.com and post your questions on Launchpad.  Developers do not answer questions posted in this forums.

---

### Post by GuiGuy on 2010-06-30
> **dnguyen1963 said:**
> Goto Ubuntu.com and post your questions on Launchpad.  Developers do not answer questions posted in this forums.

Good luck with that. I mean, this "bug" has been around for nearly three years, there are a number of complaints about it on launchpad, yet nothing seems to be done about it. My understanding is that it has been given a low priority. Unbe -effing- lievable,

---

### Post by darkshines87 on 2010-07-01
So there I was, minding my own business and a kernel update came along!

But, after a quick test it proved that 2.6.32-23 didn't change anything. What a pity. It is unbelievable that no one fixes this. Copying big files to a thumb drive is a common use case or am I out of my mind?

---

### Post by dnguyen1963 on 2010-07-01
> **GuiGuy said:**
> Good luck with that. I mean, this "bug" has been around for nearly three years, there are a number of complaints about it on launchpad, yet nothing seems to be done about it. My understanding is that it has been given a low priority. Unbe -effing- lievable,

Well, with any free software based on a community approach, we are at the mercy of the developers.  If you are into programming, this problem is not fanciful enough to deserve their attention.  Just think about all of the random freezes that many of us are experiencing with 10.04 LTS and, yet, not a whisper from any of the developers in this forum.  I did receive some responses from Launchpad regarding the freeze problem and that was why I suggested that we should post our questions there.

---

### Post by Ub28 on 2010-08-03
I'm having the same problem here.  I copy a folder with lots of files over to my USB pendrive, it starts off fast then slows down so much it almost stops!  Sometimes it will speed up again, then slow right down.

Has anyone created a bug report?

I'm using Ubuntu 10.04 Lucid 64-bit.

---

### Post by GuiGuy on 2010-08-03
> **Ub28 said:**
> 
Has anyone created a bug report?

The problem has been around for at least 2 years now. There are bug reports but those who might have the skills to fix it don't seem the slightest bit interested.

---

### Post by philinux on 2010-08-03
> **Ub28 said:**
> I'm having the same problem here.  I copy a folder with lots of files over to my USB pendrive, it starts off fast then slows down so much it almost stops!  Sometimes it will speed up again, then slow right down.

**Has anyone created a bug report**?

I'm using Ubuntu 10.04 Lucid 64-bit.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/591174](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/591174)

Don't post a me too comment instead click the This Bug Affects Me.

---

### Post by bhishan on 2010-08-03
Still unassigned :(

---

### Post by StuartN on 2010-08-04
> **Ub28 said:**
> I'm having the same problem here.  I copy a folder with lots of files over to my USB pendrive, it starts off fast then slows down so much it almost stops!  Sometimes it will speed up again, then slow right down.

I tried a large number of these objects and found Maxell devices work fine with my laptops, Sandisk Cruzer are terrible, some others were intermediate. All of them function faultlessly in my desktops, and in Macs. Find a model that works for you.

You can add another USB controller in a desktop, which will probably not be affected.

---

### Post by dacookiemonn on 2010-08-08
ya this is ridiculous.
My issue seems a little diff tho.

Say i have a 700mb file, if i copy the 700mb file to 8Gb sandisk cruzer, it is amazingly fast, takes liek 2 seconds it seems to get to the end, liek 98%-99% with only 5-10mb left, then it just sits there.

Sometimes it will finish up and the transfer window closes, but i can see my usb light still flashing.  It keeps on flashing.  So when i unmount or eject it says somethis is something hign liek writing data to prevent filelosss or something liek that, and it will sit there all night if i let it.

When i cancel and remove the usb, and put back in, the entire file seems to be there, but its not, its missing parts.

I got so mad and accused my ubuntu of acting liek windows, but i found it so much faster to reboot into windows7 (dualboot), copy the file which still seems liek 4mb/sec it way to slow, but it copies, and when it reaches the end it actually is copied.

this is something important for me, and just this alone almsot has me going back to using windows, which is pretty dang sad.

This is on 64bit 10.04, on 9.04 it works perfect and liek 2-3 seconds a 700 mb file is copied.  And it seems liek when i first installed 10.04 , a new install it worked, then all of a sudden it wants to screw me around.

Its not just my brand either, it does this on usb sandisk, and a kodak usb i got, 4gb and 8gb, it does it on sd card plugged right into my card reader built into the laptop, 2gb and 4 gb, but does not do this on a 250gb external One-click external hard drive.

and its not so much lack of experience, ive been using ubuntu since 7.xx days, and i can setup my own php and stuiff from svn sources, so i dont think its me.  It only works right when my file im copying is liek 5-10Mb, anythign bigger just acts liek it dont knwo what to do.

I really hate when windows starts to do simple task much faster than ubuntu, this is a very very sad thing and needs attention.

Also does this with any file manager i use, nautilus, and even in terminal using cp with and without root.

Im at a complete loss and i really really hate having to reboot into windows for somethign so simple.  if i dont, my file will nto get copied.  I left it alone for over 3 hours one time and nothin but a corrupt file.  Ubuntu is gonna loose some ground if this is not addressed, becasue one of my buddies that i talked into using ubuntu has same prob, so he just went back to windows for now until its fixed.

---

### Post by t.ebentheuer on 2010-08-08
Here is this noob's experience....

Copying large files or large groups of files with nautilus it will go very fast at first then suddenly slow to an absolute crawl, less than 1 MB/sec.  Just for craps n grins i downloaded the thunar file manager that comes with xfce and have been experimenting with that.  

Here is what I found: If I copy from my HD in a thunar window to my USB stick in a nautilus window, the rate stays consistent at about 4 MB per second, and if i copy within thunar it doesnt show the speed but it seems to be about the same speed judging by how long it takes.  

This is totally odd and makes no sense to me but it does do it.  Its enough of a difference that backing up 2.5 gigs of stuff was tolerable doing it that way whereas just using nautilus by itself was miserably slow.  This is on an asus k50 laptop with ubuntu 10.04 64 bit.  Something else i checked out, if you have a card reader, SD cards transferred at a solid 10MB a sec for me either direction.  Unfortunately mine is only 2 gigs so that was too small for what i need, but its somethin to consider.

---

### Post by bhishan on 2010-08-09
I have tried with more than a dozen USB sticks its the same problem. But works good with any external hard drive.

---

### Post by beharuko on 2010-08-13
i am running karmic koala kernel v. 2.6.31.14-generic. file transfer from usb to my hd is fine, but when its from my hd to usb of any brand, transfer starts at really fast then slows down..any ideas? I think its when i made some updates via update manager though i didn't test on a fresh install of karmic..

---

### Post by ffixcollector on 2010-09-25
I have the same problem here, any updates?

---

### Post by GuiGuy on 2010-10-01
> **ffixcollector said:**
> I have the same problem here, any updates?

Only to say that I am sitting here fuming that it's going to take 13 hours and 45 minutes to copy a 2G video file to a thumb drive. 

I'm looking around for a WindowsPC.

---

### Post by msakms on 2010-10-01
I had the exact same issue and it works like charm when you mount your drive with the async option.

---

### Post by GuiGuy on 2010-10-01
> **msakms said:**
> I had the exact same issue and it works like charm when you mount your drive with the async option.

So, mount the devices manually?

---

### Post by msakms on 2010-10-01
Yes, I always mount my external drive manually and currently I'm discussing that issue everywhere to figure out how to auto-mount drives with the async option. In other words, how to set async option as the default option.

---

### Post by GuiGuy on 2010-10-01
> **msakms said:**
> Yes, I always mount my external drive manually and currently I'm discussing that issue everywhere to figure out how to auto-mount drives with the async option. In other words, how to set async option as the default option.

OK, but that's not for me.

---

### Post by msakms on 2010-10-01
I've been looking everywhere on how to get over that issue and it seems there's no other way around except for the async option so, I'll appreciate any suggestion on how to solve the slow transfer speeds to thumb drives. 
cheers

---

### Post by GuiGuy on 2010-10-03
> **msakms said:**
>  I'll appreciate any suggestion on how to solve the slow transfer speeds to thumb drives. 

I used borrow my daughter's Macbook and copy files across the network. More recently I've installed a NAS device running gigabit ethernet. It has three USB ports. In a round about way it looks like solving my problem for now.

Nevertheless, it is shameful that this must essential of functions is not given a higher priority for a fix.

---

### Post by messie on 2010-10-24
Currently I also use the asynchronous mount to achieve a decent copy speed... however it does not alwayss work. I hope there will be some kind of solution some time soon.

---

### Post by ebramwells on 2010-10-29
It’s a shame this problem still exists. I run 64-bit maverick now after upgrading from jaunty to karmic to lucid to maverick, and even after all this time and generations of Ubuntu, still no fix. I’ve had many USB’s over the years and every one has been horrifically slow at transfers. Oh well...

---

### Post by mcmagostini on 2010-10-29
I think this problem might be more related to the USB controller on the motherboard
rather than to the USB drives per se, since not everyone experience it. 
I had it on an older machine, but on my actual workstation this doesn't happen. 
Quite bothersome, indeed.

---

### Post by SamsamTS on 2010-10-29
> **mcmagostini said:**
> I think this problem might be more related to the USB controller on the motherboard
rather than to the USB drives per se, since not everyone experience it.

Indeed. Although it is not the controller that have a problem but rather Ubuntu (or linux ? some other distributions seem to be affected too) with some controllers. I experienced this problem myself (and still do) writing data on an USB key works perfectly fine with Windows but with Ubuntu (actually Mint) it is just slow as hell.

One thing to note is that with my external USB HDD I have no problem so could it be a problem with flash memory ? I read that some have problem with SSD and SD cards. I also have a DVB-T key working perfectly. So maybe it's not all about USB ?

Of course i tried various solutions, changing the scheduler, mount the device with async, start the system with the key already plugged in and so on. Nothing worked.

---

### Post by mercier on 2010-10-29
the solution is not to use nautilus in gnome. i use double commander and have no problems any more.

to me it seems that it's nautilus' problem

---

### Post by bhishan on 2010-11-02
I recently installed ubuntu 10.10 32 bit. The problem still exists. The transfer rate started at 19mb/s and dropped down to 2mb/s when it was done transferring a 700mb file. The copying time was around 10 minutes i think.

---

### Post by Hated On Mostly on 2010-11-02
> **mercier said:**
> the solution is not to use nautilus in gnome. i use double commander and have no problems any more.

to me it seems that it's nautilus' problem

Is this true? Anybody have this problem using Kubuntu (KDE), Xubuntu (Xfce), or some other distribution that does not use the GNOME desktop environment with Nautilus?

---

### Post by Hated On Mostly on 2010-11-03
Never mind, went through some of the old links I posted and this problem has been reported with desktop environments other than GNOME. This bug is not limited to the GNOME DE.

I switched from Linux since this bug became a problem for me so I can't do any testing myself.

---

### Post by mixu75 on 2010-11-06
Has anyone tried installing KDE Dolphin file manager in Gnome?

I've had this freezing of copy process problem with both USB sticks and LAN hard drive. Today I've tried different file managers and "stress tests" in order to find a solution. Copying a file from the network drive while trying to play an avi file froze the copy process to a grinding halt with the regular Nautilus file manager. I've got Ubuntu Maverick installed, haven't installed the KDE desktop, though.

Right now I'm doing a stress test with Dolphin, and it seems that my 7,9 GB file is still being copied at the same transfer rate as when I started the process: no freezing.

I haven't tested USB stick yet, need to locate the actual sticks first :)

---

### Post by aa2k on 2010-11-07
Hi,

I am also having this problem, I have a file server that has a 2 usb external drives, I copy (scheduled) backup overnight to the usb drives, not much.. maybe 1 or 2 gigs every other day... it used to work perfectly under Ubuntu 10.04 but now that I upgraded to 10.10 it starts fast and then it becomes very sloooooow.. to copy a 1gb file it takes aprox. 4 hours... this is very annoying... i woke up in the morning and it still running...
I am using GNOME as the desktop. 64-bit
The copy is done from windows machines to a a share on the Ubuntu  machine (via shared USB drive attached), gegabit connection... like I  mentioned , perfect on Ubuntu 10.04, bad/slow on 10.10.

Any help would be appreciated.

Thanks!

EDIT: I found an interesting link, check this out:

[http://ubuntuforums.org/showpost.php?p=8124807&postcount=144](http://ubuntuforums.org/showpost.php?p=8124807&postcount=144)

---

### Post by bhishan on 2010-11-08
> **aa2k said:**
> 
EDIT: I found an interesting link, check this out:

[http://ubuntuforums.org/showpost.php?p=8124807&postcount=144](http://ubuntuforums.org/showpost.php?p=8124807&postcount=144)

Did it work for you?

---

### Post by mister_playboy on 2010-11-09
> **mixu75 said:**
> Has anyone tried installing KDE Dolphin file manager in Gnome?

Dolphin exhibits the exact same behavior.  I have encountered this bug on every Ubuntu install I have used.

---

### Post by mrsfixit on 2010-11-27
I am using Karmic on my laptops, and Lucid 10.04 64 bit on my desktop. I too am having the problem with slow transfer speeds- in this case to an 8 GB flash card.

I've tried reformatting the card in both Windows and Ubuntu, and it makes no difference.

However- I noticed something *very* interesting, and obviously this applies only to flash cards, not thumb drives.

When I start having issues with a card, I find that putting the card into my digital camera and having the camera do a low level format of the card will speed things up.

After doing this, the transfer speeds improve and transferring a 700 Mb file from the HDD to the card takes about 90 seconds, a 1.4 GB file take a little over 3 minutes. 

I can't explain why formatting the card in the camera should help, but I hope this info helps someone.

---

### Post by dcstar on 2010-11-27
Someone with this problem should try this and report back any changes:

[http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html](http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html)

---

### Post by Kevin B on 2010-11-28
I have had the same problems transferring to Flash Drives.
I have changed the I/O scheduler to Deadline to test the difference. At the same time I downloaded Gnome-Commander.

I found little difference with Deadline so I changed back to CFQ. Gmome_Commander did make  big difference for me though. So I now use Nautilus for all my normal directory work as I like the program, and I use commander just to transfer to Flash and SD.

Works for me, although I would like to see Ubuntu deal with this problem as the speeds I am getting are no where near Windows XP. I would hate for linux to start loosing people back to the Dark Side.

---

### Post by GuiGuy on 2010-11-29
I too am a long time sufferer of poor USB performance across a range of PC hardware. 

Today I bought my wife an early xmas present, a [Medion Akoya E7214]("http://www.pcworld.idg.com.au/review/notebooks/medion/akoya_e7214_md98410/359262"). 

I installed Kubuntu Maverick (64). 

Imagine my surprise; USB transfer speeds are blazingly fast across a range of devices. I have yet to find fault with it. 

So, maybe this USB thing is very, very hardware critical?

---

### Post by Robert Lutken on 2010-11-29
I have this problem as well, i find if i turn off internet activitys. close file browsers down it helps speed up, slightly however it is still very slow =/

---

### Post by Sylos on 2010-11-30
Another person experiencing this problem. Using Ubuntu 9.10 with USB 1 ports - starting transfer rate is around 8mb/s slowing down to 3mb/s or less.

Im gonna try and do some testing and post will post any results that look useful or interesting.

---

### Post by kirbyparufo on 2010-11-30
After a recent kernel update in 10.04, I've starting getting this problem too. Files  copy quickly to start, but after around 100 MB, things slow to a  complete crawl. I thought this was a problem with Nautilus at first, as  the problem didn't seem to happen until the file operations window  appeared, but I'm having the same problem in GNOME Commander.

---

### Post by Sylos on 2010-12-01
So ......
My flash drive continues slowing down from 8Mb to 3Mb when transfering files around 1.5g. I have tried this on Karmic, Lucid Studio, and KXStudio (with older and newer kernels) and it seems to always be the same.

I have also tried out transfering to to external WD HDD connected via usb and the rate is around 20Mb slowing slightly to 18/19Mb.

I also tried to copy the 1.5g file onto the flash drive using cli and the cp command. I waited for 10minutes and I still didnt have my prompt back (which I assume means its not finished) and then I gave up.

EDIT: I also tried transfering to another external HDD (Iomega) and got around 11mb/s. Wierd!

---

### Post by syborfical on 2010-12-03
I also have the same problem.

If there a way to force usb drives to mount and work at USB2 speeds?

Just about to upgrade to 10.10 ill report if i get the same bug in 10.10

---

### Post by lotharmat on 2010-12-12
Has there been any progress on this?

---

### Post by bhishan on 2010-12-12
> **lotharmat said:**
> Has there been any progress on this?

Not that I know of.

---

### Post by GuiGuy on 2010-12-18
> **lotharmat said:**
> Has there been any progress on this?

[S]Google's Chrome OS will arrive first...[/S]

Sorry, churlish post. Let's face it, the USB xfer has been around for years. Why should we retain any hope that it will ever be fixed.

Cheers

---

### Post by msakms on 2010-12-18
> **lotharmat said:**
> Has there been any progress on this?

Worked like a charm with all my USB drives and seems it ain't an issue anymore right after I upgraded to the 2.6.32-25-generic kernel......I didn't seem to find any info on that release regarding the transfer speeds thing. However, I'm glad anyway that it works now.
I'm wondering if this happened to someone else??

---

### Post by GuiGuy on 2010-12-18
> **msakms said:**
> Worked like a charm with all my USB drives and seems it ain't an issue anymore right after I upgraded to the 2.6.32-25-generic kernel......I didn't seem to find any info on that release regarding the transfer speeds thing. However, I'm glad anyway that it works now.
I'm wondering if this happened to someone else??

You should consider yourself lucky. For most the xfer of large files remains a task best done on windows. 

That said, my wife has a new Medion notebook PC and it works fine. The other six (Ubuntu) PCs I have access to do not.

PS: I'm running the same kernel on a range of PCs. It has made no difference. Transferring a large file, say 700M, the first 150M to 200M seem to transfer at blinding speed. Then it slows down progressively until, around 600M transferred, the speed is measured in kilobytes rather than megabytes. It's shameful.

---

### Post by ffixcollector on 2010-12-21
This is a problem that is affecting a large number of people. I have many thumb drives, external drives, etc. Something as basic as USB transfer should work well on any OS. Why is this a problem with Ubuntu. I am excited that Ubuntu is expanding, even being loaded on dell OEM machines, and I am excited that it is open-source. I have no room to complain, but if Ubuntu wants to keep expanding, the general public will not tolerate problems like this any better than they tolerated windows vista.

---

### Post by GuiGuy on 2010-12-21
> **ffixcollector said:**
>  Why is this a problem with Ubuntu.

I suspect it's because not many will know how to fix it and those who might have the skills & knowledge are blissfully unaware; they are too busy  playing in their shells :D 

Cheers & seasonal best wishes to all.

---

### Post by dpwilson on 2011-01-10
I found this link, [http://www.dslreports.com/forum/r25103425-Ubuntu-10.10-slow-USB-transfer-after-upgrade.]("http://www.dslreports.com/forum/r25103425-Ubuntu-10.10-slow-USB-transfer-after-upgrade.") while searching for a fix.  It helped me out a bit, but still only around 8.5 - 9 MB/s.  Not real sure what I should be expecting either though, but I know its a lot better than what I had and it hasn't stalled after I moved it off the same hub as as the mouse/keyboard which is a plus.

---

### Post by dpwilson on 2011-01-10
I just ran similar test on my laptop  and desktop using 10.04 and windows vista.  Transferring the same files/folder on each, the results are:
ubuntu 10.10 (desktop) - 8.5 - 9 MB/s
ubuntu 10.04 (laptop) - 8.5 - 9 MB/s
windows vista (laptop) - 6.5 - 7 MB/s

I am going to check the BIOS on the laptop to see if I can change somethings and will retry and post.

UPDATE: after disabling usb legacy support on the laptop, there was virtually no change to transfer rates, if anything, they were a hair slower across both ubuntu and windows.  So there's my two cents for what its worth.

---

### Post by nito2721 on 2011-01-14
> **dpwilson said:**
> I found this link, [http://www.dslreports.com/forum/r25103425-Ubuntu-10.10-slow-USB-transfer-after-upgrade.](http://www.dslreports.com/forum/r25103425-Ubuntu-10.10-slow-USB-transfer-after-upgrade.) while searching for a fix.  It helped me out a bit, but still only around 8.5 - 9 MB/s.  Not real sure what I should be expecting either though, but I know its a lot better than what I had and it hasn't stalled after I moved it off the same hub as as the mouse/keyboard which is a plus.


This helped me. Hope it helps others as well.

---

### Post by Hotdog_Incident on 2011-01-18
I remember this problem from Mint 7.  Now I'm running Mint 10 and the same issue still exists...
(Mint is based on Ubuntu)

I have benchmarked a handful of thumb-drives in Windows.  The fastest ones gave consistent 30MB read and 30MB write which is about the max transfer rate for USB 2.0.

When doing large file transfers in Mint, (eight 1GB files for example) the transfer starts near 30MBps, but after some minutes, the throughput just tapers and keeps getting slower, down to 2.6MBps.

So frustrating!  I don't think it's a cache issue because the same transfers go relatively fast in Windows.

Does nobody know the cause?

---

### Post by GuiGuy on 2011-01-18
> **Hotdog_Incident said:**
> 
Does nobody know the cause?

Those that might know aren't telling.

The fanboys will tell us that it's all our fault because we don't explore the inner workings of Linux enough and we haven't learnt to use the shell.

The fools will simply post that it works for them.

I personally suspect it is an obscure issue. I have a number of linux based PCs running quality and recent hardware- all display the same problem Large file transfers start really fast. Within seconds they slow down to something less than 1Mps. Yet the same hardware will perform at expected speeds running Windows. So it's something to do with linux (ubuntu). 

However, I recently bought two new MEDION AKOYA notebooks. They both run Ubuntu 10.10. USB transfers are blindingly fast. So it seems some hardware is OK. 

I don't think we'll see a fix in our lifetime because the geniuses out there are beavering away on USB3. So the best we can hope for that USB3 might give us speeds better than USB1.1[/tongueincheek]

Cheers

---

### Post by confused57 on 2011-01-21
I just recently experienced the extremely slow usb transfer speeds, using Ubuntu 10.04 64-bit.
Transferring approximately 20 Gb of data from an external usb hard drive(1TB Hitachi) to an internal hard drive, both ext3 partitions, on Ubuntu 10.04 64-bit, the maximum speed was less than 1.0 MB/s.

I cancelled the transfer, rebooted into Ubuntu 8.04 32-bit, on the same computer(nothing was different other than it was 8.04), and the transfer speeds were more than 30 MB/s.  In this case, it appears the problem was with 10.04 64-bit.  Internet searches have failed to show a viable solution to the problem.  There was an error message in 10.04 when unmounting the drive pertaining to synchronized cached, which I've found references to with internet searches, but again no solution.

---

### Post by GuiGuy on 2011-01-21
> **confused57 said:**
> 
I cancelled the transfer, rebooted into Ubuntu 8.04 32-bit, on the same computer(nothing was different other than it was 8.04), and the transfer speeds were more than 30 MB/s.  In this case, it appears the problem was with 10.04 64-bit.  Internet searches have failed to show a viable solution to the problem.  There was an error message in 10.04 when unmounting the drive pertaining to synchronized cached, which I've found references to with internet searches, but again no solution.

IIRC, it was after 8.04 that they fixed this problem. I say fixed because surely they wouldn't make something worse in successive versions, would they?

---

### Post by unicorn-21 on 2011-02-12
hi there,
I am in the process now of backing photo's, video's etc to an external hard-drive via USB and it is very slow. It is so slow that I now plug the external drive into my XP laptop and FTP the files onto my Ubuntu machine.

Is there any resolution to this?

---

### Post by GuiGuy on 2011-02-12
> **unicorn-21 said:**
> 
Is there any resolution to this?

Absolutely!  Ubuntu doesn't do USB2 on flashdrives yet. And since we've been waiting for them to fix this since at least Karmic, I don't hold any hope. 

SO, use windoze.

I use my WIn7 based notebook to copy across from my ubuntu PC. Works pretty well as long as you have a gigabit network.

---

### Post by YA§uOtL]gS7y£xpj}R on 2011-02-20
Hi
I 'm using Ubuntu 10.4.

I also have very slow writes with an USB pen of 8Gb,  the transfer rate was about 15Kb.
Surprisingly testing with another O.S located in another drive but with the same version (10.4), everything was OK.

I have found a workaround just doing this: If I dismount/remount the USB pendrive with the disk utility from System/Admin  the speed of the transfers becomes normal (About 5Mb).

Hope this helps
:)

---

### Post by GuiGuy on 2011-02-20
> **Erunaven said:**
> I have found a workaround just doing this: If I dismount/remount the USB pendrive with the disk utility from System/Admin  the speed of the transfers becomes normal (About 5Mb).


Is that sustained? In other words, when you transfer a file > 600MB, what's the speed after the first 250MB or so (indicated)

---

### Post by linuxisgoed on 2011-03-19
I'm running Ubuntu 10.10 and have only been about to transfer info to my usb stick at just over 5MB/sec it seems very slow.  Not sure what actions to take to correct this.

---

### Post by GuiGuy on 2011-03-20
> **linuxisgoed said:**
> I'm running Ubuntu 10.10 and have only been about to transfer info to my usb stick at just over 5MB/sec it seems very slow.  Not sure what actions to take to correct this.

Consider yourself lucky. 5mbps would be a luxury for many. If I copy a 650M file the first 150M scream by, probably as data is been transferred to memory before writing to the flashmem device. 

Then it slows down.... BY 400M its less than 1mbps. By 500 < 150kbps. 

I'll shut up now or the fanbois will come out of the shadows to tell me it's all my fault....

---

### Post by AfriKa~Fantasia on 2011-03-21
i'm using karmic, i can say i have same problem.
i see you using lucid, this means if i upgrade to lucid, it won't fix this problem, right?
so, no solutions.

peace

---

### Post by GuiGuy on 2011-03-21
> **AfriKa~Fantasia said:**
> i'm using karmic, i can say i have same problem.
i see you using lucid, this means if i upgrade to lucid, it won't fix this problem, right?


Basically that's correct. However, there is the odd piece of hardware that works OK. We have a Medion AKOYA E7216 notebook. USB file transfer to memory sticks works very well. But on most PCs it's the same sad story. 

The best solution I have found is to maintain a WIndows PC. The Ubuntu fanbois can rant all they like, there are some things WIndows and MacBooks just do so much better. 

Cheers

---

### Post by ajgreeny on 2011-03-21
Just to add my recent experience of this slow usb transfer problem to this thread as a bit of a warning.

I run 10.04, Lucid, 32 bit on a sempron 2400+, 2GB ram, with ATI 9200SE graphics card.  To get the best from that card I was trying the kernel ppa repos with a couple of 2.6.37 kernels on the system.  They possibly helped a little with graphics rendering, but the main problem was the incredibly slow file transfer to usb, either flash drives, writing to USB install disks using the startup-disk-creator, or using rsync for regular backups, nothing was faster than 2MB/sec, and often it was only a few KB/sec, totally unacceptable.

It occurred to me that when I installed the system USB speeds were as expected, 20GB/sec or more, so as a trial I booted to the latest 2.6.32-30 kernel, which was installed with updates in the normal way, and "BINGO", I am back to 20GB+ speed.

It just goes to show that you have to look at all the effects of using packages not in the normal repos, and can not assume that just because it will install, it will also work without fault.

Those two kernels are now a thing of the past for me, and I think the 2.6.32-30 kernel is also better at graphics than the original, so I am a happy man once again.

---

### Post by GuiGuy on 2011-03-21
> **ajgreeny said:**
> 
It occurred to me that when I installed the system USB speeds were as expected, 20GB/sec or more, so as a trial I booted to the latest 2.6.32-30 kernel, which was installed with updates in the normal way, and "BINGO", I am back to 20GB+ speed.

Are the high speeds sustained on large  (> 250M) files? It's my observation small file transfers give a perception that all is well, unless a lot of them are being copied in the same batch.

Cheers

---

### Post by ajgreeny on 2011-03-22
Good question to which I don't have an answer.

I tested the transfer rate on my machine by copying an iso of ubuntu 10.04-2 from usb drive to my hard disk to "burn" it as a usb startup disk.  It took about an hour to make that startup usb with the 2.6.37 kernels, whereas I know it used to take about 5 or 10 minutes previously.  I tested that time again with the 2.6.32 kernel and making a usb startup disk is also back to the expected faster time again.

Whether that helps answer your question I am not sure; I know that the startup disk contains a lot of small files, but it also has the huge casper file, so it may not be an answer in any way to your question.

Not to worry; I'm happy again now that I can backup to external usb hard drive in a sensible time.  I just thought it worth mentioning in this thread as slow usb transfers seem to be a problem to a lot of people, and this could be a cause for some of them as well as me.

---

### Post by RussellWing on 2011-04-02
Please check your BIOS settings before concluding Ubuntu 10.04 is at fault (as I initially did). I had not enabled high speed USB in BIOS, once I did it flies along at the right speed.

Type lspci to check you have an EHCI USB controller (EHCI = USB 2.0, UHCI = USB 1.0). EHCI can operate in 2 modes: 12 Mbps (so called Full speed) or 480Mbps (High Speed). In my case I needed to explicitly set High speed in the BIOS before my USB drive would function at the maximum speed (copying 4+ GB files, using cp in terminal rather than Nautilus).

I am using 10.04 on Shuttle with the USB hard drive connected to the rear hub, along with a USB keyboard and mouse.

Hope this helps someone :D

---

### Post by felipemartim on 2011-04-15
I am having the same problem here, but I just realized that transfering from ext3 to FAT is faster than from NTFS to FAT.
I have a NTFS partition where I keep my videos (>2GB) and to transfer to my usb stick I first copy it to the ext3 partition (home) and then to the usb stick.

I don't know why that happens.

---

### Post by dtach on 2011-06-30
> **RussellWing said:**
> Please check your BIOS settings before concluding Ubuntu 10.04 is at fault (as I initially did). I had not enabled high speed USB in BIOS, once I did it flies along at the right speed.

Type lspci to check you have an EHCI USB controller (EHCI = USB 2.0, UHCI = USB 1.0). EHCI can operate in 2 modes: 12 Mbps (so called Full speed) or 480Mbps (High Speed). In my case I needed to explicitly set High speed in the BIOS before my USB drive would function at the maximum speed (copying 4+ GB files, using cp in terminal rather than Nautilus).

I am using 10.04 on Shuttle with the USB hard drive connected to the rear hub, along with a USB keyboard and mouse.

Hope this helps someone :D


I ran lspci and was actually startled to find out that you were absolutely correct as far as my usb controllers basically being stuck at usb1 speeds. But what was equally startling for me is the fact that there is NOWHERE in my bios that gives the option of upping the speed to "full" or "high" speed. Do you know of any workarounds for people that don't have the ability to switch it through their bios?   (damn HP and their notoriously crappy bios...)

btw, I'm willing to bet that this is probably what the majority of people are experiencing, just as the latest kernel is not properly communicating controller power-savings mode with a large amount of people's system bioses resulting in battery life in 11.04 being severely drained.

---

### Post by pizza-is-good on 2011-07-01
> **dtach said:**
> I ran lspci and was actually startled to find out that you were absolutely correct as far as my usb controllers basically being stuck at usb1 speeds. But what was equally startling for me is the fact that there is NOWHERE in my bios that gives the option of upping the speed to "full" or "high" speed. Do you know of any workarounds for people that don't have the ability to switch it through their bios?   (damn HP and their notoriously crappy bios...)

btw, I'm willing to bet that this is probably what the majority of people are experiencing, just as the latest kernel is not properly communicating controller power-savings mode with a large amount of people's system bioses resulting in battery life in 11.04 being severely drained.


I'm running into the same problem. My lspci output is as following:
```

...
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)

...

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)

...

```And like dtach, I have no options in my BIOS to chance the speeds of th EHCI controllers...
And there are only 4 USB ports in the laptop, but I think that is not related to the number of USB controllers. 
How do I assign a controller to a specific port?

---

