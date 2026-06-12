---
title: "ir-keytable or: How I Learned to Stop Worrying about the LIRC Kernel"
date: 2011-05-10
forum: General Help
---

### Post by darkscout on 2011-05-10
Cross posted from the [XBMC Forums]("http://forum.xbmc.org/showthread.php?t=101151"). I know there's a whole lot of WTF surrounding the new IR setup and not a whole lot of documentation.

This is what got it working for me.
----------------
*This is for kernel's 2.6.35+ and LIRC 0.9.0 and above.*

Foreword: I've put off upgrading from Lucid because of the cluster that was LIRC in Kernel (and have not been shy about it). After Natty... I'm not happy about Natty, I'm going back to what every thing else in my house runs. A good proper Debian system. I've finally bit the bullet and started to figure out how to deal with LIRC in the Kernel, because it's not going away. Turns out, its just a little bit of awesome (and a whole lot of work.)

First you're going to need ir-keytable. It's available in natty (not maverick) and Sid & Testing.
apt-get install ir-keytable. ir-keytable turns ... I'm not really sure what ir-keytable really does. But it turns remote presses into LIRC stuff.

This is the flow chart of fun. I'll try and work on this in order.
lirc kernel -> ir-keytable mapping -> LIRC devinput -> lircmap.xml -> remote.xml.

Do not install LIRC yet. Un-install it if you have it. Right now we're going to be futzing without it.

Running ir-keytable by itself will dump out what IR receiver it recognizes in addition to what protocols it supports. I have a real HP receiver & Remote (ID 045e:006d Microsoft Corp. eHome Remote Control Keyboard keys)
```
ir-keytable 
Found /sys/class/rc/rc0/ (/dev/input/event0) with:
	Driver mceusb, table rc-rc6-mce
	Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC 
	Enabled protocols: NEC RC-5 RC-6 JVC SONY LIRC 
	Repeat delay = 500 ms, repeat period = 33 ms
```
	
[RC5/6](http://www.sbprojects.com/knowledge/ir/rc6.htm) are the IR protocols defined by Philips.
[NEC](http://www.sbprojects.com/knowledge/ir/nec.htm) aka "Japanese Format" are by NEC. This is the bread and butter protocol as most remotes use this. (At least in my house hold my Yamaha receiver and Samsung TV both use it.)
[Sony](http://www.sbprojects.com/knowledge/ir/sirc.htm). Sony ALWAYS does their own thing... I don't have anything in my house that uses this.
[JVC](http://www.sbprojects.com/knowledge/ir/jvc.htm). JVC has their own too.
--
First, You're going to be making a hex -> LIRC button name file for each of your remotes. I have 3. MCE Remote, Yamaha Receiver Remote & TV Remote.

The MCE Remote should already be mostly mapped, but if you try to standardize something as non-standard as remotes, you're bound to get a few wrong. Inside of /lib/udev/rc_keymaps/, there should be an rc6_mce. Copy that to /etc/rc_keymaps/, we're going to be editing that instead of creating a brand new file.
```
cp /lib/udev/rc_keymaps/rc6_mce /etc/rc_keymaps/
```

1) Open up my dump of valid LIRC keys: [http://xbmc.exstatic.org/ir_keys.txt](http://xbmc.exstatic.org/ir_keys.txt). You can use your own, but these are "standard". These are the names we'll be working 
2) I'm opening text files on my laptop for each remote then scping them over. You can edit directly in nano. You can export the /etc/rc_keymaps/. You can use [butterflies if you like](http://xkcd.com/378/)
3) Run "ir-keytable -c" to clear out the old table. Fire up "ir-keytable -t". If you'd like to think of this as the new "irw", you can. (If you're running LIRC, you didn't follow the directions and you have to at least stop it before running ir-keytable.)

"ir-keytable -t/--test" shows you what is being pressed. This is where the slight bit of awesome comes in. irrecord would NOT record some buttons for me, TV up down. This literally shows me something every time I press the remote. Even weird keys like +10. All of my TV commands, etc.

4) First we're going to go through our rc6 remote and 'correct' any keys that are funky. For example the "Start" key on my remote is KEY_PROG1, I want to change it to KEY_HOME.
```
nano /etc/rc_keymaps/rc6_mce
```

5) Repeat this for every remote you want to program. For my Yamaha remote "XBMC" is going to be the DVD button. When I press it on remote the receiver swaps to the correct HDMI and SPDIF in. So when I press the DVD button, it'll now control my XBMC.

Down, Up, Left, Right, Select, Keys 1-0.
```
ir-keytable -t
Testing events. Please, press CTRL-C to abort.
1304995824.617619: event MSC: scancode = 7cb3
1304995825.030592: event MSC: scancode = 7cb4
1304995825.380603: event MSC: scancode = 7cb5
...
```

