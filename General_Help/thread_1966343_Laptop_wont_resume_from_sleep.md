---
title: "Laptop wont resume from sleep"
date: 2012-04-27
forum: General Help
---

### Post by sky5564 on 2012-04-27
So i have installed 12.04 on my acer aspire 5253-bz893 laptop, Everything is working except the sleep feature, It will go into sleep but it will not come out of sleep, I just get a black screen.

Anyone else have this problem?

Sleep worked fine on the live cd but after i installed it no longer works.

---

### Post by sky5564 on 2012-04-27
chika chika bump bump..:guitar:

---

### Post by sky5564 on 2012-04-30
Heyyyy yoooouuuuuu guyssss.

---

### Post by Quackers on 2012-04-30
I get this sometimes on my Sony Vaio. It's probably ACPI related. As it's only occasional I can live with it.

---

### Post by sky5564 on 2012-04-30
> **Quackers said:**
> I get this sometimes on my Sony Vaio. It's probably ACPI related. As it's only occasional I can live with it.

Got any recommendations for me? I could probably fix it myself if someone could just tell me where to look.

---

### Post by Quackers on 2012-04-30
No idea where to start really. ACPI deals with your pc's hardware and settings, as I understand it. It's not an area I would want to get in to. The down side could be disastrous.
Can you manage without sleep? I think I would.

You can keep the system fully updated. That way updates in the future may yield a result.

---

### Post by williejones on 2012-04-30
> **sky5564 said:**
> Got any recommendations for me? I could probably fix it myself if someone could just tell me where to look.

If you have an intel video card you can try the following

```
sudo gedit /etc/rc.local
setpci -s 00:02.0 F4.B=00
```


Before you try the above command let's see what your video card is

> lspci | grep VGA 

Here is mine


> terry@terry-eMachines-E725:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)


---

### Post by sky5564 on 2012-04-30
> **williejones said:**
> If you have an intel video card you can try the following

```
sudo gedit /etc/rc.local
setpci -s 00:02.0 F4.B=00
```


Before you try the above command let's see what your video card is



Here is mine

skilo@ubuntu12:~$ lspci | grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6250]

---

