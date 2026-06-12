---
title: "Random freezes for like a couple of minutes"
date: 2009-08-25
forum: General Help
---

### Post by jaansson on 2009-08-25
Hello! I've seen lot's of posts about the computer freezes, but I haven't found anything like mine really. So, I'm running Jaunty with a ati HD3200. I know that the HD series is not fully supported yet. I should probably tell you that I'm running the catalyst drivers atm as well, but would love to change to an open source, but I just can't find one that really supports my card. And with the ati/radeon ones it doesn't actually change, but it still keep going with the mesa or vesa or whatever it's called. So basicly when I'm running like any program, like firefox and music at the same time, my computer freezes after a while. Then after like 5mins it start working fine again. Same if I'm playing like any game like for example supertux. then it freezes after like 10-15mins, then I sometimes have to do a restart. This does not happen with the standard driver that comes with Ubuntu, but then I can't play games like supertux as the 3D isn't enabled, so I don't know, maybe it would freeze if I could actually play it.

So I know that catalyst is closed source, but I still thought I should ask. Maybe someone knows something that could be useful.

Oh, right! I also should tell you that my ram isn't raising when this happens. Nor does the CPU usage.

---

### Post by P4man on 2009-08-25
is the mouse frozen as well when this happens? Can you check in your log files if you see any hint of a problem there after it happened (system > adminstration > log file viewer.

BTW, you must be a patient man. If my PC would lock up for anything near 5 minutes, I would have long pressed the reset button and would never have noticed it started working again!

---

### Post by jaansson on 2009-08-25
Haha, it's more that I try to figure out how I can stop the freeze than being patient :) The mouse is not frozen during this time, and actually I maybe should not call it freezing, more like slowing down very much. Because all my applications do freeze, but the rest is just terribly slow. Like going in to the menus at the top, the "Applications", "Places" and "System" ones, that actually work, but it's responding terribly slow. Oh, and if I have my  mouse just still somewhere, then nothing happens, but when I move it around then it's actually thinking and stuff are starting to happen slowly.

I will check my logfile next time it happens. I will try to provoke it to happen now, so it should be soon ;)

---

### Post by cocopuffz on 2009-08-25
I have the nvidia 9600gt but I was getting the same issues when running the open source drivers. My system would get real sluggish. Scrolling webpages was gittery. Movies would occaisionally have hiccups, pause and then resume etc etc..

Generally the experience wasn't awesome. I uninstalled the open source drivers, installed the proprietary ones and voila. Perfect system since.

I saw via Twitter than the new ATI drivers were just released. You might wanna give those a go.

