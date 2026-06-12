---
title: "lirc SMK eHome Infrared Receiver Karmic"
date: 2009-11-09
forum: General Help
---

### Post by grafted_scion on 2009-11-09
I'm trying to setup a remote with receiver i got from a old Scaleo H.
Browsing the forum for help has brought me closer to my goal.
Just not close enough :(

```
$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0609:031d SMK Manufacturing, Inc. eHome Infrared Receiver
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c50b Logitech, Inc. Cordless Desktop Optical
Bus 006 Device 003: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
``````
$ dmesg | grep -i lirc
[   10.979048] lirc_dev: IR Remote Control driver registered, major 61 
[   13.256084] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   13.256090] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   13.519406] lirc_dev: lirc_register_driver: sample_rate: 0
[   13.524401] lirc_mceusb[2]: SMK eHome Infrared Transceiver on usb7:2
[   13.524458] usbcore: registered new interface driver lirc_mceusb
``````
$ lsmod | grep lirc
lirc_mceusb            15520  0 
lirc_dev               10804  1 lirc_mceusb
```irw gives no readings.

A picture of the hardware:
[IMG]http://img109.imageshack.us/img109/5369/smk.jpg[/IMG]

If anyone knows the hardware or know what is wrong please tell.

Thanks

---

### Post by kylemallory on 2009-12-20
I've had this hardware working in the past with previous versions of Ubuntu.  But reinstalling it after some time (a year?) on 9.10, I'm not seeing an option for it in the lirc setup.  If I find something more, I'll post it.  But I do know for a fact that both this receiver and remote have worked for me in the past with Ubuntu and Rhythmbox.

---

### Post by joebrady on 2010-02-03
I have a similar remote, same button layout and same receiver (SMK).  It's Toshiba branded and came with my Qosmio laptop.  I've been fighting LIRC for three days trying to get any kind of resoponse from this thing.  I'd love to use this with my new XBMC machine, but at the moment, I'm closer to breaking it in half.
 
Anyone have LIRC files for this remote?

---

### Post by bmullan on 2010-08-09
> **grafted_scion said:**
> I'm trying to setup a remote with receiver i got from a old Scaleo H.
Browsing the forum for help has brought me closer to my goal.
Just not close enough :(

```
$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0609:031d SMK Manufacturing, Inc. eHome Infrared Receiver
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c50b Logitech, Inc. Cordless Desktop Optical
Bus 006 Device 003: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
``````
$ dmesg | grep -i lirc
[   10.979048] lirc_dev: IR Remote Control driver registered, major 61 
[   13.256084] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   13.256090] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   13.519406] lirc_dev: lirc_register_driver: sample_rate: 0
[   13.524401] lirc_mceusb[2]: SMK eHome Infrared Transceiver on usb7:2
[   13.524458] usbcore: registered new interface driver lirc_mceusb
``````
$ lsmod | grep lirc
lirc_mceusb            15520  0 
lirc_dev               10804  1 lirc_mceusb
```irw gives no readings.

A picture of the hardware:
[IMG]http://img109.imageshack.us/img109/5369/smk.jpg[/IMG]

If anyone knows the hardware or know what is wrong please tell.

Thanks

I have the same IR remote/receiver and got the same responses from DMESG etc that you did (although on Lucid 10.04 desktop).

After doing some searching **I did find a solution that worked (and it was simple to fix) !!**

[http://eubolist.wordpress.com/2010/02/01/set-up-lirc-to-control-your-ubuntumythtv-box-with-a-microsoft-media-center-edition-mce-infrared-remote-control/](http://eubolist.wordpress.com/2010/02/01/set-up-lirc-to-control-your-ubuntumythtv-box-with-a-microsoft-media-center-edition-mce-infrared-remote-control/)

---

### Post by bmullan on 2010-08-09
I have the same IR remote/receiver and got the same responses from DMESG etc that you did (although on Lucid 10.04 desktop).

After doing some searching I did find a solution that worked (and it was simple to fix) !!

[http://eubolist.wordpress.com/2010/0...emote-control/](http://eubolist.wordpress.com/2010/0...emote-control/)

---

### Post by SL666 on 2011-05-06
Hi All, 

When i was trying to fix my lirc mce issue, this is the thread that kept popping up, so i figure it might be a good place to start trying to figure out why my machine is now fixed.

As i have no idea why - what i did fixed the issue, i can only assume that it will break again at any time.

It started after i ran a usual update - it updated the kernel from 2.6.32-28 to 2.6.32-31.

System is a 10.04 x64 mythbuntu build

symptoms were a dissapearing /dev/lirc0 (at one point) and no output from irw at all.



I have this Remote - 
[img]http://www.mythtv.org/w/images/thumb/b/b2/MCE-Remote-2-v1069.jpg/100px-MCE-Remote-2-v1069.jpg[/img]

shows up as - 
```
steve@mythbox:/dev$ lsusb
Bus 013 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 012 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0609:0322 SMK Manufacturing, Inc. eHome Infrared Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 2040:9950 Hauppauge
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 2040:9950 Hauppauge
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


```
dmesg | grep -i lirc
[    9.766767] lirc_dev: IR Remote Control driver registered, major 61
[   10.560074] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   10.560077] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   11.060712] lirc_dev: lirc_register_driver: sample_rate: 0
[   11.069391] lirc_mceusb[2]: SMK eHome Infrared Transceiver on usb5:2
[   11.069449] usbcore: registered new interface driver lirc_mceusb
[  144.486780] usbcore: deregistering interface driver lirc_mceusb
[  144.487483] lirc_mceusb[2]: usb remote disconnected
[  166.146620] lirc_dev: IR Remote Control driver registered, major 61
[  166.154039] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[  166.154046] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[  166.499829] lirc_dev: lirc_register_driver: sample_rate: 0
[  166.508822] lirc_mceusb[2]: SMK eHome Infrared Transceiver on usb5:2
[  166.508941] usbcore: registered new interface driver lirc_mceusb
```


```
lsmod | grep lirc
lirc_mceusb            14054  1
lirc_dev               11302  3 lirc_mceusb

```

and pulling all the logs when i plug the reciever in - 

```
May  7 10:31:47 mythbox kernel: [  130.268779] usb 8-2: new full speed USB device using ohci_hcd and address 2

==> syslog <==
May  7 10:31:47 mythbox kernel: [  130.268779] usb 8-2: new full speed USB device using ohci_hcd and address 2

==> daemon.log <==
May  7 10:31:48 mythbox lircd-0.8.6[1292]: caught signal
May  7 10:31:48 mythbox lircd-0.8.6[2141]: lircd(default) ready, using /var/run/lirc/lircd

==> kern.log <==
May  7 10:31:48 mythbox kernel: [  130.512282] usb 8-2: configuration #1 chosen from 2 choices
May  7 10:31:48 mythbox kernel: [  130.690048] usb 8-2: reset full speed USB device using ohci_hcd and address 2
May  7 10:31:48 mythbox kernel: [  130.889854] lirc_dev: lirc_register_driver: sample_rate: 0
May  7 10:31:48 mythbox kernel: [  130.898877] lirc_mceusb[2]: SMK eHome Infrared Transceiver on usb8:2

==> syslog <==
May  7 10:31:48 mythbox kernel: [  130.512282] usb 8-2: configuration #1 chosen from 2 choices
May  7 10:31:48 mythbox kernel: [  130.690048] usb 8-2: reset full speed USB device using ohci_hcd and address 2
May  7 10:31:48 mythbox kernel: [  130.889854] lirc_dev: lirc_register_driver: sample_rate: 0
May  7 10:31:48 mythbox kernel: [  130.898877] lirc_mceusb[2]: SMK eHome Infrared Transceiver on usb8:2
May  7 10:31:48 mythbox lircd-0.8.6[1292]: caught signal
May  7 10:31:48 mythbox lircd-0.8.6[2141]: lircd(default) ready, using /var/run/lirc/lircd

==> daemon.log <==
May  7 10:31:50 mythbox lircd-0.8.6[2141]: accepted new client on /var/run/lirc/lircd

==> syslog <==
May  7 10:31:50 mythbox lircd-0.8.6[2141]: accepted new client on /var/run/lirc/lircd



```


The "configuration #1 chosen from 2 choices" line caught my attention - i read here [http://www.mythtv.org/wiki/MCE_Remote](http://www.mythtv.org/wiki/MCE_Remote) that my remote should use lirc_mceusb2 not lirc_mceusb, so after some experimenting i unloaded lirc_mceusb and blacklisted it.

```
sudo modprobe -r lirc_mceusb
```

```
steve@mythbox:/etc/modprobe.d$ cat blacklist-custom.conf
# /etc/modprobe.d/blacklist-custom.conf
# Custom blacklist file so I don't mess with any of the files that come with
# the module-init-tools package.
blacklist lirc_mceusb

```

Then i tried to load lirc_mceusb2 - which doesn't exist.. so i loaded lirc_mceusb and then fired up irw - and had output.. so was shocked.. .

So i rebooted (expecting to have to load lirc_mceusb manually)
 - but straight after the reboot it worked fine - i have no idea why.

I'm reasonably comfortable with linux but this whole kernel module thing is way beyond my grasp at this point (but i would like to know more)

---