### Post by Toz on 2012-04-30
Perhaps these might help:
- [http://ubuntuforums.org/showthread.php?t=1868270]("http://ubuntuforums.org/showthread.php?t=1868270")
- [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/926792]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/926792")

---

### Post by sky5564 on 2012-04-30
> **Toz said:**
> Perhaps these might help:
- [http://ubuntuforums.org/showthread.php?t=1868270]("http://ubuntuforums.org/showthread.php?t=1868270")
- [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/926792]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/926792")

Wow thanks, When i searched the forum nothing came up lol.

It seems this is a driver issue and can probably be solved by replacing the proprietary fglrx driver with an opensource one.

Thanks again. :guitar:

---

### Post by williejones on 2012-04-30
> **sky5564 said:**
> skilo@ubuntu12:~$ lspci | grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6250]

In this case do not try my suggestion above.  Perhaps someone with your video card can give better advise.

---

### Post by MarjaE on 2012-05-10
I still use 11.04 because of arm injuries and workflow... My right arm hurts enough after using Gnome 2 and gets even worse after using Unity.

Anyway, I didn't have much trouble with waking the computer from sleep until the latest kernel update. Now I can't wake the computer from sleep, except by hard rebooting [and losing my work]. Because of my injuries, I take long breaks and need to let the thing sleep.

---

### Post by Ctulhu on 2012-07-05
Same thing here, which is really annoying: Hibernate is not even offered as a shutdown option, and the computer doesn't wake up from sleep. Kubuntu 12.04 x64 on a Dell Latitude E6500 ...

---

### Post by Toz on 2012-07-05
> **Ctulhu said:**
> Same thing here, which is really annoying: Hibernate is not even offered as a shutdown option, and the computer doesn't wake up from sleep. Kubuntu 12.04 x64 on a Dell Latitude E6500 ...

Hibernate is disabled by default in 12.04. See: [http://askubuntu.com/questions/94754/how-to-enable-hibernation-in-12-04]("http://askubuntu.com/questions/94754/how-to-enable-hibernation-in-12-04") for info on how to re-enable hibernate.

As for the sleep issue, can you provide more information:
1. The results of:
```
cat /proc/cmdline
```


2. The contents of your /var/log/pm-suspend.log file:
```
pasteinit /var/log/pm-suspend.log
```
...and post back the link


3. And the results of this command:
```
cat /var/log/syslog* | grep PM:
```

---

### Post by Ctulhu on 2012-07-05
Here's the info, hope it helps!. Thanks for looking into this! :-)

Latitude-E6500:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-26-generic root=UUID=afeb19b5-e9c2-4005-b301-44d9656f39a4 ro quiet splash vt.handoff=7

Latitude-E6500:~$ pastebinit /var/log/pm-suspend.log
[http://paste.ubuntu.com/1076560/](http://paste.ubuntu.com/1076560/)

Latitude-E6500:~$ cat /var/log/syslog* | grep PM:
Jul  4 23:26:13 Latitude-E6500 kernel: [  158.895681] PM: Syncing filesystems ... done.
Jul  4 23:26:13 Latitude-E6500 kernel: [  158.902472] PM: Preparing system for mem sleep
Jul  4 23:26:22 Latitude-E6500 kernel: [  158.936255] PM: Entering mem sleep
Jul  4 23:26:22 Latitude-E6500 kernel: [  159.080050] PM: suspend of drv:snd_hda_intel dev:0000:00:1b.0 complete after 119.847 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  159.515137] PM: suspend of drv:sd dev:0:0:0:0 complete after 578.176 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  159.515172] PM: suspend of drv:scsi dev:target0:0:0 complete after 578.178 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  159.515204] PM: suspend of drv:scsi dev:host0 complete after 561.708 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  159.528037] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 567.934 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  159.528070] PM: suspend of drv: dev:pci0000:00 complete after 567.567 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  159.528101] PM: suspend of devices complete after 591.518 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  159.528104] PM: suspend devices took 0.592 seconds
Jul  4 23:26:22 Latitude-E6500 kernel: [  159.559560] PM: late suspend of devices complete after 31.460 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  159.580726] PM: Saving platform NVS memory
Jul  4 23:26:22 Latitude-E6500 kernel: [  159.684669] PM: Restoring platform NVS memory
Jul  4 23:26:22 Latitude-E6500 kernel: [  159.816456] PM: early resume of devices complete after 28.022 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  159.954499] PM: resume of drv:e1000e dev:0000:00:19.0 complete after 137.965 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  159.956155] PM: resume of drv:hub dev:7-0:1.0 complete after 116.304 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  159.956162] PM: resume of drv: dev:ep_00 complete after 111.566 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  159.956167] PM: resume of drv: dev:ep_81 complete after 111.914 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  159.956249] PM: resume of drv:hub dev:4-0:1.0 complete after 116.454 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  159.956256] PM: resume of drv: dev:ep_81 complete after 116.458 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  159.956265] PM: resume of drv: dev:ep_00 complete after 116.463 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  159.964086] PM: resume of drv:hub dev:8-0:1.0 complete after 119.454 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  159.964095] PM: resume of drv: dev:ep_00 complete after 119.434 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  159.964101] PM: resume of drv: dev:ep_81 complete after 119.454 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.060104] PM: resume of drv: dev:ep_00 complete after 220.280 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.060110] PM: resume of drv:hub dev:5-0:1.0 complete after 220.294 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.060117] PM: resume of drv: dev:ep_00 complete after 220.277 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.060122] PM: resume of drv: dev:ep_81 complete after 220.303 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.060130] PM: resume of drv:hub dev:6-0:1.0 complete after 220.297 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.060136] PM: resume of drv: dev:ep_00 complete after 220.351 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.060145] PM: resume of drv: dev:ep_81 complete after 220.308 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.060153] PM: resume of drv:hub dev:3-0:1.0 complete after 220.374 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.060163] PM: resume of drv: dev:ep_81 complete after 220.381 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.076859] PM: resume of drv:battery dev:PNP0C0A:00 complete after 221.758 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.532070] PM: resume of drv:hub dev:3-1:1.0 complete after 687.323 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.532077] PM: resume of drv: dev:ep_00 complete after 687.302 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.532090] PM: resume of drv: dev:ep_81 complete after 687.329 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.536833] PM: resume of drv:btusb dev:3-1.3:1.0 complete after 691.842 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.536842] PM: resume of drv:btusb dev:3-1.3:1.1 complete after 691.797 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.536851] PM: resume of drv:usb dev:3-1.3:1.2 complete after 691.765 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.536860] PM: resume of drv:usb dev:3-1.3:1.3 complete after 691.734 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.536865] PM: resume of drv: dev:ep_00 complete after 691.727 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.536870] PM: resume of drv: dev:ep_81 complete after 691.866 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.536874] PM: resume of drv: dev:ep_82 complete after 691.858 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.536879] PM: resume of drv: dev:ep_02 complete after 691.847 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.536884] PM: resume of drv: dev:ep_83 complete after 691.826 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.536889] PM: resume of drv: dev:ep_03 complete after 691.818 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.536894] PM: resume of drv: dev:ep_84 complete after 691.796 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.536899] PM: resume of drv: dev:ep_04 complete after 691.787 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.752194] PM: resume of drv:sd dev:0:0:0:0 complete after 907.516 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.752208] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 907.494 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.752222] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 670.721 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.819342] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 1002.318 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.875869] PM: resume of drv: dev:ep_00 complete after 1031.011 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.875890] PM: resume of drv:usbhid dev:6-1:1.0 complete after 1031.086 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  160.875925] PM: resume of drv: dev:ep_81 complete after 1031.082 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.128855] PM: resume of drv:usb dev:5-1:0.1 complete after 1283.637 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.128868] PM: resume of drv: dev:ep_00 complete after 1283.596 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.128875] PM: resume of drv:usb dev:5-1:0.0 complete after 1283.710 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.128880] PM: resume of drv: dev:ep_82 complete after 1283.643 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.128888] PM: resume of drv: dev:ep_86 complete after 1283.630 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.128893] PM: resume of drv: dev:ep_02 complete after 1283.646 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.128904] PM: resume of drv: dev:ep_81 complete after 1283.727 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.128908] PM: resume of drv: dev:ep_85 complete after 1283.701 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.128913] PM: resume of drv: dev:ep_01 complete after 1283.722 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.431856] PM: resume of drv:uvcvideo dev:5-2:1.1 complete after 1586.530 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.431864] PM: resume of drv: dev:ep_00 complete after 1586.524 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.431873] PM: resume of drv:uvcvideo dev:5-2:1.0 complete after 1586.575 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.431889] PM: resume of drv: dev:ep_83 complete after 1586.578 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.545812] PM: resume of drv: dev:ep_00 complete after 1700.901 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.545832] PM: resume of drv:usbhid dev:3-1.1:1.0 complete after 1700.947 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.545861] PM: resume of drv:generic-usb dev:0003:413C:8157.0002 complete after 669.939 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.545969] PM: resume of drv: dev:ep_81 complete after 1701.072 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.724815] PM: resume of drv: dev:ep_00 complete after 1879.850 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.724836] PM: resume of drv:usb dev:3-1.2:1.0 complete after 1879.898 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.724856] PM: resume of drv: dev:ep_81 complete after 1879.905 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.724862] PM: resume of devices complete after 1908.361 msecs
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.725048] PM: resume devices took 1.908 seconds
Jul  4 23:26:22 Latitude-E6500 kernel: [  161.725083] PM: Finishing wakeup.

