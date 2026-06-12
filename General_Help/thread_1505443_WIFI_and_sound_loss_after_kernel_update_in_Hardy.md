---
title: "WIFI and sound loss after kernel update in Hardy"
date: 2010-06-09
forum: General Help
---

### Post by mariannep on 2010-06-09
Hello!

I have a Hardy which last night asked for updates that included kernel changes. Today I find I no longer can connect using WIFI and have no sound. :( The GUIs are just not there and it's as if the controllers themselves have disappeared. For example lshw -C network reveals a Cisco Airon Wireless, but it's not listed as a wireless device, just as network controller.

Can anyone advice me on how to approach this? Is it possible to revert changes or something?

Thanks! 


Marianne

---

### Post by mariannep on 2010-06-11
So no one has any idea? 

It's an old laptop, hence having Hardy. Until I can get something newer and better, I think I'm stuck... :(

---

### Post by RHTopics on 2010-06-11
Hi Marianne,

I going to make a few of assumptions.  And they are that you are using the generic desktop kernel, which with the latest upgrade should be 2.6.24-28, your grub menu is hidden, and that you have not recently removed any of the older linux kernel packages.

When booting up the computer, press the "Esc" key to reveal the "Grub" menu, select one of the previous kernel images (2.6.24.27 or 2.6.24.6).  This should allow you to boot into an environment where your WIFI and sound should work.

It appears the latest kernel image is not directly including your wireless device and sound card drivers.  You may be able to load the modules your self if that is the case.

You might compare the messages that appear when doing a "dmesg" command to see the differences between the latest kernel and the previous one.  That is see what may be missing for your WIFI and sound card.

---

### Post by mariannep on 2010-06-13
Thanks a lot!!

I do have the generic kernel you mention, but I didn't know what to check for. Ever the newbie... <redface>

I do have to go back all the way to 2.6.17 for sound and WIFI to work properly, though.

> **RHTopics said:**
> You might compare the messages that appear when doing a "dmesg" command to see the differences between the latest kernel and the previous one.  That is see what may be missing for your WIFI and sound card.

What should I be looking for? I see no mentions there of anything with snd sound or audio. Plenty of diffs but nothing that stands out to my untrained eye.

I have been reading on similar problems, but nothing actually got that specific :/

Comparing lsmod | grep sound in both cases all I get is different numbers in general, but the list seems otherwise the same.

From lspci, in the current kernel, I get:

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: IBM ThinkPad T41
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at c0000c00 (32-bit, non-prefetchable) [size=512]
        Memory at c0000800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

Thanks so much!!



Marianne

---

### Post by RHTopics on 2010-06-13
I am glad you were able to use one of your previous kernels to get the computer back to full functionality.  Although I am puzzled you could not use the one right before the latest one.

In the display from the dmesg command, it may only give you information about your wifi card and not show you anything about your sound card.  For the wifi card look for words like wlan0 or eth0 or eth1, and see if you can tie one of them back to your wifi card.

From the results of the lsmod, it appears the sound card driver modules are being loaded but not working properly.  You might try doing the command "alsamixer" from a terminal window and see what shows up.  Maybe the sound card got muted some how.  The alsamixer screen will show you your sound card and sound chip.  Might try a Google search on them to see if other people are having your problem.

Other places to look for error messages are the system logs which are available from the System -> Administration -> System log menu.  

You might also search in Launchpad to see if a bug report has already been filed for your problem and if there is a work-around fix for it.

If your sound card and wifi also stop working on the previous kernel as well, you might want to consider replacing the cmos battery in the computer.  I have a 12 year old Compaq desktop computer that started acting flakey.  Replacing the cmos battery brought it back to its old self.

---

### Post by mariannep on 2010-06-19
Thank you once again! :)

I've been too busy to look into this until today. 

Alsamixer as before doesn't lead anywhere at all. It just says:

alsamixer: function snd_ctl_open failed for default: No such file or directory

I can't see much in the way of errors in the System -> Administration -> System log menu.

But  /var/log/syslog shows the following:

```
Jun 19 13:09:16 ibm-foton audio[5753]: Bluetooth Audio daemon
Jun 19 13:09:16 ibm-foton audio[5753]: Unix socket created: 5
Jun 19 13:09:16 ibm-foton audio[5753]: audio.conf: Key file does not have key 'Enable'
Jun 19 13:09:16 ibm-foton audio[5753]: audio.conf: Key file does not have key 'Disable'
Jun 19 13:09:16 ibm-foton kernel: [  638.948770] Bluetooth: RFCOMM socket layer initialized
Jun 19 13:09:16 ibm-foton kernel: [  638.949182] Bluetooth: RFCOMM TTY layer initialized
Jun 19 13:09:16 ibm-foton kernel: [  638.949191] Bluetooth: RFCOMM ver 1.8
Jun 19 13:09:16 ibm-foton audio[5753]: add_service_record: got record id 0x10000
Jun 19 13:09:16 ibm-foton audio[5753]: audio.conf: Key file does not have key 'Disable'
Jun 19 13:09:16 ibm-foton audio[5753]: audio.conf: Key file does not have group 'A2DP'
Jun 19 13:09:16 ibm-foton last message repeated 3 times
Jun 19 13:09:16 ibm-foton audio[5753]: SEP 0x806d0f8 registered: type:0 codec:0 seid:1
Jun 19 13:09:16 ibm-foton audio[5753]: add_service_record: got record id 0x10001
Jun 19 13:09:16 ibm-foton audio[5753]: add_service_record: got record id 0x10002
Jun 19 13:09:16 ibm-foton audio[5753]: add_service_record: got record id 0x10003
Jun 19 13:09:16 ibm-foton audio[5753]: Registered manager path:/org/bluez/audio
```

One strange thing that happened is that one day this week it had sound again, though no wifi. So I wonder if the CMOS battery may be involved as you say... :/

I tried searching bug reports on Launchpad but with no luck so far.


Thank you!


Marianne

---

