---
title: "Cursor freezes in 10.10"
date: 2010-10-12
forum: General Help
---

### Post by cov on 2010-10-12
Hi, I'm suddenly getting mouse cursor freezes since I upgraded from Lucid.

It's not serious, just irritating; I can get cursor movement back by alt-tabbing.

Anyone having similar issues?

I'm running 32bit on an Asus Laptop, model K501J and am using the XFce window manager. My /var/log/messages reports the following:

> Oct 12 09:46:23 SNECCII kernel: [10122.860511] psmouse.c: Touchpad at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
Oct 12 09:46:27 SNECCII kernel: [10126.679195] psmouse.c: resync failed, issuing reconnect request


---

### Post by Milesio on 2010-10-12
Same story here. I had been having this problem since I upgraded to 10.04 I think, and it's still present in 10.10. I was hoping the new upgrade would fix it but... meh.
It only happens when I use a USB mouse and it's completely random. I've done all sorts of tests, combinations... to no avail. It comes and goes and I cannot make heads or tails of it.
I ended up using just the touchpad and that's it. I sort of gave up on the USB mouses. 
Obviously, I won't stop using Ubuntu just 'cos of this but yeah, it's damn annoying although it also is the only thing that's not working for me. 

I'm using a Dell 1530 XPS (4 gigs ram, dual 2.4 processor if memory serves me correctly, NVidia GeForce 8600 (512 mb) card, 500 Gb hdd), with Ubuntu 10.10 now.

---

### Post by mr.interested on 2010-10-13
I have the very same problem. It's happening since yesterday when I upgraded to Ubuntu 10.10. (In Ubuntu 10.04 everything was OK.) The log is also the same as OP:

> Oct 13 09:51:06 michael-laptop kernel: [ 3598.220761] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
Oct 13 09:51:07 michael-laptop kernel: [ 3599.504991] psmouse.c: resync failed, issuing reconnect request

---

### Post by Refalm on 2010-10-13
I have the same problem in Maverick. Everything worked great though in Lucid.

There's also a weird problem with Linux-native games like Quake Live and UrbanTerror, where the cursor does not move, but the mouse buttons work fine.
Gaming in Wine does work ironically.

---

### Post by mr.interested on 2010-10-13
> **Refalm said:**
> the cursor does not move, but the mouse buttons work fine.

On my Ubuntu 10.10 both cursor and mouse buttons don't work. They start working after several seconds, or after I press and hold Esc button for a second. The cursor freezes randomly, but on average once a minute.

I'm a bit disappointed with the new version, as this is the second problem I have with it (the other is about Media Player: [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9959415](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9959415)).

---

### Post by cov on 2010-10-14
Just to update the original post, I stated that Alt-Tabbing unfreezes the mouse cursor, however, just pressing the Alt key is sufficient.

Looks like a bug, no?

How do I report it?

---

### Post by alex.white on 2010-10-14
I have the similar problem with mouse cursor freezings... Everything was OK on my old workstation. But after i bought a new one and install 10.04 at first and then 10.10 (both 64bit) cursor begins to freeze randomly for a second or few and then returns back to normal work. It happens with USB wireless mouses (i've tried two different mouses). Frequently it happens during active disk IO operations or when i use Firefox.

PS: AMD Phenom II 965, MSI 890GXM-G65 (with on-board ATI Radeon HD 4290), SATA HDD, fglrx driver.

---

### Post by Martyn Collins, Esq. on 2010-10-14
My mouse in thinkpad T42 has been persistently freezing after upgrade to Maverick.  Just sayin.

---

### Post by encho on 2010-10-15
It happens here as well, Dell Latitude D630, Maverick 64bit.

---

### Post by maen on 2010-10-15
My cursor freezes, and downloads stall. Pressing Alt gets it going again. Would love a solution :)

Acer Aspire 5735Z on Maverick, dist. upgraded from lucid and others

---

### Post by parun on 2010-10-16
Ok I had the same problem after upgrade, from 10.04 to 10.10 , 
and here is my solution:

get new kernel image from : [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34.7-maverick/linux-image-2.6.34-02063407-generic_2.6.34-02063407.201009140905_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34.7-maverick/linux-image-2.6.34-02063407-generic_2.6.34-02063407.201009140905_amd64.deb)

and install and reboot with new kernel, if everething is ok, than you may uninstall generic kernel 2.6.35

For me everything working ok now.

P.S 

