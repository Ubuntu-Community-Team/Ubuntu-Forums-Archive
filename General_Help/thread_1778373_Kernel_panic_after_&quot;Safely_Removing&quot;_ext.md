---
title: "Kernel panic after &quot;Safely Removing&quot; external hard drive"
date: 2011-06-08
forum: General Help
---

### Post by Brushstroke on 2011-06-08
I don't know why it's happening or what caused it, but just a few minutes ago it occurred that every time I unmount/power down my external hard drive from within the Nautilus browser, Ubuntu freezes and Caps Lock starts blinking, indicative of a kernel panic. It doesn't do this when I Safely Remove the drive from the right-click menu on the drive's desktop icon. Even stranger is that no other external device I've tried causes the panic. It only does this with this particular external hard drive and it's a repeatable error. 

Why is this happening and how do I fix it?

Thanks, 
Phil

EDIT: To note, I'm using Ubuntu 10.04 with the 2.6.32.33 kernel. Not Ubuntu 11.04.

---

### Post by Brushstroke on 2011-06-09
...bump.

---

### Post by tgalati4 on 2011-06-09
We like to wait 24 hours before a b*mp.

What does dmesg say when remotely logged in?

dmesg | tail -f

You should see some error just prior to the panic.

---

### Post by Brushstroke on 2011-06-09
Sorry about the early bump. 

dmesg produces this output: 

> [ 3934.582607] [UFW BLOCK] IN=wlan0 OUT= MAC=b4:82:fe:13:f2:d7:c0:3f:0e:69:ca:4a:08:00 SRC=76.11.53.95 DST=10.0.0.2 LEN=64 TOS=0x00 PREC=0x00 TTL=109 ID=16125 DF PROTO=TCP SPT=2792 DPT=5346 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 3937.537093] [UFW BLOCK] IN=wlan0 OUT= MAC=b4:82:fe:13:f2:d7:c0:3f:0e:69:ca:4a:08:00 SRC=76.11.53.95 DST=10.0.0.2 LEN=64 TOS=0x00 PREC=0x00 TTL=109 ID=16210 DF PROTO=TCP SPT=2792 DPT=5346 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 3941.571280] [UFW BLOCK] IN=wlan0 OUT= MAC=b4:82:fe:13:f2:d7:c0:3f:0e:69:ca:4a:08:00 SRC=76.11.53.95 DST=10.0.0.2 LEN=64 TOS=0x00 PREC=0x00 TTL=109 ID=16375 DF PROTO=TCP SPT=2794 DPT=5346 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 3944.577290] [UFW BLOCK] IN=wlan0 OUT= MAC=b4:82:fe:13:f2:d7:c0:3f:0e:69:ca:4a:08:00 SRC=76.11.53.95 DST=10.0.0.2 LEN=64 TOS=0x00 PREC=0x00 TTL=109 ID=16445 DF PROTO=TCP SPT=2794 DPT=5346 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 3950.564103] [UFW BLOCK] IN=wlan0 OUT= MAC=b4:82:fe:13:f2:d7:c0:3f:0e:69:ca:4a:08:00 SRC=76.11.53.95 DST=10.0.0.2 LEN=64 TOS=0x00 PREC=0x00 TTL=109 ID=16623 DF PROTO=TCP SPT=2794 DPT=5346 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 5681.414440] [UFW BLOCK] IN=wlan0 OUT= MAC=b4:82:fe:13:f2:d7:c0:3f:0e:69:ca:4a:08:00 SRC=69.114.183.35 DST=10.0.0.2 LEN=48 TOS=0x00 PREC=0x00 TTL=107 ID=2867 DF PROTO=TCP SPT=59457 DPT=5346 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 5684.401554] [UFW BLOCK] IN=wlan0 OUT= MAC=b4:82:fe:13:f2:d7:c0:3f:0e:69:ca:4a:08:00 SRC=69.114.183.35 DST=10.0.0.2 LEN=48 TOS=0x00 PREC=0x00 TTL=107 ID=2965 DF PROTO=TCP SPT=59457 DPT=5346 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 5687.400066] [UFW BLOCK] IN=wlan0 OUT= MAC=b4:82:fe:13:f2:d7:c0:3f:0e:69:ca:4a:08:00 SRC=69.114.183.35 DST=10.0.0.2 LEN=48 TOS=0x00 PREC=0x00 TTL=107 ID=3108 DF PROTO=TCP SPT=59458 DPT=5346 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 5690.390575] [UFW BLOCK] IN=wlan0 OUT= MAC=b4:82:fe:13:f2:d7:c0:3f:0e:69:ca:4a:08:00 SRC=69.114.183.35 DST=10.0.0.2 LEN=48 TOS=0x00 PREC=0x00 TTL=107 ID=3207 DF PROTO=TCP SPT=59458 DPT=5346 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 5696.374659] [UFW BLOCK] IN=wlan0 OUT= MAC=b4:82:fe:13:f2:d7:c0:3f:0e:69:ca:4a:08:00 SRC=69.114.183.35 DST=10.0.0.2 LEN=48 TOS=0x00 PREC=0x00 TTL=107 ID=3423 DF PROTO=TCP SPT=59458 DPT=5346 WINDOW=8192 RES=0x00 SYN URGP=0 
Honestly, I hate to sound like a noob here but I do not know how to interpret this here. But I did take a look in /var/log/messages and found this interesting gem: 