[http://www.theinquirer.net/inquirer/news/1529490/ati-updates-linux-graphics-display-drivers](http://www.theinquirer.net/inquirer/news/1529490/ati-updates-linux-graphics-display-drivers)

---

### Post by jaansson on 2009-08-25
Weird, because it's the prop. drivers that I have already, and I have this problem with them. Also, I already have the newest drivers, and have had the same problem both with earlier drivers and ubuntu releases :( Thanks anyway, all tips and thoughts are highly welcome!

So, no I have had one of these little freezes again. This was in my log:

```
Aug 26 07:45:53 danne-laptop kernel: [31956.537793] Clocksource tsc unstable (delta = -620078292 ns)
Aug 26 07:45:53 danne-laptop kernel: [31956.540022] BUG: soft lockup - CPU#0 stuck for 231s! [pulseaudio:3316]
Aug 26 07:45:53 danne-laptop kernel: [31956.540028] Modules linked in: ppp_deflate zlib_deflate bsd_comp ppp_async crc_ccitt binfmt_misc ppdev bridge stp bnep input_polldev lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq fglrx(P) snd_timer snd_seq_device leds_hp_disk led_class uvcvideo psmouse joydev i2c_piix4 agpgart pcspkr video compat_ioctl32 serio_raw snd soundcore option lis3lv02d usbserial ieee80211_crypt_tkip videodev output btusb snd_page_alloc v4l1_compat wl(P) ieee80211_crypt shpchp usb_storage sky2 fbcon tileblit font bitblit softcursor
Aug 26 07:45:53 danne-laptop kernel: [31956.540096] 
Aug 26 07:45:53 danne-laptop kernel: [31956.540103] Pid: 3316, comm: pulseaudio Tainted: P           (2.6.28-15-generic #49-Ubuntu) HP Compaq 6735s
Aug 26 07:45:53 danne-laptop kernel: [31956.540110] EIP: 0060:[<f7ed2381>] EFLAGS: 00000246 CPU: 0
Aug 26 07:45:53 danne-laptop kernel: [31956.540150] EIP is at wlc_1160+0x1/0x7d [wl]
Aug 26 07:45:53 danne-laptop kernel: [31956.540155] EAX: f5d64000 EBX: 00000001 ECX: 00000001 EDX: 00000003
Aug 26 07:45:53 danne-laptop kernel: [31956.540159] ESI: f5d64000 EDI: 00000000 EBP: f63fd800 ESP: f4cbfe48
Aug 26 07:45:53 danne-laptop kernel: [31956.540164]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Aug 26 07:45:53 danne-laptop kernel: [31956.540168] CR0: 80050033 CR2: af43e028 CR3: 34c0a000 CR4: 00000690
Aug 26 07:45:53 danne-laptop kernel: [31956.540173] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Aug 26 07:45:53 danne-laptop kernel: [31956.540177] DR6: ffff0ff0 DR7: 00000400
Aug 26 07:45:53 danne-laptop kernel: [31956.540180] Call Trace:
Aug 26 07:45:53 danne-laptop kernel: [31956.540217]  [<f7edf932>] ? wlc_809+0x5e6/0x8a8 [wl]
Aug 26 07:45:53 danne-laptop kernel: [31956.540253]  [<f7f2d98d>] ? wlc_705+0x2af/0x2b7 [wl]
Aug 26 07:45:53 danne-laptop kernel: [31956.540288]  [<f7f2db17>] ? wlc_dpc+0x182/0x4bb [wl]
Aug 26 07:45:53 danne-laptop kernel: [31956.540301]  [<c0140000>] ? adjust_resource+0x60/0xb0
Aug 26 07:45:53 danne-laptop kernel: [31956.540326]  [<f7ebf1e9>] ? wl_dpc+0x39/0xc4 [wl]
Aug 26 07:45:53 danne-laptop kernel: [31956.540334]  [<c013ee18>] ? tasklet_action+0x78/0x100
Aug 26 07:45:53 danne-laptop kernel: [31956.540342]  [<c013f297>] ? __do_softirq+0x97/0x170
Aug 26 07:45:53 danne-laptop kernel: [31956.540348]  [<c0120411>] ? hpet_interrupt_handler+0x11/0x30
Aug 26 07:45:53 danne-laptop kernel: [31956.540368]  [<f89c0c00>] ? snd_pcm_playback_ioctl+0x0/0x50 [snd_pcm]
Aug 26 07:45:53 danne-laptop kernel: [31956.540376]  [<c013f3cd>] ? do_softirq+0x5d/0x60
Aug 26 07:45:53 danne-laptop kernel: [31956.540382]  [<c013f545>] ? irq_exit+0x55/0x90
Aug 26 07:45:53 danne-laptop kernel: [31956.540389]  [<c0106853>] ? do_IRQ+0x83/0xa0
Aug 26 07:45:53 danne-laptop kernel: [31956.540397]  [<c01cab87>] ? sys_ioctl+0x47/0x70
Aug 26 07:45:53 danne-laptop kernel: [31956.540402]  [<c01051f3>] ? common_interrupt+0x23/0x30
```


It was in my syslog, kern.log and messages

It also said this in my user.log just before/when it started:

```
Aug 26 07:40:54 danne-laptop last message repeated 5595 times
```

Oh, I just noticed, looking at the times that the freeze was EXACTLY (well, 1 second away from) 5 minutes. Weird?

---

### Post by P4man on 2009-08-25
> Aug 26 07:45:53 danne-laptop kernel: [31956.537793] Clocksource tsc unstable (delta = -620078292 ns)


That may be it. Seen that (too) often. Crappy bios or crappy linux programers, depending who you ask :). But there is good chance we can solve it.