Sorry for my english :(

---

### Post by godor on 2010-10-18
Hi,

I got the same Problem on an Thinkpad Edge 11 with Intel Processor.
I did a new Install of the 10.10.
The Kernel Downgrade to linux-image-2.6.34-02063407-generic_2.6.34-02063407.201009140905_amd64 did not help, there was still the same Problem.
Sometimes the cursor freezes are realy anoying, sometimes there not here for a long time.
I got this computer new, and didn't test it with Windows. Can it be a Hardware Problem?
I attached the fail part in var/log/messages.
Greetings,
Guido

---

### Post by Ibertech on 2010-10-18
I have also been experiencing similar problems, i have maverick installed on my Acer Aspire 5940G and i get mouse freezing and also freezing when transfering files via USB to my external disk or ipod.

---

### Post by AXe Naqvi on 2010-10-19
I have been running into this annoying issue since the day i upgraded from 10.04 to 10.10. Is there any solution to this? Right now I've to click any key from keyboard and the mouse pointer is moving again...

---

### Post by shawnyar217 on 2010-10-19
I see a simliar problem in 10.04. I was hoping 10.10 would fix it but apparently not.

If I open a terminal window and hold down the enter key, sometimes it keeps printing new prompts repeatedly as you would expect. Other times, it stops and does nothing as if the key repeat logic was interrupted somehow.

Other times, the entire desktop freezes up for several seconds without a good reason (i.e. CPU usage is low).

Web browser cursors sometimes stop flashing. If I touch the CTRL key or move the mouse, the flashing resumes. While I was writing this, I stopped typing, waited several seconds and the flashing cursor froze. At the same time, an animated smiley image on the side froze also. Pressing CTRL brought them both right back.

It's like the kernel isn't waking up processes from a sleep state when it should.

Anyone know if this problem has been called to the attention of Ubuntu?

---

### Post by mustail on 2010-10-19
My mouse pointer started to freeze out of nothing, after a clean install of Ubuntu 10.10 on a Thinkpad T400. I did not notice this problem before with 10.04.
I'm using trackpoint and touchpad, not a USB mouse.

By the way, there is a bug report for that:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/658538](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/658538)

---

### Post by Nicke on 2010-10-20
> **godor said:**
> Hi,

I got the same Problem on an Thinkpad Edge 11 with Intel Processor.
I did a new Install of the 10.10.
The Kernel Downgrade to linux-image-2.6.34-02063407-generic_2.6.34-02063407.201009140905_amd64 did not help, there was still the same Problem.
Sometimes the cursor freezes are realy anoying, sometimes there not here for a long time.
I got this computer new, and didn't test it with Windows. Can it be a Hardware Problem?
I attached the fail part in var/log/messages.
Greetings,
Guido

I have an Edge 11 and the exact same problem, don't think its a hardware failure. The trackpoint works fine in W7.
/Nicke

---

### Post by cov on 2010-10-22
This has really started to get irritating.

Previously it was freezing once every ten minutes or so, but now it is freezing several times a minute.

Pressing any key frees it, but all computer activity appears to halt (including downloading) when the freeze occurs.

---

### Post by cov on 2010-10-25
Nobody got a fix for this?

It doesn't just stop the mouse, it freezes the whole system. If it happens while booting up, it will freeze mid boot up. Any downloads are frozen also. Sometimes I have to repeatedly press the Control button to make sure I can download something.

So it's developed from a minor irritation into a major annoyance.

---

### Post by eyalv on 2010-10-25
Same here since upgrade to 10.10.
Cursor stuck when using the touchpad, clicking on a keyboard key sometimes releases it.
Lenovo laptop G500.

---

### Post by hatkirby on 2010-10-30
I'm having a similar problem with my Acer Extensa (don't know version number, sorry, lost the sticker). The mouse will suddenly stop moving for a while, and sometimes when it comes back, it moves erratically, even avoiding certain areas on the screen. After reading some other posts, I tried dmesg and found tons of errors like this:```
[68610.856840] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 5 bytes away.
[68611.425797] psmouse.c: resync failed, issuing reconnect request
[68680.576670] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[68681.859415] psmouse.c: resync failed, issuing reconnect request
```I have not yet tried pressing any keys during the problem, but I will definitely try the next time it happens. Also, a real solution would be lovely.

...oh, okay, it just happened again and I tried hitting Alt. The mouse started moving again, but very erratically.

---

### Post by Method X on 2010-11-01
IBM Lenovo Thinkpad R500.
Same problem with Maverick.
Looking for solution.

---

### Post by victoitor on 2010-11-04
I have the same problem on my mom's new HP laptop touchpad (lost the sticker so I don't know which model it is exactly). Help guys, I finally got her to Ubuntu and this might be ruining her experience.

Same message from dmesg as you guys get.

---

### Post by azertyh on 2010-11-05
hello,
 
