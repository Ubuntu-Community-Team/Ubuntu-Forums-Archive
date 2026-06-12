---
title: "Your system encountered a serious kernel problem 9.10"
date: 2009-10-31
forum: General Help
---

### Post by uknowho008 on 2009-10-31
Hi, I keep getting this error after running my computer for a while. I have never had this problem until installing the new 9.10 has this been happening to anybody else? Anybody know what the problem is? Or need more information? The only thing that I've noticed it effecting is that internet stops working and restarting networking doesn't help. Thanks.

> **Your system encountered a serious kernel problem.**

Your system might become unstable now and might need to be restarted.

You can help the developers to fix the problem by reporting it.

---

### Post by wildweathel on 2009-10-31
I've seen this a few times when my USB disk is misbehaving.  I'm pretty sure that box appears whenever the Linux kernel reports an error.  Unfortunately, it doesn't actually *show* the error (which is irritating), nor is it enough for a bug report by itself (which isn't very helpful).

Since you also mention that networking stops working at the same time here's what I think is happening:

1) Something happens involving your networking driver and/or hardware.  This causes two things to happen:
2a) You lose networking.
2b) That error message appears.

It sounds like this is a bug.  Unfortunately, just clicking "report" won't give enough information to give a good bug report.

So, here are the questions to answer:

1) How exactly do you connect to the Internet?  e.g.: "Ethernet cable + DSL" or  "Cable + WiFi Router + WiFi laptop"

2) What kind of networking device does your computer use?  Also, post the output of "lspci."

3) If you search Launchpad for the name of your networking device, can you find a bug report similar to your problem?

Good luck.

---

### Post by uknowho008 on 2009-10-31
I'm connected through Netgear GA311 gigabit pci card, which I haven't had problems with before 9.10. This connects to a router which connects obviously to my cable modem.

lspci
> 00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. Device 6290
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1)
05:06.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)


And I don't see any similar posts on launchpad that have anything to do with my network card, but I do see a similar post about the "serious kernel problem" which doesn't help me.

Any ideas? Thanks.

---

