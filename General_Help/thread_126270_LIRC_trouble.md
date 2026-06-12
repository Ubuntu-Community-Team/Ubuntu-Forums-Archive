---
title: "LIRC trouble"
date: 2006-02-06
forum: General Help
---

### Post by gshegosh on 2006-02-06
I've got a home brew IR receiver and am trying to install it in Ubuntu 5.10.
Gathering information from different sources from Internet, I've managed to compile lirc_serial kernel module and got to the point where mode2 reacts when I press remote control buttons.
I then used irrecord to create lircd.conf for my remote - with success, too.

But now when I run irw to test it, it just goes back to the prompt and nothing happens. I even looked into the source code of irw and it should get into an endless loop (not returning to prompt) OR print out an error message. None of that happens.

It just looks like

#irw
#

When I try to run irw next time, I get
#irw
cannot connect to device
#

So I restart lircd and am able to run irw again, but it just returns to prompt everytime :(

Can anyone help me with this one?

Regards,
gshegosh

---

### Post by _rob_ on 2006-02-08
I have _exactly_ the same problem - except that I'm using a Hauppauge card (lirc_i2c).  And as it happened, I also got things working when I first installed.  But after monkeying with config files to get it to start at boot, I broke something -I think.  Ahh!

I've recompiled lirc once (to lirc 0.8.0) to try to get things working - no good.  But I'm not 100% sure about what I'm doing.  I didn't download a new rev of the kernel though.

lsmod shows both modules loaded.  The daemon (lircd) dies when I try irw or mythfrontend.

I've attached some logs below in hopes that someone will see something.  This is driving me crazy.  Any suggestions?  ...Maybe a proper way to undo all lirc stuff and kernel and start from sratch again?!?

Lirc no work!
Help!
-Rob

ps - I've tried the other thread - with no help (last entry): [http://www.ubuntuforums.org/showthread.php?t=30612](http://www.ubuntuforums.org/showthread.php?t=30612)
-----------logs below----------

_My lirc log:_
went from...
Jan 31 08:45:07 ClosetBox lircd 0.7.3pre1: accepted new client on /dev/lircd
Jan 31 08:45:07 ClosetBox lircd 0.7.3pre1: could not get file information for /dev/lirc
Jan 31 08:45:07 ClosetBox lircd 0.7.3pre1: default_init(): No such file or directory
Jan 31 08:45:07 ClosetBox lircd 0.7.3pre1: caught signal

...to...

Feb  7 00:25:59 ClosetBox lircd: accepted new client on /dev/lircd
Feb  7 00:25:59 ClosetBox lircd: could not open /dev/lirc
Feb  7 00:25:59 ClosetBox lircd: default_init(): No such device
Feb  7 00:25:59 ClosetBox lircd: caught signal
Feb  7 00:26:35 ClosetBox lircd: lircd(hauppauge) ready


_My messages log:_
[4867687.867000] lirc_dev: IR Remote Control driver registered, at major 61
[4867687.927000] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[4867687.997000] bttv: disagrees about version of symbol tveeprom_hauppauge_analog
[4867687.997000] bttv: Unknown symbol tveeprom_hauppauge_analog
[4867688.529000] cx88xx: disagrees about version of symbol tveeprom_hauppauge_analog
[4867688.529000] cx88xx: Unknown symbol tveeprom_hauppauge_analog
[4867688.537000] cx8800: Unknown symbol cx88_reset
[4867688.537000] cx8800: Unknown symbol cx88_call_i2c_clients
[4867688.537000] cx8800: Unknown symbol cx88_wakeup
...

_interesting daemon log items:_
Feb  6 23:52:36 localhost modprobe: FATAL: Error inserting bttv 
(/lib/modules/2.6.12-10-386/kernel/drivers/media/video/bttv.ko): Unknown symbol in module, or unknown parameter (see dmesg) 

Feb  6 23:52:36 localhost modprobe: WARNING: Error inserting cx88xx 
(/lib/modules/2.6.12-10-386/kernel/drivers/media/video/cx88/cx88xx.ko): Unknown symbol in module, or unknown parameter (see dmesg) 

Feb  6 23:52:36 localhost modprobe: FATAL: Error inserting cx8800 
(/lib/modules/2.6.12-10-386/kernel/drivers/media/video/cx88/cx8800.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by oblib on 2006-02-10
I don't know if this will help, but here are the basics.
To get lirc to work the following must happen:
sudo modprobe lirc-serial
sudo /etc/init.d/lirc restart

If at this point, you have a device existing called /dev/lirc, and it's permissions are set to rw on all, then you shouldn't have a problem in my experience. Ubuntu defaults to calling it /dev/lirc0 for some reaons, and to fix that create a file called /etc/udev/rules.d/lirc.rules and add the following to it:
KERNEL="lirc[0-9]*",    NAME="lirc", MODE="0666"

Reboot and it should be okay. If the permissions are not set, fix it with
sudo chmod 666 /dev/lirc

If you type dmesg | grep lirc and see errors with accessing the serial port, you need this:
setserial /dev/ttyS0 uart none
modprobe lirc-serial
somewhere in your /etc/init.d/bootmisc.sh file before the exit. You will need to install the package setserial of course.

That's all I can think of off the top of my head. Use 'mode2' rather than 'irw' to check it initiall, as that shows the raw codes.

---

### Post by _rob_ on 2006-02-10
Thanks, oblib.  Quick question: Are IR connections thru Hauppage cards effected by serial port access?  I was thinking that it doesn't access the serial port because it's not plugged into the serial connector.???

I'll check the permissions, but I'm pretty sure my device is "/dev/lirc".  So I'm guessing I don't need that extra line in the rules file.

Thanks,
Rob

---

### Post by oblib on 2006-02-14
I'm not using Hauppauge IR, so I don't know. You should be right though, and it should not be involved with the serial port at all. That was more for gshegosh, who is using a homebrew IR like me. Looking more closely at your logs, I would have to say it looks like you have something weird going on, but I don't know what. The only line that means anything to me is "could not get file information for /dev/lirc" which could mean it's having problems finding the device. Let us know if you figure out what's wrong.

---

### Post by _rob_ on 2006-03-03
Well, I finally got enough time to give it another try.  And I got things working again.  

Here’s what I did:
1. Made sure no lirc modules and processes running (lsmod and process viewer?).
2. Followed step 5.1 of [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html) to get a good build environment.  [Which may have been my trouble in the past.]
3. Followed step 7 in same document (skipped the other sections not needed for lirc).

I think that #2 was the key for me.

Now I’m back to where I was before.  It’s now time to configure lirc to send commands to my STB (not currently in the loop).  I’ve been told there are 2 ways that you can do this: (1) copy the lirc program to another folder, rename it, and reconfigure it, or (2) some other way where you don’t have to make a copy of itself.  Anyone have any recommends either way?

Thanks for the support.  Hope this helps someone.

-Rob

---

### Post by _rob_ on 2006-03-03
Forgot to meantion:

One thing I noticed that is different now is that there is a process called lirc that is running even before starting the daemon (lircd).  That process wasn't there before (when things didn't work).  I'm still a newbie to linux, but I think it might be for the device itself. [?]

-Rob

---

### Post by _rob_ on 2006-03-06
Sorry, that should have been "...a process called lirc_dev...".

Also, something I did not know:
"NOTE(S): Compiling LIRC should be done after you have built your kernel. Also, everytime you recompile your kernel to a new version, old lirc modules will not work anymore. Make sure you recompile and install it again."

from - [http://www.restricted.dyndns.org/twoinstancelirc.html](http://www.restricted.dyndns.org/twoinstancelirc.html)

---