I'm personally doing this in TextMate and then just copying it to ssh. The scan codes are in hex. So right now it looks like this:
```
0x7cb3 KEY_DOWN
0x7cb4 KEY_UP
0x7cb5 KEY_LEFT
0x7cb6 KEY_RIGHT
0x7cb8 KEY_OK

0x7c93 KEY_NUMERIC_0
0x7c94 KEY_NUMERIC_1
...
```

The first line of the file, best I can figure, MUST look like this:
```
==> rc6_mce <==
# table rc6_mce, type: RC6

==> samsung_stb <==
# table samsung, type: NEC

==> yamaha_dvd <==
# table yamaha, type: NEC
```

Again, it's not really documented. But if it didn't look like this, it threw a fit.

6) Edit /etc/rc_maps.cfg ... To what. I really don't know right now. I have no @#)(* clue how it works or what it does.

Right now I'm loading each of the files individually. 
```
/usr/bin/ir-keytable -c
/usr/bin/ir-keytable -p NEC,RC6 -w /etc/rc_keymaps/rc6_mce
/usr/bin/ir-keytable -p NEC,RC6 -w /etc/rc_keymaps/yamaha_dvd
/usr/bin/ir-keytable -p NEC,RC6 -w /etc/rc_keymaps/samsung_stb
```

Now when you run 'ir-keytable -t' you should see each of the buttons mapped.
You need to specify the protocol otherwise it'll drop one of them based on the rc_keymaps.

7) NOW you can install LIRC. Edit */etc/lirc/hardware.conf* so that
```
LOAD_MODULES=true
DRIVER="devinput"
DEVICE="/dev/input/by-id/**YOUR DEVICE HERE***"
```

To determine where the input device is mapped just do an 'ls' of /dev/input/by-id/. It should be fairly obvious which one it is. If it's not obvious, unplug everything else until your receiver is the only thing left.

Edit */etc/lirc/lircd.conf* so that it looks like this:
```
include "/usr/share/lirc/remotes/devinput/lircd.conf.devinput"
```

Fire up lirc. Now when you run irw, you should see the output of each of your remotes, except they're all channeled as devinput.

```
/etc/rc_keymaps# irw
0000000080010069 00 KEY_LEFT devinput
0000000080010069 01 KEY_LEFT devinput
0000000080010069 00 KEY_LEFT devinput
000000008001006a 00 KEY_RIGHT devinput
000000008001006a 01 KEY_RIGHT devinput
0000000080010067 00 KEY_UP devinput
000000008001006c 00 KEY_DOWN devinput
0000000080010160 00 KEY_OK devinput
0000000080010160 00 KEY_OK devinput
```

8-n) From here on out, you're on your own. Read up on [LIRC and lircmap.xml](http://wiki.xbmc.org/index.php?title=Lirc_and_Lircmap.xml)

Problems as of now: I literally have no clue WTF rc_maps.cfg does or how to use it. For some crazy reason if LIRC starts in init.d like it should, it won't work. I always have to restart it. So right now, my rc.local looks like this:
```
/etc/init.d/lirc stop
/usr/bin/ir-keytable -c
/usr/bin/ir-keytable -p NEC,RC6 -w /etc/rc_keymaps/rc6_mce
/usr/bin/ir-keytable -p NEC,RC6 -w /etc/rc_keymaps/yamaha_dvd
/usr/bin/ir-keytable -p NEC,RC6 -w /etc/rc_keymaps/samsung_stb
/etc/init.d/lirc start
```

All 3 of my remotes work on reboot, and that's better than they used to.

---

### Post by darkscout on 2011-05-10
There's also a bug in debian (and probably ubuntu's) readahead-fedora. If you use it (or plan to use it) it just makes rc_core flip out. Reported, I think, first time I've used reportbug.