> Jun  8 23:07:50 ubuntu-laptop kernel: [ 2014.000051] usb 1-3: new high speed USB device using ehci_hcd and address 2
Jun  8 23:07:51 ubuntu-laptop kernel: [ 2014.151975] usb 1-3: configuration #1 chosen from 1 choice
Jun  8 23:07:51 ubuntu-laptop kernel: [ 2014.290732] Initializing USB Mass Storage driver...
Jun  8 23:07:51 ubuntu-laptop kernel: [ 2014.290871] scsi6 : SCSI emulation for USB Mass Storage devices
Jun  8 23:07:51 ubuntu-laptop kernel: [ 2014.291053] usbcore: registered new interface driver usb-storage
Jun  8 23:07:51 ubuntu-laptop kernel: [ 2014.291056] USB Mass Storage support registered.
Jun  8 23:07:56 ubuntu-laptop kernel: [ 2019.290828] scsi 6:0:0:0: Direct-Access     Seagate  FreeAgent Go     0148 PQ: 0 ANSI: 4
Jun  8 23:07:56 ubuntu-laptop kernel: [ 2019.294693] sd 6:0:0:0: Attached scsi generic sg2 type 0
Jun  8 23:07:56 ubuntu-laptop kernel: [ 2019.303894] sd 6:0:0:0: [sdb] 976773167 512-byte logical blocks: (500 GB/465 GiB)
Jun  8 23:07:56 ubuntu-laptop kernel: [ 2019.304377] sd 6:0:0:0: [sdb] Write Protect is off
Jun  8 23:07:56 ubuntu-laptop kernel: [ 2019.305631]  sdb: sdb1
Jun  8 23:07:56 ubuntu-laptop kernel: [ 2019.375205] sd 6:0:0:0: [sdb] Attached SCSI disk
**Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092320] scsi 6:0:0:0: [sdb] Unhandled error code**
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092327] scsi 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_OK
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092335] scsi 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 b7 00 00 08 00
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092358] __ratelimit: 18 callbacks suppressed
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092441] PGD 1003067 PUD 1007063 PMD 130cbb063 PTE 8000000001597161
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092461] CPU 0 
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092465] Modules linked in: usb_storage cryptd aes_x86_64 aes_generic binfmt_misc ppdev vboxnetadp vboxnetflt vboxdrv ipt_REJECT ipt_LOG xt_limit xt_tcpudp ipt_addrtype xt_state joydev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss ip6table_filter ip6_tables snd_pcm nf_nat_irc nf_conntrack_irc nf_nat_ftp snd_seq_dummy snd_seq_oss nf_nat snd_seq_midi nf_conntrack_ipv4 nf_defrag_ipv4 snd_rawmidi nf_conntrack_ftp snd_seq_midi_event nf_conntrack snd_seq iptable_filter snd_timer snd_seq_device ip_tables fbcon tileblit font bitblit x_tables softcursor fglrx(P) snd vga16fb vgastate soundcore psmouse edac_core serio_raw snd_page_alloc edac_mce_amd i2c_piix4 rtl8187se(C) shpchp video output lp parport r8169 mii ahci pata_atiixp
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092560] Pid: 1943, comm: scsi_eh_6 Tainted: P         C 2.6.32-33-generic #65-Ubuntu Satellite L455D
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092566] RIP: 0010:[<ffffffff81597220>]  [<ffffffff81597220>] sg_fops+0x0/0xe0
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092576] RSP: 0018:ffff88008cf55c68  EFLAGS: 00010082
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092580] RAX: ffffffff81597220 RBX: ffff880132b5e900 RCX: 000000010002a9ad
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092585] RDX: ffff8800b0414b00 RSI: ffff88008ca8b000 RDI: ffff880132b5e900
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092589] RBP: ffff88008cf55c80 R08: 0000000000000001 R09: 0000000000000002
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092594] R10: 0000000000000000 R11: 0000000000000000 R12: ffff88008ca8b000
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092599] R13: ffff880132b5e900 R14: 0000000000000286 R15: ffffffff817174a1
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092604] FS:  00007fcdb55f9820(0000) GS:ffff880028200000(0000) knlGS:00000000f69f6760
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092610] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092614] CR2: ffffffff81597220 CR3: 0000000110f94000 CR4: 00000000000006f0
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092619] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092624] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092629] Process scsi_eh_6 (pid: 1943, threadinfo ffff88008cf54000, task ffff880113c716f0)
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092636]  ffffffff812969e8 ffff880132b5e900 ffff88008ca8b000 ffff88008cf55cb0
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092643] <0> ffffffff812a082c ffff88008ca8b000 ffff88008ca8b000 00000000fffffffb
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092651] <0> ffff880132b5e900 ffff88008cf55cd0 ffffffff812a0951 ffff88008ca8b000
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092670]  [<ffffffff812969e8>] ? elv_completed_request+0x78/0xe0
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092678]  [<ffffffff812a082c>] __blk_put_request+0x3c/0xe0
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092684]  [<ffffffff812a0951>] blk_finish_request+0x81/0xc0
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092691]  [<ffffffff812a0d64>] blk_end_bidi_request+0x54/0x80
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092696]  [<ffffffff812a0de0>] blk_end_request+0x10/0x20
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092702]  [<ffffffff812a0e25>] blk_end_request_err+0x35/0x60
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092712]  [<ffffffff8138b36e>] scsi_io_completion+0x15e/0x510
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092719]  [<ffffffff81382d12>] scsi_finish_command+0xc2/0x130
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092726]  [<ffffffff8138714e>] scsi_eh_flush_done_q+0x7e/0x160
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092732]  [<ffffffff813887d1>] scsi_unjam_host+0xb1/0x210
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092739]  [<ffffffff81388a48>] scsi_error_handler+0x118/0x170
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092745]  [<ffffffff81388930>] ? scsi_error_handler+0x0/0x170
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092755]  [<ffffffff81084946>] kthread+0x96/0xa0
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092763]  [<ffffffff810131ea>] child_rip+0xa/0x20
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092769]  [<ffffffff810848b0>] ? kthread+0x0/0xa0
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092775]  [<ffffffff810131e0>] ? child_rip+0x0/0x20
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092839]  RSP <ffff88008cf55c68>
Jun  8 23:08:22 ubuntu-laptop kernel: [ 2045.092848] ---[ end trace 048776744f8c122c ]---
Jun  8 23:08:28 ubuntu-laptop kernel: [ 2051.440095] usb 1-3: USB disconnect, address 2
Jun  8 23:08:41 ubuntu-laptop kernel: [ 2064.170059] usb 1-3: new high speed USB device using ehci_hcd and address 3
Jun  8 23:08:41 ubuntu-laptop kernel: [ 2064.321641] usb 1-3: configuration #1 chosen from 1 choice
Jun  8 23:08:41 ubuntu-laptop kernel: [ 2064.324853] scsi7 : SCSI emulation for USB Mass Storage devices
Jun  8 23:08:46 ubuntu-laptop kernel: [ 2069.320902] scsi 7:0:0:0: Direct-Access     Seagate  FreeAgent Go     0148 PQ: 0 ANSI: 4
Jun  8 23:08:46 ubuntu-laptop kernel: [ 2069.324777] sd 7:0:0:0: Attached scsi generic sg2 type 0
Jun  8 23:08:46 ubuntu-laptop kernel: [ 2069.334701] sd 7:0:0:0: [sdb] 976773167 512-byte logical blocks: (500 GB/465 GiB)
Jun  8 23:08:46 ubuntu-laptop kernel: [ 2069.335186] sd 7:0:0:0: [sdb] Write Protect is off
Jun  8 23:08:46 ubuntu-laptop kernel: [ 2069.336437]  sdb: sdb1
Jun  8 23:08:46 ubuntu-laptop kernel: [ 2069.403891] sd 7:0:0:0: [sdb] Attached SCSI disk
**Jun  8 23:09:09 ubuntu-laptop kernel: [ 2092.728801] scsi 7:0:0:0: [sdb] Unhandled error code**
Jun  8 23:09:09 ubuntu-laptop kernel: [ 2092.728810] scsi 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_OK
Jun  8 23:09:09 ubuntu-laptop kernel: [ 2092.728818] scsi 7:0:0:0: [sdb] CDB: Read(10): 28 00 2e 91 08 3f 00 00 08 00
Jun  8 23:09:09 ubuntu-laptop kernel: [ 2092.728843] __ratelimit: 38 callbacks suppressed
Jun  8 23:09:16 ubuntu-laptop kernel: [ 2099.690091] usb 1-3: USB disconnect, address 3
Jun  8 23:15:46 ubuntu-laptop pulseaudio[1467]: ratelimit.c: 1 events suppressed
Jun  8 23:18:34 ubuntu-laptop pulseaudio[1467]: ratelimit.c: 1 events suppressed
I'm curious what this part I've bolded is about. Might this have something to do with the problem?