Op en a terminal and type (or rather paste):

```
cat /sys/devices/system/clocksource/clocksource0/*
```

That should give something like this:

```
bob@bob-desktop:~$ cat /sys/devices/system/clocksource/clocksource0/*
tsc acpi_pm jiffies 
tsc

```

Those are available clocksources. And tsc in your case is no good, so we can try another one. In my case, i could try acpi_pm and jiffies. Yours is probably the same, but could differ.

Anyway, to change that, edit the grub menu. 

```
gskudo gedit /boot/grub/menu.lst
```

Find your most recent kernel entry. Something like:

> 
## ## End Default Options ##

title		Ubuntu 9.04  kernel 2.6.28-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet


Copy that entire section, so you have it twice. Should the new clocksource fail to boot, you can select the previous entry in grub.  Then edit it to add the new kernel parameter regarding the clocksource (and change the description so you can make it out) :

> 
## ## End Default Options ##

title		ubuntu 9.04 **test using acpi_pm**  
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro quiet splash** clocksouce=acpi_pm**
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04  kernel 2.6.28-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet


You can try that for each clocksource you found earlier.  reboot, select the appropriate line in grub menu. Should booting fail, then select the second line with the original settings.

let me know if that helps.

---

### Post by jaansson on 2009-08-25
Okay, so now I've tried all three of hpet, acpi_pm and jiffies. After around 1h with hpet I thought that it was actually working! But then it froze. Got some new log messages though. 2 that I found interresting, but I have no idea what to do with them really, so here they are.

```
Aug 26 10:51:24 danne-laptop pulseaudio[3297]: asyncq.c: q overrun, queuing locally
Aug 26 10:51:24 danne-laptop last message repeated 1497 times
```

```
Aug 26 10:56:41 danne-laptop kernel: [ 6918.654959] ACPI: Transitioning device [FAN2] to D0
Aug 26 10:56:41 danne-laptop kernel: [ 6918.654959] ACPI: Unable to turn cooling device [f6c1bc48] 'on'
```

I also got this, even though I was running hpet:

```
danne-laptop kernel: [ 3736.149436] Clocksource tsc unstable (delta = 299948791647 ns)
```

---

### Post by P4man on 2009-08-26
You can check which clocksource you are using by typing
> 
cat /sys/devices/system/clocksource/clocksource0/current_clocksource 

You might still see kernel messages about other clocksources though.
> 
Aug 26 10:56:41 danne-laptop kernel: [ 6918.654959] ACPI: Transitioning device [FAN2] to D0
Aug 26 10:56:41 danne-laptop kernel: [ 6918.654959] ACPI: Unable to turn cooling device [f6c1bc48] 'on'

thats potentially interesting indeed. Although it may be than fan2 is simply not connected (motherboard header not in use). Can you check if your fans are actually running? Can you check in the bios if your temps are out of the ordinary?

As for the pulseaudio error.. googling it returns this:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/354220](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/354220)

Where you running virtualbox or some other virtualization app?

Lastly, if you feel like testing some more kernel options, have a look at these:

[https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options)

---

### Post by pveurshout on 2009-09-20
> **jaansson said:**
> Weird, because it's the prop. drivers that I have already, and I have this problem with them. Also, I already have the newest drivers, and have had the same problem both with earlier drivers and ubuntu releases :( Thanks anyway, all tips and thoughts are highly welcome!

So, no I have had one of these little freezes again. This was in my log:

```
Aug 26 07:45:53 danne-laptop kernel: [31956.537793] Clocksource tsc unstable (delta = -620078292 ns)
Aug 26 07:45:53 danne-laptop kernel: [31956.540022] BUG: soft lockup - CPU#0 stuck for 231s! [pulseaudio:3316]
Aug 26 07:45:53 danne-laptop kernel: [31956.540028] Modules linked in: ppp_deflate zlib_deflate bsd_comp ppp_async crc_ccitt binfmt_misc ppdev bridge stp bnep input_polldev lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq fglrx(P) snd_timer snd_seq_device leds_hp_disk led_class uvcvideo psmouse joydev i2c_piix4 agpgart pcspkr video compat_ioctl32 serio_raw snd soundcore option lis3lv02d usbserial ieee80211_crypt_tkip videodev output btusb snd_page_alloc v4l1_compat wl(P) ieee80211_crypt shpchp usb_storage sky2 fbcon tileblit font bitblit softcursor
Aug 26 07:45:53 danne-laptop kernel: [31956.540096] 
Aug 26 07:45:53 danne-laptop kernel: [31956.540103] Pid: 3316, comm: pulseaudio Tainted: P           (2.6.28-15-generic #49-Ubuntu) HP Compaq 6735s
Aug 26 07:45:53 danne-laptop kernel: [31956.540110] EIP: 0060:[<f7ed2381>] EFLAGS: 00000246 CPU: 0
Aug 26 07:45:53 danne-laptop kernel: [31956.540150] EIP is at wlc_1160+0x1/0x7d [wl]
Aug 26 07:45:53 danne-laptop kernel: [31956.540155] EAX: f5d64000 EBX: 00000001 ECX: 00000001 EDX: 00000003
Aug 26 07:45:53 danne-laptop kernel: [31956.540159] ESI: f5d64000 EDI: 00000000 EBP: f63fd800 ESP: f4cbfe48
Aug 26 07:45:53 danne-laptop kernel: [31956.540164]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Aug 26 07:45:53 danne-laptop kernel: [31956.540168] CR0: 80050033 CR2: af43e028 CR3: 34c0a000 CR4: 00000690
Aug 26 07:45:53 danne-laptop kernel: [31956.540173] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Aug 26 07:45:53 danne-laptop kernel: [31956.540177] DR6: ffff0ff0 DR7: 00000400
Aug 26 07:45:53 danne-laptop kernel: [31956.540180] Call Trace:
Aug 26 07:45:53 danne-laptop kernel: [31956.540217]  [<f7edf932>] ? wlc_809+0x5e6/0x8a8 [wl]
Aug 26 07:45:53 danne-laptop kernel: [31956.540253]  [<f7f2d98d>] ? wlc_705+0x2af/0x2b7 [wl]
Aug 26 07:45:53 danne-laptop kernel: [31956.540288]  [<f7f2db17>] ? wlc_dpc+0x182/0x4bb [wl]
Aug 26 07:45:53 danne-laptop kernel: [31956.540301]  [<c0140000>] ? adjust_resource+0x60/0xb0
Aug 26 07:45:53 danne-laptop kernel: [31956.540326]  [<f7ebf1e9>] ? wl_dpc+0x39/0xc4 [wl]
Aug 26 07:45:53 danne-laptop kernel: [31956.540334]  [<c013ee18>] ? tasklet_action+0x78/0x100
Aug 26 07:45:53 danne-laptop kernel: [31956.540342]  [<c013f297>] ? __do_softirq+0x97/0x170
Aug 26 07:45:53 danne-laptop kernel: [31956.540348]  [<c0120411>] ? hpet_interrupt_handler+0x11/0x30
Aug 26 07:45:53 danne-laptop kernel: [31956.540368]  [<f89c0c00>] ? snd_pcm_playback_ioctl+0x0/0x50 [snd_pcm]
Aug 26 07:45:53 danne-laptop kernel: [31956.540376]  [<c013f3cd>] ? do_softirq+0x5d/0x60
Aug 26 07:45:53 danne-laptop kernel: [31956.540382]  [<c013f545>] ? irq_exit+0x55/0x90
Aug 26 07:45:53 danne-laptop kernel: [31956.540389]  [<c0106853>] ? do_IRQ+0x83/0xa0
Aug 26 07:45:53 danne-laptop kernel: [31956.540397]  [<c01cab87>] ? sys_ioctl+0x47/0x70
Aug 26 07:45:53 danne-laptop kernel: [31956.540402]  [<c01051f3>] ? common_interrupt+0x23/0x30
```