---

### Post by Toz on 2012-07-05
According to your /var/log/suspend.log file, suspend/resume worked:
> Running hook /usr/lib/pm-utils/slInitial commandline parameters: 
Wed Jul  4 23:26:09 MDT 2012: Running hooks for suspend.
...
Wed Jul  4 23:26:13 MDT 2012: performing suspend
...
Wed Jul  4 23:26:22 MDT 2012: Awake.
Wed Jul  4 23:26:22 MDT 2012: Running hooks for resume
...


What exaclty is happening when you resume? I'm guessing the lights come on but nothing displays on the screen? If so, try this:

1. Try increasing/decreasing the brightness using the brightness keys
2. Try going to the first tty (Ctrl+Alt+F1). Do you see text? Try going back to the gui screen (Ctrl+Alt+F7). Does it reappear?
3. If you press the Caps Lock key, does the keyboard indicate that it comes on?

---

### Post by Ctulhu on 2012-07-05
What happens is that the hard drive, wifi, and bluetooth light come back on (with the hard drive light flashing/indicating activity). The screen comes on again but is all black with no mouse pointer or anything visible. I did try CTRL-ALT-F1 and CTRL-ALT-F7, which I had seen in other posts, but nothing. The brightness thing can't be it because the screen is much blacker than my brightness keys would ever go, but I will try that and the caps lock again.
Thx!