---

### Post by linuxinstalledfromhdd on 2011-06-09
Total guess.. but..

Are you force disconnecting because your system is slow and can't wait?  Is there something that is causing your system to run slow?  Are you running anything besides normal OS defaults at the time when you are disconnecting it?  

I don't know what is causing this error..  keep bumping this periodically.

---

### Post by Brushstroke on 2011-06-09
Nope. Normal OS defaults and the system runs pretty quickly actually. And I always use the Safely Remove Drive option with no problems. This is completely new.

Although, I do wonder if it has something to do with the recent kernel update from a few days ago. Lucid is still on 2.6.32.xx. And it just upgraded to 2.6.32.33 a few days ago.

---

### Post by Brushstroke on 2011-06-09
Bad news. I think it may be something to do with the external hard drive itself. It might be going bad. I found this in kern.log in the System Log Viewer: 

```
Jun  8 23:09:09 ubuntu-laptop kernel: [ 2092.728835] end_request: I/O error, dev sdb, sector 781256767
Jun  8 23:09:09 ubuntu-laptop kernel: [ 2092.728843] __ratelimit: 38 callbacks suppressed
Jun  8 23:09:09 ubuntu-laptop kernel: [ 2092.728849] Buffer I/O error on device sdb1, logical block 97657088
Jun  8 23:09:09 ubuntu-laptop kernel: [ 2092.729342] Buffer I/O error on device sdb1, logical block 97657088
Jun  8 23:09:09 ubuntu-laptop kernel: [ 2092.729402] Buffer I/O error on device sdb1, logical block 97657117
Jun  8 23:09:09 ubuntu-laptop kernel: [ 2092.729410] Buffer I/O error on device sdb1, logical block 97657117
Jun  8 23:09:09 ubuntu-laptop kernel: [ 2092.729423] Buffer I/O error on device sdb1, logical block 1
Jun  8 23:09:09 ubuntu-laptop kernel: [ 2092.729431] Buffer I/O error on device sdb1, logical block 1
Jun  8 23:09:09 ubuntu-laptop kernel: [ 2092.729445] Buffer I/O error on device sdb1, logical block 97657118
Jun  8 23:09:09 ubuntu-laptop kernel: [ 2092.729456] Buffer I/O error on device sdb1, logical block 97657118
Jun  8 23:09:09 ubuntu-laptop kernel: [ 2092.729465] Buffer I/O error on device sdb1, logical block 97657118
Jun  8 23:09:09 ubuntu-laptop kernel: [ 2092.729475] Buffer I/O error on device sdb1, logical block 97657118
Jun  8 23:09:16 ubuntu-laptop kernel: [ 2099.690091] usb 1-3: USB disconnect, address 3
```