i had a similar problem, the message in syslog is just a little different. see [http://ubuntuforums.org/showthread.php?t=1606041]](http://ubuntuforums.org/showthread.php?t=1606041])
 
the
```
sudo modprobe -r psmouse
sudo modprobe psmouse
```
works after doing that 3 or 4 times, but it's not permanently.

---

### Post by Refalm on 2010-11-06
I'm not sure it will help your problem, but this one solved problems with mouse movement sometimes not working.

I added this to /etc/X11/xorg.conf
```
Section "Module"
   SubSection   "extmod"
      Option    "omit xfree86-dga"
   EndSubSection
EndSection
```Be sure to combine, if there's already a section called "Module".

---

### Post by cov on 2010-11-16
> **Refalm said:**
> I'm not sure it will help your problem, but this one solved problems with mouse movement sometimes not working.

I added this to /etc/X11/xorg.conf
```
Section "Module"
   SubSection   "extmod"
      Option    "omit xfree86-dga"
   EndSubSection
EndSection
```Be sure to combine, if there's already a section called "Module".

Hmmm.

There is no **/etc/X11/xorg.conf**.

```
dave@SNECCII:~$ ls -l /etc/X11/
total 64
drwxr-xr-x 2 root root  4096 2010-10-11 08:53 app-defaults
drwxr-xr-x 2 root root    32 2010-04-29 14:27 cursors
-rw-r--r-- 1 root root    14 2010-04-29 14:28 default-display-manager
drwxr-xr-x 6 root root    32 2010-04-29 14:25 fonts
-rw-r--r-- 1 root root 17394 2009-12-03 12:56 rgb.txt
lrwxrwxrwx 1 root root    13 2010-05-15 15:14 X -> /usr/bin/Xorg
drwxr-xr-x 3 root root    40 2010-10-11 08:52 xinit
drwxr-xr-x 2 root root     1 2010-04-15 14:12 xkb
-rw-r--r-- 1 root root   270 2010-07-03 09:57 xorg.conf.failsafe
-rwxr-xr-x 1 root root   709 2010-04-01 13:19 Xreset
drwxr-xr-x 2 root root    16 2010-10-11 08:19 Xreset.d
drwxr-xr-x 2 root root    16 2010-10-11 08:19 Xresources
-rwxr-xr-x 1 root root  3730 2010-04-01 13:07 Xsession
drwxr-xr-x 2 root root  4096 2010-10-20 08:02 Xsession.d
-rw-r--r-- 1 root root   265 2008-07-01 19:41 Xsession.options
-rw------- 1 root root   601 2010-04-29 14:20 Xwrapper.config

```

---

### Post by cov on 2010-11-20
This is now more than a minor irritation.

The Laptop freezes on boot up unless a key is constantly pressed while it boots up.

Similarly it won't close down unless I constantly click a key.

(Or lose patience with the effing thing and hold down the power button.)

---

### Post by azertyh on 2010-11-20
hello,
i solved my problem. perhaps it will work for you too. [http://ubuntuforums.org/showthread.php?t=1606041]](http://ubuntuforums.org/showthread.php?t=1606041])

---

### Post by AXe Naqvi on 2010-11-22
Thanks azertyh... that solution also worked for me.. 2 days now without any pointer hanging issue.. it was becoming a major pain in the ..... :D .. am glad its over now..

---

### Post by bayr00t on 2010-11-23
The way to resolve this on my friend's Amilo a2030 laptop was to add "nohz=off" to the grub... Now the laptop doesn't freeze at all...

::short howto::

1. add "nohz=off" to the grub settings:

```
sudo gedit /etc/default/grub
```

change
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nohz=off"

2. update grub with the new settings:

```
sudo update-grub
```

3. restart your computer

```
sudo reboot
```

important note: this settings (nohz=off) suck your battery quite fast!

---

### Post by Nailor on 2010-11-30
nohz=off is not an option due to the increased battery consumption. Also tried the nolapic, but no win there either.

In addition to these I've tried 2.6.37 rc 2 kernel, and it didn't help either.

Any other tips?

---

### Post by godor on 2010-12-08
Hi,
It looks like, the problen persists since a long time, i found in some old posts (with old kernels) the same problem.
One interesting workaround is:

rmmod psmouse
modprobe psmouse proto=imps

This reloads the psmouse modul with an normal mouse protokol. It helps getting my freezes away, but it also disables the advanced synaptic actions like sidescrolling. So I dont use it. This workaround has not the powerconsumption problem like if you dont use a tickless kernel. (nohz option)

A little improofment was to use a meanline Kernel (v2.6.35.9-maverick) of ubuntu the mouse comes up faster after the lost sync.

So I still hope we will get a solution...
Greetings
Godor

---

### Post by mr-pink on 2011-01-27
I'm not so confident we'll get a fix for this issue... :(

Anyway, this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/658538](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/658538) is a link to the bug on launchpad... maybe subscribing the bug could help increasing the chances that it wll be fixed.

---

### Post by docmojo on 2011-05-09
Hi guys, I am a novice in these technical issues...

But faced this mouse freeze prob for a few days... Just struck me that, I had installed ClamAV prior to this glitch... So removed it from the system, and the problem seems to have disappeared... 

Do you'll have it installed too?

---

