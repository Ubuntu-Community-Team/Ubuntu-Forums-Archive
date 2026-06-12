---
title: "loud beeping after recover from suspend, no virtual consoles on ctrl+alt+f[1-6], gdm"
date: 2010-01-02
forum: General Help
---

### Post by fraktalek on 2010-01-02
Hi,

I just want to report a problem I've just (hopefully) solved.

Symptoms: 
[LIST]
[*]loud beeping on recover from suspend
[*]can't switch to virtual consoles (ctrl+alt+f[1-6])
[*]gdm starting a bit strangely during boot (blank screen, had to do Alt+F7 to get the login screen, etc.)
[/LIST]

HW: 
[LIST]
[*] Dell Latitude D630, 
[*] 01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 135M (rev a1)
[/LIST]
SW: Karmic Koala 9.10
 
It started hapenning perhaps after a bios upgrade (because of fan problems after upgrading to 9.10).

When recovering from suspend the laptop's speaker would produce several loud beeping noises. The beeping should be indicative of errors during the recover but I didn't notice anything special in any logs, perhaps except for (/var/log/kern.log):

```

[ 4257.571712] PM: resume devices took 10.208 seconds
[ 4257.571714] ------------[ cut here ]------------
[ 4257.571721] WARNING: at /build/buildd/linux-2.6.31/kernel/power/suspend_test.c:53 suspend_test_finish+0x84/0x90()
[ 4257.571723] Hardware name: Latitude D630                   
[ 4257.571725] Component: resume devices, time: 10208
[ 4257.571726] Modules linked in: binfmt_misc ppdev bridge stp bnep snd_hda_codec_idt snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss arc4 snd_pcm ecb snd_seq_dummy snd_seq_oss snd_seq_midi iwl3945 iwlcore mac80211 iptable_filter led_class dell_wmi ip_tables snd_rawmidi x_tables pcmcia snd_seq_midi_event snd_seq snd_timer snd_seq_device coretemp joydev dell_laptop dcdbas psmouse yenta_socket rsrc_nonstatic serio_raw pcmcia_core sbp2 snd soundcore snd_page_alloc cfg80211 btusb nvidia(P) lp parport i8k dm_raid45 xor uvesafb usbhid ohci1394 ieee1394 tg3 intel_agp agpgart video output
[ 4257.571769] Pid: 4047, comm: pm-suspend Tainted: P           2.6.31-17-generic #54-Ubuntu
[ 4257.571772] Call Trace:
[ 4257.571777]  [<c01450fd>] warn_slowpath_common+0x6d/0xa0
[ 4257.571781]  [<c0174e34>] ? suspend_test_finish+0x84/0x90
[ 4257.571784]  [<c0174e34>] ? suspend_test_finish+0x84/0x90
[ 4257.571787]  [<c0145176>] warn_slowpath_fmt+0x26/0x30
[ 4257.571791]  [<c0174e34>] suspend_test_finish+0x84/0x90
[ 4257.571794]  [<c0174c1f>] suspend_devices_and_enter+0x9f/0xd0
[ 4257.571797]  [<c056e92c>] ? printk+0x18/0x1c
[ 4257.571800]  [<c0174d09>] enter_state+0xb9/0xf0
[ 4257.571804]  [<c01743fd>] state_store+0x6d/0xb0
[ 4257.571807]  [<c0174390>] ? state_store+0x0/0xb0
[ 4257.571811]  [<c0311fb0>] kobj_attr_store+0x20/0x30
[ 4257.571815]  [<c0239790>] sysfs_write_file+0x90/0x100
[ 4257.571819]  [<c01e792a>] vfs_write+0x9a/0x190
[ 4257.571822]  [<c0239700>] ? sysfs_write_file+0x0/0x100
[ 4257.571826]  [<c057325b>] ? do_page_fault+0x19b/0x380
[ 4257.571829]  [<c01e83ed>] sys_write+0x3d/0x70
[ 4257.571832]  [<c010336c>] syscall_call+0x7/0xb
[ 4257.571834] ---[ end trace 0e2a8c97be9eaeb5 ]---
[ 4257.572128] PM: Finishing wakeup.

```

Threads about a similar problem:
[LIST]
[*][Weird biping after wakup from suspend ]("http://ubuntuforums.org/showthread.php?t=798236")
[*][pangolin laptop beeping noise ]("http://ubuntuforums.org/showthread.php?t=1318521")
[/LIST]

A bug report about the warning:
[LIST][*][URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/464552"]
suspend_test_finish warning triggers too easily, increase timeout to match mainline times[/URL]
[/LIST]

Then I also noticed that I couldn't switch to a virtual console using CTRL+ALT+F[1-6]

Thread about a similar problem:
[LIST][*][No Virtual Terminals in Gutsy]("http://ubuntuforums.org/showthread.php?t=582962")
[/LIST]

A related bug report:
[LIST][*][URL="https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910"]
Blank ttys when using vesafb (vga=xxx)[/URL]
[/LIST]

I tried the fix suggested in the bug report, that is:
> TJ  wrote on 2007-09-09:  	  #15

Confirming John Yate's fix with Gusty Tribe-5 64-bit:

1. Add fbcon to /etc/initramfs-tools/modules
2. Update initrd.img
3. Restart

$ sudo sh -c "echo 'fbcon' >>/etc/initramfs-tools/modules"
$ sudo update-initramfs -u


So far this seems to have fixed all the problems described above. Beeping is gone, virtual consoles work again and booting works normally.

Originally I was also concerned it may be a overheating problem of the graphics card (Latitude D630 is known for it), hopefully it is not the case.

---