---

### Post by matt_symes on 2011-06-09
Hi

Check the SMART status of the hard drive. If it is newish then it should have it.

You can do this from System->Administration->Disk Utility. Select the drive and select the "View smart data and run tests" option.

If your more of a CLI person

```
sudo apt-get install smartmontools
```

Run the extended test and then view the results.

```
man smartctl
```

for more info.

Kind regards

---

### Post by tgalati4 on 2011-06-09
Do you have an external power supply connected to this disk?  If not, you should.  USB ports can't supply enough power to run the drive properly, leading to strange errors.  Add a power supply and suddenly things start to work correctly.

It appears that the kernel panic resulted from an unhandled disk error that you pointed out.  Immediately after that point is a crash dump of the code involved.

If you log into your machine remotely using ssh, you can use dmesg | tail -f to watch this in real time.

If you are into that sort of thing.

---

### Post by gradinaruvasile on 2011-06-09
> **Brushstroke said:**
> I don't know why it's happening or what caused it, but just a few minutes ago it occurred that every time I unmount/power down my external hard drive from within the Nautilus browser, Ubuntu freezes and Caps Lock starts blinking, indicative of a kernel panic. It doesn't do this when I Safely Remove the drive from the right-click menu on the drive's desktop icon. Even stranger is that no other external device I've tried causes the panic. It only does this with this particular external hard drive and it's a repeatable error. 