---

### Post by Toz on 2012-07-05
Do you see any text in Ctrl+Alt+F1?

Another thing to try is to suspend from tty1 and see if it will resume. Go to tty1 (Ctrl+Alt+F1), log in, run:
```
sudo pm-suspend
```
...to initiate suspend. Then resume and see if you get back to the text screen and whether it is visible.

EDIT: Also, while in tty1, can you run this script before and after resume (if possible) to report on the state of your backlight interfaces:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
```

---

### Post by Ctulhu on 2012-07-05
Ok, so both scripts that are out there don't help and jsut now it got really nasty: Upon pressing on the on-button again to resume, the laptop went off and then wouldn't go on anymore unless I take out the battery. (Twice, the caps-lock and the num-lock lights were flashing in unison. Gonna try your suspend from tty1 now ...

---

### Post by Toz on 2012-07-05
> **Ctulhu said:**
> Ok, so both scripts that are out there don't help and jsut now it got really nasty: Upon pressing on the on-button again to resume, the laptop went off and then wouldn't go on anymore unless I take out the battery. (Twice, the caps-lock and the num-lock lights were flashing in unison. Gonna try your suspend from tty1 now ...

I'm sorry, which scripts?

---

### Post by Ctulhu on 2012-07-05
Sorry, that was cryptic. There are two scripts flying around here in forum (<http://ubuntuforums.org/showthread.php?t=1978290>) and I tried both, but they don't work.

So, I can sleep AND then resume from tty1, but after resuming, I can't switch back with CTRL-ALT-F7.

I am now saving your script into /home and will try to run from tty1.

---

### Post by jchiso on 2012-10-15
Has this problem been overcome?  I am stuck in the same situation with this notebook running Precise.  It worked fine in Natty...

---

### Post by Toz on 2012-10-15
> **jchiso said:**
> Has this problem been overcome?  I am stuck in the same situation with this notebook running Precise.  It worked fine in Natty...

@jchiso,
This thread is a little old. It would be a good idea to start a new thread for your specific issues, and please include the following information:
- a complete description of the problem
- the make and model of your computer
- the version of ubuntu that you are running 
- the contents of the /var/log/pm-suspend.log file. An easy method is to run the following command in a terminal window:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated
- and the results of running this command in a terminal:
```
cat /var/log/syslog | grep PM:
```

This should give us a good starting point to begin offering some assistance.

---

### Post by jchiso on 2012-10-16
It's the same problem and PC as the original post, that's why I did not start a new thread ...

[PHP]cat /var/log/syslog | grep PM:
Oct 15 20:43:18 Aspire5253 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Oct 15 20:43:18 Aspire5253 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Oct 15 20:43:18 Aspire5253 kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Oct 15 20:43:18 Aspire5253 kernel: [    0.156663] PM: Registering ACPI NVS region at de649000 (2097152 bytes)
Oct 15 20:43:18 Aspire5253 kernel: [    0.156663] PM: Registering ACPI NVS region at dfdbf000 (1048576 bytes)
Oct 15 20:43:18 Aspire5253 kernel: [    1.448598] PM: Hibernation image not present or could not be loaded.
Oct 16 13:30:47 Aspire5253 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Oct 16 13:30:47 Aspire5253 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Oct 16 13:30:47 Aspire5253 kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Oct 16 13:30:47 Aspire5253 kernel: [    0.156665] PM: Registering ACPI NVS region at de649000 (2097152 bytes)
Oct 16 13:30:47 Aspire5253 kernel: [    0.156665] PM: Registering ACPI NVS region at dfdbf000 (1048576 bytes)
Oct 16 13:30:47 Aspire5253 kernel: [    1.452466] PM: Hibernation image not present or could not be loaded.
Oct 16 14:18:00 Aspire5253 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Oct 16 14:18:00 Aspire5253 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Oct 16 14:18:00 Aspire5253 kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Oct 16 14:18:00 Aspire5253 kernel: [    0.156665] PM: Registering ACPI NVS region at de649000 (2097152 bytes)
Oct 16 14:18:00 Aspire5253 kernel: [    0.156665] PM: Registering ACPI NVS region at dfdbf000 (1048576 bytes)
Oct 16 14:18:00 Aspire5253 kernel: [    1.452521] PM: Hibernation image not present or could not be loaded.
Oct 16 21:53:08 Aspire5253 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Oct 16 21:53:08 Aspire5253 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Oct 16 21:53:08 Aspire5253 kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Oct 16 21:53:08 Aspire5253 kernel: [    0.156663] PM: Registering ACPI NVS region at de649000 (2097152 bytes)
Oct 16 21:53:08 Aspire5253 kernel: [    0.156663] PM: Registering ACPI NVS region at dfdbf000 (1048576 bytes)
Oct 16 21:53:08 Aspire5253 kernel: [    1.445400] PM: Hibernation image not present or could not be loaded.
[/PHP]

---

### Post by jchiso on 2013-01-04
No hope at all?

---

### Post by Toz on 2013-01-04
> **jchiso said:**
> No hope at all?

```
pastebinit /var/log/pm-suspend.log
```
...would help.



This might also be relevant: [https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume#Dead.2C_Blank.2C_or_Black_Screen_on_Resume]("https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume#Dead.2C_Blank.2C_or_Black_Screen_on_Resume"), but it would be helpful to know which video driver you are using. The above log file would show that.

---

### Post by jchiso on 2013-01-08
It just says:

```
You are trying to send an empty document, exiting.
```

---

### Post by apnavarun on 2013-01-08
try to install os again, if not solved contact customer care of acer, they might be able to help you

---

### Post by Toz on 2013-01-08
@jchiso, I'm surprised that you are getting this message. Can you post back the contents of your /var/log directory?
```
ls -l /var/log
```

Make sure you do this after a suspend attempt.

---

### Post by jchiso on 2013-01-08
```