### Post by uknowho008 on 2009-10-31
It seems to be happening for frequently now, like every 15 min or so I haven to restart. :(

---

### Post by wildweathel on 2009-10-31
Yeah, that's interesting.  lspci says you have a Realtek RTL-8169, which is the name of the chip on the card.  

Searching for [r8169]("https://bugs.launchpad.net/bugs/+bugs?field.searchtext=r8169&orderby=-date_last_updated&search=Search&assignee_option=any&field.assignee=&field.bug_reporter=&field.bug_supervisor=&field.bug_commenter=&field.subscriber=&field.status_upstream-empty-marker=1&field.omit_dupes.used=&field.omit_dupes=on&field.has_patch.used=&field.has_cve.used=&field.tag=&field.tags_combinator=ANY") gives 102 bugs as of writing.  To narrow this down, it'd be great to find the error message.  It might be somewhere in /var/log/messages; immediately after it happens it'll be at the end.  Could you especially look for a line mentioning "NETDEV WATCHDOG"?

Also, What did you run before Karmic?  The pop-up error notification is a new feature in Karmic, before then networking would stop working silently.  The error message was there, it just wasn't being popped-up.  A lot of the bugs I'm looking at are from Intrepid and Jaunty-era kernels.

[Bug #381807]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381807")
[Bug #378907]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/378907")

---

### Post by RTrev on 2009-10-31
> **uknowho008 said:**
> Hi, I keep getting this error after running my computer for a while. I have never had this problem until installing the new 9.10 has this been happening to anybody else? Anybody know what the problem is? Or need more information? The only thing that I've noticed it effecting is that internet stops working and restarting networking doesn't help. Thanks.

You've made sure you have all the latest updates, right?  I was getting the same thing until around Wednesday or so.. shortly before final release it simply stopped happening.  <fingers crossed>

---

### Post by uknowho008 on 2009-10-31
Oh wow! You said I had a RTL-8169 so I looked and realized that I had my cable plugged into the onboard network adapter rather than the pci card I had bought. I switched it over and see if the problem persists. I do remember my connection dropping randomly in the past and I think that's why I put a new card in in the first place. I've just never seen the "kernel problem" notification thing, which you said was a new thing.

So I'll try this with the new card and see if it continues. Thanks a lot, and good eyes.

Edit:Also, I was running 9.04 before and my current 9.10 install is totally up to date.

---

### Post by wildweathel on 2009-10-31
Lol, not good enough eyes.  If I had better eyes, I'd have asked if you meant the Realtek or the VIA.  From the picture on Netgear's website, it looks like the Realtek chip is on their card (the Realtek crab is visible in their product picture).

That means you're now switching from the VIA (onboard) to Realtek (expansion card).  Here's hoping it works.  Like I said, the Realtek-related bugs seemed to apply to Intrepid/Jaunty but are fixed in Karmic.  Good luck!

---

### Post by uknowho008 on 2009-10-31
> **wildweathel said:**
> Lol, not good enough eyes.  If I had better eyes, I'd have asked if you meant the Realtek or the VIA.  From the picture on Netgear's website, it looks like the Realtek chip is on their card (the Realtek crab is visible in their product picture).

That means you're now switching from the VIA (onboard) to Realtek (expansion card).  Here's hoping it works.  Like I said, the Realtek-related bugs seemed to apply to Intrepid/Jaunty but are fixed in Karmic.  Good luck!

haha, figures. Well so far so good. I guess this ones solved. Thanks again.

---

### Post by nikkichowchow on 2009-11-01
I have this message now systematically coming out of "suspend". The kernel log has the following interresting story to tell:

Nov  1 16:12:32 doron-linux kernel: [52847.412810] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Nov  1 16:12:32 doron-linux kernel: [52851.668033] ata3: link is slow to respond, please be patient (ready=0)
Nov  1 16:12:32 doron-linux kernel: [52852.564165] ata3.00: configured for UDMA/133
Nov  1 16:12:32 doron-linux kernel: [52852.860024] usb 2-1: reset low speed USB device using uhci_hcd and address 2
Nov  1 16:12:32 doron-linux kernel: [52853.167642] PM: resume devices took 6.560 seconds
Nov  1 16:12:32 doron-linux kernel: [52853.167643] ------------[ cut here ]------------
Nov  1 16:12:32 doron-linux kernel: [52853.167651] WARNING: at /build/buildd/linux-2.6.31/kernel/power/suspend_test.c:52 suspend_test_finish+0x80/0x90()
Nov  1 16:12:32 doron-linux kernel: [52853.167653] Hardware name: IMEDIA J9502
Nov  1 16:12:32 doron-linux kernel: [52853.167654] Component: resume devices
Nov  1 16:12:32 doron-linux kernel: [52853.167656] Modules linked in: nls_utf8 isofs nls_iso8859_1 nls_cp437 vfat fat usblp binfmt_misc ppdev vboxnetflt vboxnetadp vboxdrv psmouse iptable_filter ip_tables x_tables serio_raw snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device sbp2 snd soundcore snd_page_alloc lp nvidia(P) shpchp i2c_viapro parport ohci1394 8139too 8139cp usbhid usb_storage ieee1394 mii via_agp sata_via agpgart
Nov  1 16:12:32 doron-linux kernel: [52853.167693] Pid: 23551, comm: pm-suspend Tainted: P           2.6.31-14-generic #48-Ubuntu
Nov  1 16:12:32 doron-linux kernel: [52853.167695] Call Trace:
Nov  1 16:12:32 doron-linux kernel: [52853.167700]  [<c014518d>] warn_slowpath_common+0x6d/0xa0
Nov  1 16:12:32 doron-linux kernel: [52853.167704]  [<c0174e70>] ? suspend_test_finish+0x80/0x90
Nov  1 16:12:32 doron-linux kernel: [52853.167707]  [<c0174e70>] ? suspend_test_finish+0x80/0x90
Nov  1 16:12:32 doron-linux kernel: [52853.167710]  [<c0145206>] warn_slowpath_fmt+0x26/0x30
Nov  1 16:12:32 doron-linux kernel: [52853.167713]  [<c0174e70>] suspend_test_finish+0x80/0x90
Nov  1 16:12:32 doron-linux kernel: [52853.167716]  [<c0174c5f>] suspend_devices_and_enter+0x9f/0xd0
Nov  1 16:12:32 doron-linux kernel: [52853.167721]  [<c056e41c>] ? printk+0x18/0x1c
Nov  1 16:12:32 doron-linux kernel: [52853.167724]  [<c0174d49>] enter_state+0xb9/0xf0
Nov  1 16:12:32 doron-linux kernel: [52853.167727]  [<c017443d>] state_store+0x6d/0xb0
Nov  1 16:12:32 doron-linux kernel: [52853.167730]  [<c01743d0>] ? state_store+0x0/0xb0
Nov  1 16:12:32 doron-linux kernel: [52853.167734]  [<c0311a70>] kobj_attr_store+0x20/0x30
Nov  1 16:12:32 doron-linux kernel: [52853.167739]  [<c0239290>] sysfs_write_file+0x90/0x100
Nov  1 16:12:32 doron-linux kernel: [52853.167743]  [<c01e747a>] vfs_write+0x9a/0x190
Nov  1 16:12:32 doron-linux kernel: [52853.167746]  [<c0239200>] ? sysfs_write_file+0x0/0x100
Nov  1 16:12:32 doron-linux kernel: [52853.167749]  [<c0572d4b>] ? do_page_fault+0x19b/0x380
Nov  1 16:12:32 doron-linux kernel: [52853.167752]  [<c01e7f3d>] sys_write+0x3d/0x70
Nov  1 16:12:32 doron-linux kernel: [52853.167755]  [<c010336c>] syscall_call+0x7/0xb
Nov  1 16:12:32 doron-linux kernel: [52853.167758] ---[ end trace f67a3134c1f67b25 ]---
Nov  1 16:12:32 doron-linux kernel: [52853.167787] PM: Finishing wakeup.
Nov  1 16:12:32 doron-linux kernel: [52853.167789] Restarting tasks ... done.

I'm enchanted to know all that. 
first time I saw it I forced an fsck and rebooted, nothing to report.

---

### Post by Tuomas on 2009-11-02
I just got exactly the same error. I don't notice anything unusual, and I'm still connected to the internet. I've never seen this message before. I've been using 8.10 until today when I installed 9.10.

---

### Post by bodhi.zazen on 2009-11-02
If you search Launchpad there are tons of bug reports on this, I have not seen that there is any single problem or fix.

---

### Post by rosswmcgee on 2009-11-02
Yes I have bug 422536, and am running amd 64 bit. I wonder if a clean install would 

fix it? I did an upgrade and all else is well. Or could I delete the crash report file? If so how?

---

### Post by slumbergod on 2009-11-02
I had a serious kernel error a couple of days ago. It really annoyed me because I couldn't actually work out what caused it. In the end, I decided it must have been related to my wireless network crashing. Everything seemed perfectly fine but I rebooted just in case.

---

### Post by wildweathel on 2009-11-02
"Your system encountered a serious kernel problem" is a *generic* error message.  It means "something went wrong,"  not "you're experiencing exactly the same issue that wildweathel and uknowho008 solved." 

(If you are, make sure your ethernet cable is plugged into the jack it should be, because that's what fixed it.)

If you're experiencing a problem with bug [#422536]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422536"), just be patient, updates should fix it soon.  If you're having trouble with something else, please start a new thread and then feel free to PM me.  I can't guarantee I'll have time to help, but I'll try.  Thank you.

---

### Post by jest0r on 2010-02-06
I have the same problem where my computer is telling me that i have a serious kernel problem. I have my computer dual booted with windows 7 and Ubuntu 9.10. And whenever I get that message my internet signal stops working, and its really annoying because I'm trying to get used to ubuntu, but i keep having to go back and use windows because i cant get anything done. please help. Thanks.

---

### Post by Teddyl3ear on 2010-04-02
I have the same message popping out just after the fresh install of ubuntu 9.10, or usually right after i try to configure my wired network (i have to change to a static ip and also change my MAC address). I'll try to see if updating will do any good before configuring the network.

---