Why is this happening and how do I fix it?

Thanks, 
Phil

EDIT: To note, I'm using Ubuntu 10.04 with the 2.6.32.33 kernel. Not Ubuntu 11.04.


Start the disk utility (the administration menu), select your drive and look at its smart data - reallocation count, current pending sector count, uncorrectable sector count should be 0 on a good drive.

---

### Post by Brushstroke on 2011-06-09
> **gradinaruvasile said:**
> Start the disk utility (the administration menu), select your drive and look at its smart data - reallocation count, current pending sector count, uncorrectable sector count should be 0 on a good drive.
It says one sector's been reallocated. Current Pending Sector count and Uncorrectable Sector count are both 0. 

Regardless, it's stopped causing the system to freeze. I don't know why though.

EDIT: Scratch that. It's doing it again...

---

### Post by fmachado2906 on 2011-06-10
Folks,


The same began to happen yesterday with me, I noticed after I have installed the 2.6.38-10-generic-pae kernel. I'm on a Thinkpad t400, ubuntu 11.04, all fixes installed. 

I'm not able to try the same procedure right now since I don't have the hard drive here with me, but will try with the "default" kernel I had before.

But to me, it happened right after Deja Dup was doing its scheduled weekly backup into the drive.. I tried 2 times repeating, and 2 times it froze. 

One thing though, is that my Caps Lock doesn't blink as stated here..

Regards, Fábio.

---

### Post by matt_symes on 2011-06-11
Hi

@[fmachado2906]("http://ubuntuforums.org/member.php?u=771644")

> One thing though, is that my Caps Lock doesn't blink as stated here..That is a good thing it means your kernel did not crash. 

Run fsck and check the SMART status of the drive.

To run fsck

```
sudo touch /forcefsck
```Enter your password. It will not be echoed to the screen. Then to reboot.

Check the SMART status as instructed in the other post.

@[Brushstroke]("http://ubuntuforums.org/member.php?u=1085692")
> 
It says one sector's been reallocated. Current Pending Sector count and Uncorrectable Sector count are both 0. 

Regardless, it's stopped causing the system to freeze. I don't know why though.

EDIT: Scratch that. It's doing it again...                                                                                                                   One sector reallocated should be all right.

As stated, does the drive have an external power supply ?

How much free space is on the drive ?

Kind regards

---

### Post by 3rdalbum on 2011-06-11
> **matt_symes said:**
> Hi

@[fmachado2906]("http://ubuntuforums.org/member.php?u=771644")

That is a good thing it means your kernel did not crash.

Or that it crashed before it was able to run the "blink the keyboard lights" routine.

My advice to the OP is to test your RAM. Actually physically test it - take some of it out, see if the problem still occurs. If it does, put it back in and take the rest of it out. Narrow it down to a particular RAM stick and then put that stick in the trash.

There is a lot of bad RAM these days. You might not see a problem in Windows because Windows aggressively grabs up to half your RAM and then just lets it sit unused.

My way of thinking is that when you use the "Safely Remove" or the "Eject" on your disk, it causes the kernel to flush the read and write caches, which are of course stored in RAM.

---