total 3168
-rw-r--r-- 1 root              root    776 Jan  8 20:51 alternatives.log
-rw-r--r-- 1 root              root   1025 Jan  1 20:41 alternatives.log.1
-rw-r--r-- 1 root              root    700 Nov 30 14:55 alternatives.log.2.gz
-rw-r--r-- 1 root              root    718 Oct 26 20:20 alternatives.log.3.gz
-rw-r--r-- 1 root              root   1342 Sep 26 22:55 alternatives.log.4.gz
-rw-r--r-- 1 root              root   5995 Sep  2 00:01 alternatives.log.5.gz
-rw-r----- 1 root              adm       0 Dec 11 21:12 apport.log
-rw-r----- 1 root              adm     764 Dec 11 21:08 apport.log.1
-rw-r----- 1 root              adm     175 Dec  6 14:14 apport.log.2.gz
-rw-r----- 1 root              adm     207 Dec  1 22:42 apport.log.3.gz
-rw-r----- 1 root              adm     229 Nov 30 17:58 apport.log.4.gz
-rw-r----- 1 root              adm     317 Nov  9 21:06 apport.log.5.gz
-rw-r----- 1 root              adm     209 Nov  9 14:53 apport.log.6.gz
-rw-r----- 1 root              adm     317 Nov  6 22:27 apport.log.7.gz
drwxr-xr-x 2 root              root   4096 Jan  2 23:07 apt
-rw-r----- 1 syslog            adm       0 Jan  8 20:49 auth.log
-rw-r----- 1 syslog            adm   17218 Jan  8 20:23 auth.log.1
-rw-r----- 1 syslog            adm    2409 Jan  2 22:41 auth.log.2.gz
-rw-r----- 1 syslog            adm    2526 Dec 11 21:10 auth.log.3.gz
-rw-r----- 1 syslog            adm    2845 Dec  2 15:03 auth.log.4.gz
-rw-r----- 1 root              adm      31 Apr 23  2012 boot
-rw-r--r-- 1 root              root   1503 Jan  8 20:23 boot.log
-rw-r--r-- 1 root              root  46891 Apr 23  2012 bootstrap.log
-rw-rw---- 1 root              utmp      0 Jan  2 23:07 btmp
-rw-rw---- 1 root              utmp      0 Dec  1 21:56 btmp.1
drwxr-xr-x 2 root              root   4096 Jan  2 23:07 ConsoleKit
drwxr-xr-x 2 root              root   4096 Jan  8 20:49 cups
drwxr-xr-x 2 root              root   4096 Sep 11 11:06 dist-upgrade
-rw-r----- 1 root              adm   55121 Jan  8 20:23 dmesg
-rw-r----- 1 root              adm   54707 Jan  8 13:45 dmesg.0
-rw-r----- 1 root              adm   14642 Jan  5 15:41 dmesg.1.gz
-rw-r----- 1 root              adm   14645 Jan  4 20:47 dmesg.2.gz
-rw-r----- 1 root              adm   14673 Jan  3 20:59 dmesg.3.gz
-rw-r----- 1 root              adm   14644 Jan  3 00:04 dmesg.4.gz
-rw-r--r-- 1 root              root  70111 Jan  8 20:51 dpkg.log
-rw-r--r-- 1 root              root  92904 Jan  1 20:41 dpkg.log.1
-rw-r--r-- 1 root              root  10806 Nov 30 14:55 dpkg.log.2.gz
-rw-r--r-- 1 root              root  15137 Oct 30 20:32 dpkg.log.3.gz
-rw-r--r-- 1 root              root  16060 Sep 26 22:55 dpkg.log.4.gz
-rw-r--r-- 1 root              root 128366 Sep  2 00:01 dpkg.log.5.gz
-rw-r--r-- 1 root              root      0 Jan  8 20:49 dvbhdhomerun.log
-rw-r--r-- 1 root              root    273 Jan  8 20:23 dvbhdhomerun.log.1.gz
-rw-r--r-- 1 root              root    248 Jan  5 15:41 dvbhdhomerun.log.2.gz
-rw-r--r-- 1 root              root    248 Jan  4 20:47 dvbhdhomerun.log.3.gz
-rw-r--r-- 1 root              root    279 Jan  3 20:59 dvbhdhomerun.log.4.gz
-rw-r--r-- 1 root              root   3273 Jan  2 22:41 dvbhdhomerun.log.5.gz
-rw-r--r-- 1 root              root      0 Jan  8 20:23 dvbhdhomerun_stderr.log
-rw-r--r-- 1 root              root      0 Jan  8 20:23 dvbhdhomerun_stdout.log
-rw-r--r-- 1 root              root  24024 Sep 10 23:23 faillog
-rw-r--r-- 1 root              root   2566 Aug 25 16:17 fontconfig.log
drwxr-xr-x 2 root              root   4096 Apr 23  2012 fsck
drwxr-xr-x 2 root              root   4096 Apr  4  2012 hp
drwxr-xr-x 3 root              root   4096 Aug 12 19:46 installer
-rw-r--r-- 1 root              root      0 Aug 13 20:11 jockey.log
-rw-r--r-- 1 root              root  85451 Aug 13 20:11 jockey.log.1
-rw-r----- 1 syslog            adm     407 Jan  8 20:51 kern.log
-rw-r----- 1 syslog            adm  541120 Jan  8 20:23 kern.log.1
-rw-r----- 1 syslog            adm  135161 Jan  2 22:42 kern.log.2.gz
-rw-r----- 1 syslog            adm  148305 Dec 11 21:09 kern.log.3.gz
-rw-r----- 1 syslog            adm  179659 Dec  2 15:07 kern.log.4.gz
-rw-rw-r-- 1 root              utmp 292292 Sep 12 12:02 lastlog
drwxr-xr-x 2 root              root   4096 Jan  8 20:23 lightdm
-rw-r----- 1 syslog            adm       0 Aug 12 19:49 mail.err
-rw-r----- 1 syslog            adm       0 Aug 12 19:49 mail.log
drwxr-xr-x 2 root              root   4096 Aug 12 19:49 news
-rw-r--r-- 1 root              root  26483 Jan  8 20:23 pm-powersave.log
-rw-r--r-- 1 root              root  92531 Jan  2 22:41 pm-powersave.log.1
-rw-r--r-- 1 root              root   2123 Dec  1 21:49 pm-powersave.log.2.gz
-rw-r--r-- 1 root              root   3146 Nov  1 20:35 pm-powersave.log.3.gz
-rw-r--r-- 1 root              root   3574 Oct  1 10:23 pm-powersave.log.4.gz
-rw-r--r-- 1 root              root      0 Dec 13 19:51 pm-suspend.log
-rw-r--r-- 1 root              root   8788 Dec 12 22:24 pm-suspend.log.1
-rw-r--r-- 1 root              root   3054 Oct 30 13:46 pm-suspend.log.2.gz
-rw-r--r-- 1 root              root   4148 Sep 24 20:57 pm-suspend.log.3.gz
-rw-r--r-- 1 root              root   6669 Sep  1 10:41 pm-suspend.log.4.gz
drwxr-x--- 2 root              adm    4096 Apr 12  2012 samba
drwx------ 2 speech-dispatcher root   4096 Feb  5  2012 speech-dispatcher
-rw-r----- 1 syslog            adm    1061 Jan  8 20:51 syslog
-rw-r----- 1 syslog            adm  240232 Jan  8 20:48 syslog.1
-rw-r----- 1 syslog            adm   21382 Jan  5 16:10 syslog.2.gz
-rw-r----- 1 syslog            adm   21613 Jan  4 21:17 syslog.3.gz
-rw-r----- 1 syslog            adm   44422 Jan  3 21:11 syslog.4.gz
-rw-r----- 1 syslog            adm  103081 Jan  2 23:06 syslog.5.gz
-rw-r----- 1 syslog            adm   24312 Dec 14 14:56 syslog.6.gz
-rw-r----- 1 syslog            adm   50115 Dec 13 19:46 syslog.7.gz
-rw-r--r-- 1 root              root 259237 Jan  8 20:23 udev
-rw-r----- 1 syslog            adm       0 Aug 12 19:49 ufw.log
drwxr-xr-x 2 root              root   4096 Mar 12  2012 unattended-upgrades
drwxr-xr-x 2 root              root   4096 Jan  8 20:49 upstart
-rw-rw-r-- 1 root              utmp  38016 Jan  8 20:51 wtmp
-rw-rw-r-- 1 root              utmp 120192 Jan  2 22:41 wtmp.1
-rw-r--r-- 1 root              root  38040 Jan  8 20:23 Xorg.0.log
-rw-r--r-- 1 root              root  39574 Jan  8 14:32 Xorg.0.log.old
-rw-r--r-- 1 root              root  38767 Nov  5 21:35 Xorg.1.log
-rw-r--r-- 1 root              root  42205 Sep 10 23:30 Xorg.1.log.old
-rw-r--r-- 1 root              root   9244 Dec 12 22:26 Xorg.failsafe.log
-rw-r--r-- 1 root              root   8668 Sep 12 00:00 Xorg.failsafe.log.old