With readahead
syslog: [http://sprunge.us/hSKK](http://sprunge.us/hSKK)
dmesg:  [http://sprunge.us/cWUF](http://sprunge.us/cWUF)
lsmod:  [http://sprunge.us/afbc](http://sprunge.us/afbc)

Without readahead:
syslog: [http://sprunge.us/CSFe](http://sprunge.us/CSFe)
dmesg:  [http://sprunge.us/CScd](http://sprunge.us/CScd)
lsmod:  [http://sprunge.us/BTAh](http://sprunge.us/BTAh)

syslog diff: [http://pastebin.com/RMkSr5hM](http://pastebin.com/RMkSr5hM)
dmesg diff:  [http://pastebin.com/EpSHSyfM](http://pastebin.com/EpSHSyfM)

---

### Post by gunnarflax on 2011-05-11
Hi! Thanks for the great how to! I was wondering if the same steps applies to **lirc 0.8.7** which is in the repositories. I tried installing **lirc 0.9.0** but can't complete the installation because it stops during install due to permission problems on **configure.sh**.

When I'm supposed to select the devinput driver, where does that go? In your example it's put in **DRIVER** put I only have **REMOTE_DRIVER** and **TRANSMITTER_DRIVER** in my **/etc/lirc/hardware.conf**.

---

### Post by darkscout on 2011-05-11
> **gunnarflax said:**
> Hi! Thanks for the great how to! I was wondering if the same steps applies to **lirc 0.8.7** which is in the repositories. I tried installing **lirc 0.9.0** but can't complete the installation because it stops during install due to permission problems on **configure.sh**.

When I'm supposed to select the devinput driver, where does that go? In your example it's put in **DRIVER** put I only have **REMOTE_DRIVER** and **TRANSMITTER_DRIVER** in my **/etc/lirc/hardware.conf**.

It should apply the same to 0.8.7. I know 0.9.0 is when a ton of stuff was supposed to merge (And why they push forward with 2.6.35 without 0.9.0 is beyond me).

The REMOTE_DRIVER/DRIVER thing is probably a discrepancy between 0.8.7 and 0.9.0 or between Ubuntu and Debian. If you want to double check which one you should use do a 'grep' on the init of lirc and see what it is expecting:
This should work:
```
grep DRIVER /etc/init*/lirc*
```

Use what ever the init script is looking for.

I'll try and get Natty installed on a Virtual Machine tonight and test it out.

---

### Post by YAFU on 2011-06-22
Ohhh! I was excited about the thread title. I wish I had read something like "How I Learned to Stop Worrying about LIRC"
LIRC is tedious, difficult, unfriendly. For years and with different devices LIRC is my frustration. I hate LIRC! :P

I have a USB DVB-T tuner (ISDB-T) and everything was perfect with ir-keytable.
"sudo ir-keytable -t" take my map correctly.

I have a question. Do I need to load some LIRC module? According to the thread title I assume it is not necessary, but I read in other guides that some people  load "devinput" but the LIRC version in Natty the module does not exist:

```
$ sudo modprobe devinput
[sudo] password for yafu: 
FATAL: Module devinput not found.
```

There is only one module called "lirc_dev".

By the way, my device is not shown with "ls /dev/input/by-id/". I must use the "event#". To know what is the number of event:
```
less /proc/bus/input/devices
```


In the section for the IR device, find the event on the line "H: Handlers=kbd event#"
In my case is event6. I suppose that my "/etc/lirc/hardware.conf " should be:

```
LOAD_MODULES=true
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event6"
```

I think the version of LIRC in Natty (0.8.7) uses the string "REMOTE_" as a prefix in DRIVER and DEVICE.

I think I'll try to compile and install LIRC 0.9.0. I feel it will be painful.
Now I continue the fight against LIRC ... :evil:

---

### Post by richud on 2011-07-30
..or more simply, mostly taken from [http://cobradevil.org/index.php?title=XBMC_GIT_Eden_natty_Zotac-id31](http://cobradevil.org/index.php?title=XBMC_GIT_Eden_natty_Zotac-id31)

sudo apt-get --purge remove lirc #gets rid of any existing config, must be already installed to remove config though, if you already removed it, re-add it first....
sudo apt-get install lirc

If it was cleanly removed, apt-get ending the install will trigger setup, which will ask which type of receiver, select Windows mce receiver

sudo nano -w /etc/rc.local
add the follwowing line before the "exit 0"
echo lirc > /sys/class/rc/rc0/protocols

This makes it only allow lirc.  


Just FYI, this just automates the change, if done manually would changes it to;
rc-5 nec rc-6 jvc sony [lirc]
instead of default
[rc-5] [nec] [rc-6] [jvc] [sony] [lirc]

I just installed a minimal Natty + XBMC and this fixed my MCE remote, yay!

---

### Post by hopelessone on 2012-01-12
Hi,

Im stuck, ive installed it but no response..
```
blade@oneiric:~$ ir-keytable
/sys/class/rc/: No such file or directory
blade@oneiric:~$ 
```

What to do?

---

### Post by Statia on 2012-08-06
> **hopelessone said:**
> Hi,

Im stuck, ive installed it but no response..
```
blade@oneiric:~$ ir-keytable
/sys/class/rc/: No such file or directory
blade@oneiric:~$ 
```What to do?

Same here:

```
root@quokka:/# ir-keytable 
Couldn't find any node at /sys/class/rc/rc*.
root@quokka:/# echo lirc > /sys/class/rc/rc0/protocols
bash: /sys/class/rc/rc0/protocols: No such file or directory

```How to get the file structure for rc? Can one just mkdir it, or is /sys like /dev and does one need mknod or some equivalent?

---