### Post by matt_symes on 2011-06-12
Hi

> Or that it crashed before it was able to run the "blink the keyboard lights" routine.A good point. 

I agree with the idea of testing the RAM.

Kind regards

---

### Post by dvdtree on 2011-07-18
Hi all,
I'm having the same issue and I'm conviced it's related to the new Ubuntu 10.04 2.6.32.33 kernel.
With the former kernels nothing (bad) happens.

Should we start a bug notice?
I'm sorry I'm just a little more of a newby so forgive me if I'm writing nonsense.

Regards to all of you and thanks for any help.

D

---

### Post by claracc on 2011-07-18
Same behaviour in my hp compaq 6720s laptop using kernel 2.6.32-33-generic. When I right  click to remove usb harddrive in the safely way, computer crash enterely, screen remains freezed and computer don't respond to Ctrl +Alt + prn screen RESUIB, neither ctrl+alt+f1 to f6. I have to do a hard reset turning off the computer with the button.

I also am sure is the new kernel, with last kernel 2.6.32-32-generic, the usb hard drive could be esaily removed without a crash. 

I attached errors file in syslog: errors.txt

Thanks in advance

---

### Post by dvdtree on 2011-07-18
I also think it may be related to the specific architecture of HP laptops (like the damned audio issue).
I have an HP Compaq NX6325 (AMD 64x2 Turion TL60).

If all ubuntu users had had this problem it sure would have been noticed and evidenced by many more in many blogs.

D

P.S.
So, how to open a mini-bug for just poor HP laptop users? I've no competence and don't really know how to do it. As stated before I don't want to bother nobody with things written badly.

Thanks anyway to ubuntu and to all the community.

---

### Post by claracc on 2011-07-18
There is now an specific bug for this behaviour in launchpad: see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/811745](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/811745)

I don't think it is related with hp architecture laptops since the bug reporter has an ASUSTeK Computer Inc. M51Va

You can see the bug in launchpad ( thelink given) and add more information or click in the button "this bug also affects me"

Regards

---

### Post by dvdtree on 2011-07-18
I'm adding my two cents to the launchpad bug site right now, thanks.

P.S.
By the way I'm going to wait for the next kernel update and use the *.32 version till then

---