```

---

### Post by Toz on 2013-01-08
Okay. Try to do a suspend. From a terminal:
```
sudo pm-suspend
```
When you recover, the /var/log/pm-suspend.log file should have some data in it. Then run:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

---

### Post by jchiso on 2013-01-09
[http://paste.ubuntu.com/1515514/](http://paste.ubuntu.com/1515514/)

---

### Post by Toz on 2013-01-09
Is there anything in your syslog that indicates a problem:
```
cat /var/log/syslog | grep PM:
```

According to the links referenced in this post: [http://ubuntuforums.org/showpost.php?p=11893497&postcount=9]("http://ubuntuforums.org/showpost.php?p=11893497&postcount=9"), removing the proprietary fglrx drivers and using the opensource radeon driver seems to solve the problem. It appears that it did for the OP.

You might also consider giving the resume-trace debugging process [here]("https://wiki.ubuntu.com/DebuggingKernelSuspend#A.22resume-trace.22_debugging_procedure_for_finding_buggy_drivers") a go. It might identify where the hang up is.

---

### Post by jchiso on 2013-01-10
I had previously tried the fglrx-removal procedures referenced in that thread.  It says I don't have the driver installed, but it still won't resume.  Looks live other folks referring to that thread were unable to use that removal procedure successfully ...

---