It was in my syslog, kern.log and messages

It also said this in my user.log just before/when it started:

```
Aug 26 07:40:54 danne-laptop last message repeated 5595 times
```

Oh, I just noticed, looking at the times that the freeze was EXACTLY (well, 1 second away from) 5 minutes. Weird?

Since this thread has been inactive for about 3 weeks now, I thought I'd ask if your problem may perhaps have been solved by now? I'm currently experiencing both entire freezes (which might be related to using hpet, which I recently forced to disable to see if it makes any difference) and occasionally I'm seeing **the exact same message** as in your dmesg output above, except that it keeps mentioning a different process all the time. Have you been able to figure out what might be causing it (and what it actually means)?

P.S. I all the time see the 'clocksource tsc unstable' message a short while after logging in, though I'm using acpi_pm. Doesn't seem related in my case. I'm not sure if it's possible, but could it be possible that in your case it switches from tsc to another hardware timer at some point and that it is actually the other ("next") hardware timer that causes the problem? Just a thought.

---

### Post by CHaoSlayeR on 2009-10-25
I have exactly the same problem here except that it is KVM that causes those lockups:
```
[506261.132047] BUG: soft lockup - CPU#0 stuck for 107s! [kvm:3500]                                                                                                                
[506261.132055] Modules linked in: radeon drm binfmt_misc tun ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ipt_REJECT xt_tcpudp iptable_filter ip_tables x_tables nfsd auth_rpcgss exportfs kvm_amd kvm video output input_polldev nfs lockd nfs_acl sunrpc bridge stp it87 hwmon_vid lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd i2c_piix4 soundcore snd_page_alloc ohci1394 ieee1394 usbhid r8169 mii raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear fbcon tileblit font bitblit softcursor                                        
[506261.132146] CPU 0:                                                                                                                                                             
[506261.132150] Modules linked in: radeon drm binfmt_misc tun ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ipt_REJECT xt_tcpudp iptable_filter ip_tables x_tables nfsd auth_rpcgss exportfs kvm_amd kvm video output input_polldev nfs lockd nfs_acl sunrpc bridge stp it87 hwmon_vid lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd i2c_piix4 soundcore snd_page_alloc ohci1394 ieee1394 usbhid r8169 mii raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear fbcon tileblit font bitblit softcursor                                        
[506261.132229] Pid: 3500, comm: kvm Not tainted 2.6.28-15-generic #52-Ubuntu                                                                                                      
[506261.132235] RIP: 0010:[<ffffffff8025bfd0>]  [<ffffffff8025bfd0>] run_timer_softirq+0x160/0x260                                                                                 
[506261.132251] RSP: 0018:ffffffff80a92e90  EFLAGS: 00000206                                                                                                                       
[506261.132255] RAX: ffffffff80a92eb0 RBX: ffffffff80a92ef0 RCX: ffffffff805d5cd0                                                                                                  
[506261.132260] RDX: ffffffff80a92eb0 RSI: 0000000000000001 RDI: ffffffff80ae5900                                                                                                  
[506261.132265] RBP: ffffffff80a92e10 R08: ffffffff80b772e0 R09: 0000000000000000                                                                                                  
[506261.132270] R10: ffff8800a75ca000 R11: 0000000000000000 R12: ffffffff80212bf3                                                                                                  
[506261.132275] R13: ffffffff80a92e10 R14: ffffffff80ae5900 R15: ffffffff80b772a8                                                                                                  
[506261.132280] FS:  00000000fffe0000(0000) GS:ffffffff80a9b000(0000) knlGS:000007fffffde000                                                                                       
[506261.132285] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033                                                                                                                  
[506261.132290] CR2: 00007f3bac5dc000 CR3: 00000001244ad000 CR4: 00000000000006a0                                                                                                  
[506261.132295] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000                                                                                                  
[506261.132300] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400                                                                                                  
[506261.132304] Call Trace:                                                                                                                                                        
[506261.132307]  <IRQ>  [<ffffffff80256c4c>] ? __do_softirq+0x9c/0x170                                                                                                             
[506261.132323]  [<ffffffff80213d8c>] ? call_softirq+0x1c/0x30                                                                                                                     
[506261.132330]  [<ffffffff80214ffd>] ? do_softirq+0x5d/0xa0                                                                                                                       
[506261.132336]  [<ffffffff802569cd>] ? irq_exit+0x8d/0xa0                                                                                                                         
[506261.132343]  [<ffffffff802152c5>] ? do_IRQ+0xc5/0x110                                                                                                                          
[506261.132349]  [<ffffffff80212bf3>] ? ret_from_intr+0x0/0x29                                                                                                                     
[506261.132352]  <EOI>  [<ffffffffa0345168>] ? vcpu_enter_guest+0x238/0x3f0 [kvm]                                                                                                  
[506261.132412]  [<ffffffffa034515a>] ? vcpu_enter_guest+0x22a/0x3f0 [kvm]                                                                                                         
[506261.132421]  [<ffffffff80268ae0>] ? autoremove_wake_function+0x0/0x40                                                                                                          
[506261.132447]  [<ffffffffa0345389>] ? __vcpu_run+0x69/0x2d0 [kvm]                                                                                                                
[506261.132473]  [<ffffffffa0347b0a>] ? kvm_arch_vcpu_ioctl_run+0x8a/0x1f0 [kvm]                                                                                                   
[506261.132497]  [<ffffffffa033c5d2>] ? kvm_vcpu_ioctl+0x2e2/0x5a0 [kvm]                                                                                                           
[506261.132507]  [<ffffffff802106c5>] ? __switch_to+0x2a5/0x490                                                                                                                    
[506261.132516]  [<ffffffff802f65e1>] ? vfs_ioctl+0x31/0xa0                                                                                                                        
[506261.132525]  [<ffffffff8069996c>] ? thread_return+0x37/0x36b                                                                                                                   
[506261.132532]  [<ffffffff802f6995>] ? do_vfs_ioctl+0x75/0x230                                                                                                                    
[506261.132539]  [<ffffffff802f6be9>] ? sys_ioctl+0x99/0xa0                                                                                                                        
[506261.132546]  [<ffffffff8021253a>] ? system_call_fastpath+0x16/0x1b                                                                                                             
[532487.816057] ------------[ cut here ]------------                                                                                                                               
[532487.816065] WARNING: at /build/buildd/linux-2.6.28/net/sched/sch_generic.c:226 dev_watchdog+0x270/0x280()                                                                      
[532487.816071] NETDEV WATCHDOG: eth1 (r8169): transmit timed out                                                                                                                  
[532487.816075] Modules linked in: radeon drm binfmt_misc tun ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ipt_REJECT xt_tcpudp iptable_filter ip_tables x_tables nfsd auth_rpcgss exportfs kvm_amd kvm video output input_polldev nfs lockd nfs_acl sunrpc bridge stp it87 hwmon_vid lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd i2c_piix4 soundcore snd_page_alloc ohci1394 ieee1394 usbhid r8169 mii raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear fbcon tileblit font bitblit softcursor                                        
[532487.816168] Pid: 0, comm: swapper Not tainted 2.6.28-15-generic #52-Ubuntu                                                                                                     
[532487.816173] Call Trace:                                                                                                                                                        
[532487.816177]  <IRQ>  [<ffffffff80250ad7>] warn_slowpath+0xb7/0xf0                                                                                                               
[532487.816195]  [<ffffffff8026c819>] ? ktime_get_ts+0x59/0x60                                                                                                                     
[532487.816203]  [<ffffffff80417b6a>] ? __next_cpu+0x1a/0x30                                                                                                                       
[532487.816210]  [<ffffffff8024782c>] ? find_busiest_group+0x1dc/0x9a0                                                                                                             
[532487.816219]  [<ffffffff80270bb9>] ? getnstimeofday+0x59/0xe0                                                                                                                   
[532487.816225]  [<ffffffff8026c819>] ? ktime_get_ts+0x59/0x60                                                                                                                     
[532487.816232]  [<ffffffff8026e88c>] ? sched_clock_cpu+0xcc/0x160                                                                                                                 
[532487.816239]  [<ffffffff8041de5a>] ? strlcpy+0x4a/0x60                                                                                                                          
[532487.816247]  [<ffffffff805c8550>] dev_watchdog+0x270/0x280                                                                                                                     
[532487.816254]  [<ffffffff80270bb9>] ? getnstimeofday+0x59/0xe0                                                                                                                   
[532487.816260]  [<ffffffff8026c819>] ? ktime_get_ts+0x59/0x60                                                                                                                     
[532487.816268]  [<ffffffff8022d42f>] ? hpet_msi_next_event+0xf/0x20                                                                                                               
[532487.816276]  [<ffffffff802739af>] ? clockevents_program_event+0x4f/0x90                                                                                                        
[532487.816283]  [<ffffffff805c82e0>] ? dev_watchdog+0x0/0x280                                                                                                                     
[532487.816291]  [<ffffffff8025bfe9>] run_timer_softirq+0x179/0x260                                                                                                                
[532487.816297]  [<ffffffff80256c4c>] __do_softirq+0x9c/0x170                                                                                                                      
[532487.816304]  [<ffffffff80213d8c>] call_softirq+0x1c/0x30                                                                                                                       
[532487.816310]  [<ffffffff80214ffd>] do_softirq+0x5d/0xa0                                                                                                                         
[532487.816316]  [<ffffffff802569cd>] irq_exit+0x8d/0xa0                                                                                                                           
[532487.816322]  [<ffffffff802152c5>] do_IRQ+0xc5/0x110                                                                                                                            
[532487.816328]  [<ffffffff80212bf3>] ret_from_intr+0x0/0x29                                                                                                                       
[532487.816331]  <EOI>  [<ffffffff8022e856>] ? native_safe_halt+0x6/0x10                                                                                                           
[532487.816345]  [<ffffffff8021a9fd>] ? default_idle+0x4d/0x50                                                                                                                     
[532487.816352]  [<ffffffff8021aa51>] ? c1e_idle+0x51/0x130                                                                                                                        
[532487.816359]  [<ffffffff8069ecb5>] ? atomic_notifier_call_chain+0x15/0x20                                                                                                       
[532487.816367]  [<ffffffff80210e85>] ? cpu_idle+0x65/0xc0
[532487.816374]  [<ffffffff806878cc>] ? rest_init+0x5c/0x70
[532487.816379] ---[ end trace 434c9284936645ed ]---
[532487.835836] r8169: eth1: link up
```


I first followed a suggestion on another thread to upgrade the BIOS and indeed it seemed to fix the problem.

Well, just for a few days. At least those lockups are less frequent now on our systems so that I think it has to do something with ACPI and Power Management.

Has anyone drilled this down to the real cause yet?

Thanx,

C]-[aoZ

---

### Post by ivotedforkodos on 2009-11-25
I'm wondering if my problem is related? It sounds like my crashes are more severe, but I'm also using an ATI card with the proprietary drivers and experiencing a timed freeze. 

[http://ubuntuforums.org/showthread.php?t=1336842](http://ubuntuforums.org/showthread.php?t=1336842)

---

### Post by mickcalcara on 2009-11-27
I have the same problem with SuperTux and TuxPaint when exiting. Any solutions? I am using a GeForce 7300 with the Nividia drivers 185.18.36.

Thanks

---