### Post by marcelezaaa on 2011-07-19
It is also happening with me on a HP Pavilion ze2000 Laptop, not every time though, but rather often. 
I am quite of a newbie, so until I find a solution for this, how would be a "safe" way to remove the drive?
(it seems to be ok when I Unmount the volume (through terminal or Disk Utility), 

Thank you,

---

### Post by claracc on 2011-07-19
I have decided to stay with kernel 2.6.32-32 generic since there isn't any problem removing the usb hd with the menu.

I haven't tried to remove the hd from the command line with kernel 2.6.32-33, but if it works for you it is a good workaround.

Someone has pointed that using that adding to the panel the applet disk mounting could work too, but I haven't neither try it.

Regards

---

### Post by marcelezaaa on 2011-07-19
Ok, I will try to be a little more detailed with my problem.
I installed Ubuntu 2 weeks ago in this HP Pavilion ZE2000. Also about two weeks ago I bought a Buffalo Ministation External HD. I first used the standard FAT32 Filesystem. I didnt notice any problems with it.

Then I formated the drive into NTFS, since I read in the forum that Linux does support NTFS well. The drive stays connected on the computer most of the time. (I suppose there is no problem with that). But if I "Safely Remove" it. The system will crash (but not ALL the time... a few times it went ok)

What I wonder now is if the filesystem is (also) a reason for this problem.
Should I change back to FAT32? 
What also worries me is that, even not really unplugging the Drive, the SMART data tells me that "power off retract - Value: 43". If that means that there were 43 emergency retract cycles, I think all the time I turn the computer off the drive is doing a emergency retract, or something like that... 

Also, right now appeared THOUSANDS of TB, as "Free Partition" on the hard drive. (as you can see on the Print Screen).
Now I am trying a "safe removal" but it says that the drive is busy.  Well, it is displaying some weird behaviour. Sometimes the lights goes off for a few seconds, and back on again.
but the SMART Data doesnt really show and problem with it, and says it is "Healthy".

Well, I am very new to all of this, so I am sorry if I am doing something obviously wrong but... i just dont know... but still... VERY happy of not having to use Windows. (hopefully soon, I do not use it at all)

So, could someone please help with these 2 "questions"?
1 - Wheather the Filesystem is one of the reasons for this problem, and if so, which filesystem would you advice to use?
2 - What would be a "real safe way" to unplug the drive?

Thank you very much!

Marcelo

---

### Post by matt5ash on 2011-07-23
Running a system76 Pangolin with two different usb drives, I get a kernel panic message with both when "safely removing" the drives ... these drives work fine on an two other ubuntu 10.04 systems (dell desktops).  I'm running 10.04 with all the latest updates.

So, I think there is a real bug ??

Any thoughts ??

---

### Post by andyhelloween on 2011-07-23
Same thing happened to me. I start noticing it right after upgrade the kernel... and now found this thread. Back to 2.6.32-32 for now solved the problem for me, so thanks all!

I am also using an HP, DV6 and running Lucid.

---

### Post by Brushstroke on 2011-07-23
Hmm. A lot of people with HPs here. I'm using a Toshiba laptop. 

So, I took the advice of someone in this thread and tested my RAM using Memtest. No errors. I don't think this problem has to do with my RAM or anyone else's RAM. This seems to be a consistent problem with the 2.6.32-33 kernel in Lucid. No solution on my end yet either. :/

---

### Post by claracc on 2011-07-24
A workaround that works for me using kernel 2.6.32-33 generic:

You open a xterm and write: mount , in order to see where is mounted my usb hdd, mount command returns /dev/sdb1 on /media/IOMEGA_HDD type fuseblk (rw,nosuid,nodev,allow_other,blksize=512,default_permissions)

So, to safely remove the usb hdd, I write in xterm: sudo umount /media/IOMEGA_HDD, introduce the password and enter.

The command works and the usb harddrive is removed from the system ( no crashes or freezes ), then I can turn off the hdd.

---

### Post by matt5ash on 2011-07-24
Using about the same approach (from the terminal goto 'media', find the drive, and use the command: umount 'drive_name') the drive is unmounted, and there is no kernel panic ... 

So, I guess there's a couple of work-around approaches.  Still, this is not a positive feature ... I guess a script could be put together to make this process easier ??

---

### Post by dvdtree on 2011-07-28
Hi all, 
they found/wrote a kernel which solves the problem see [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/811745/comments/34"), although I don't understand if that new kernel doesn't allow to have the new kernel or software updates.

For now I keep using .33-32 kernel and if I forget to boot it, I disconnect via *System* > *Admin* > *Disk Manager, *unmounting first and then safely removing.

By the way, IMHO all this stuff may be related to  swap memory shortage compared to RAM. In my HP Compaq NX6325 I've 1Gb Swap and 2Gb RAM. 

I'd like to know from someone sharing the problem if they have enough (twice the RAM) Swap memory.

Considering all the set of tweaks including the kernel one,  I don't know if someone shoud write "Solved" somewhere, anyway, thanks for the help to everybody.

---

### Post by dvdtree on 2011-07-29
I made a mistake, the method via *System* > *Admin* > *Disk Manager, *unmounting first and then safely removing, DOES NOT WORK.
Sorry if someone tested it crashing his OS.

D

---

### Post by Dalek Draco ON LINUX on 2011-08-03
I'm having the same issue, running a Dreambook w76. Unmounting from disk utility is fine, but then safely removing (from desktop or disk utility) results in the computer s***ing itself. 

I'm running the latest kernel as well.

---

### Post by barny72 on 2011-08-07
for the records: same issue here on a sony VAIO (VGN-FW11J). Kernel Panic, flashing LED's. Haven't tried the work around yet...

Version 10.04
Kernel 2.6.32-33-generic-pae
GNOME 2.30.2

---

### Post by arturj on 2011-08-10
Please, can everybody with this problem write which filesystem is used on that external drive? I have this issue also on my Fedora-15 box with a ntfs-formated drive. To me it seems to be an ntfs filesystem issue with very recent kernels. 

Cheers

---

### Post by barny72 on 2011-08-11
> **arturj said:**
> Please, can everybody with this problem write which filesystem is used on that external drive? I have this issue also on my Fedora-15 box with a ntfs-formated drive. To me it seems to be an ntfs filesystem issue with very recent kernels. 

Cheers

same here: the external drive has the NTFS file system

---

### Post by papibe on 2011-08-11
I suffered from this behavior, as most of you did (but I didn't know about this thread). If you haven't found out, this was a [confirmed bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/811745") in launchpad.

Fortunately, it was fixed in the latest kernel released by Ubuntu. 
```
$ uname -a
Linux vaughan 2.6.32-33-generic-pae **#72**-Ubuntu SMP Fri Jul 29 22:06:29 UTC 2011 i686 GNU/Linux

```
(Note the #72)
Regards.

---

### Post by barny72 on 2011-08-11
Newsflash: 

I did a bit of a reading in this bug report mentioned earlier and in fact yesterday there was a new kernel release which solved my problem. 

2.6.32-33-generic-pae
#72-Ubuntu SMP Fri Jul 29 22:06:29 UTC 2011

cheers B




> **dvdtree said:**
> Hi all, 
they found/wrote a kernel which solves the problem see [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/811745/comments/34"), although I don't understand if that new kernel doesn't allow to have the new kernel or software updates.

For now I keep using .33-32 kernel and if I forget to boot it, I disconnect via *System* > *Admin* > *Disk Manager, *unmounting first and then safely removing.

By the way, IMHO all this stuff may be related to  swap memory shortage compared to RAM. In my HP Compaq NX6325 I've 1Gb Swap and 2Gb RAM. 

I'd like to know from someone sharing the problem if they have enough (twice the RAM) Swap memory.

Considering all the set of tweaks including the kernel one,  I don't know if someone shoud write "Solved" somewhere, anyway, thanks for the help to everybody.

---

### Post by barny72 on 2011-08-11
> **papibe said:**
> I suffered from this behavior, as most of you did (but I didn't know about this thread). If you haven't found out, this was a [confirmed bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/811745") in launchpad.

Fortunately, it was fixed in the latest kernel released by Ubuntu. 
```
$ uname -a
Linux vaughan 2.6.32-33-generic-pae **#72**-Ubuntu SMP Fri Jul 29 22:06:29 UTC 2011 i686 GNU/Linux

```(Note the #72)
Regards.

sorry mate for repeating you :) 
your typing was quicker then mine and I didn't realise your post. however, problem solved, yea! cheers

---

### Post by gregalynch on 2011-10-16
I have this problem too on an hp dm4t, running oneiric.  i should have the updated kernel, right?

---

### Post by mc4man on 2011-10-16
> **gregalynch said:**
> I have this problem too on an hp dm4t, running oneiric.  i should have the updated kernel, right?

Not really - here is a bug I have on for 11.10 - in _comment 20_ there is link to test kernels if you wish to try.
Otherwise this will be updated on 11.10 in the near future

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/844957](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/844957)

To use the test kernel - 
pick your arch, click on link
Download the 3 .debs and put in an empty folder
Cd to that folder in a terminal & run 
```
sudo dpkg -i *.deb

```

---

### Post by gregalynch on 2011-10-16
Thanks for explaining.  I don't know what I'm doing nearly enough to mess around with the kernel, so I don't think I'll do that. 

Will the patch that's coming out just show up in update manager when they release it?  If so, I'll just wait for that.

---

### Post by mc4man on 2011-10-16
> **gregalynch said:**
> Thanks for explaining.  I don't know what I'm doing nearly enough to mess around with the kernel, so I don't think I'll do that. 

Will the patch that's coming out just show up in update manager when they release it?  If so, I'll just wait for that.

It will when the new kernel is released - the issue has been resolved here for me on 3 external usb drives
There have been a few comments recently from people saying they still get the panic but I get the feeling they didn't try the test kernels

When & if the bug report shows "Fix Released" for **Oneiric** then you'd know the kernel will be available in update manager or shortly so 
Currently it's "Fix Committed"

---

### Post by chuckyanutsup on 2011-11-03
> **mc4man said:**
> Not really - here is a bug I have on for 11.10 - in _comment 20_ there is link to test kernels if you wish to try.
Otherwise this will be updated on 11.10 in the near future

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/844957](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/844957)

To use the test kernel - 
pick your arch, click on link
Download the 3 .debs and put in an empty folder
Cd to that folder in a terminal & run 
```
sudo dpkg -i *.deb

```

Thank you so much for posting this. I'm having the same bug. It only surfaced after I uninstalled the games that came with 11.10. .debs downloaded and testing now :)

---

