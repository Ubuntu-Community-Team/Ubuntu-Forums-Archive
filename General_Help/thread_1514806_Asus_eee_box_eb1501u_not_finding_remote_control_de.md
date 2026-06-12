---
title: "Asus eee box eb1501u not finding remote control device"
date: 2010-06-21
forum: General Help
---

### Post by FryinRyan on 2010-06-21
I have a Asus eee box eb1501u running Kubuntu 10.04 LTS (32 bit) and I am trying to get the remote control to work. Many guides for example this one [http://wiki.xbmc.org/index.php?title=HOW-TO_preform_a_Miminal_Ubuntu_and_XBMC_install_on_a_Asus_EeeBox_PC_EB150]("http://wiki.xbmc.org/index.php?title=HOW-TO_preform_a_Miminal_Ubuntu_and_XBMC_install_on_a_Asus_EeeBox_PC_EB150") first states that you should run:
> cat /proc/bus/input/devices 
There you should see your remote looking something like this: 
Name="PHILIPS MCE USB IR Receiver- Spinel plusf0r ASUS" 
The problem is Im stuck with no output like that! This is my output:
> I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input2
U: Uniq=
H: Handlers=mouse0 event2 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=046d Product=c315 Version=0110
N: Name="Logitech Logitech USB Keyboard"
P: Phys=usb-0000:00:06.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1:1.0/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=120013
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=05f3 Product=021f Version=0100
N: Name="Contour Design Contour RollerMouse "
P: Phys=usb-0000:00:06.0-3/input0
S: Sysfs=/devices/pci0000:00/0000:00:06.0/usb4/4-3/4-3:1.0/input/input4
U: Uniq=
H: Handlers=mouse1 event4 
B: EV=17
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0003 Vendor=09da Product=000a Version=0110
N: Name="A4Tech PS/2+USB Mouse"
P: Phys=usb-0000:00:06.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:06.0/usb4/4-2/4-2:1.0/input/input5
U: Uniq=
H: Handlers=mouse2 event5 
B: EV=17
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=343
B: MSC=10

I: Bus=0001 Vendor=10ec Product=0662 Version=0001
N: Name="HDA Digital PCBeep"
P: Phys=card0/codec#0/beep0
S: Sysfs=/devices/pci0000:00/0000:00:08.0/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=40001
B: SND=6


Before I removed the Windows 7 installation I tested the remote in Windows to make sure it worked and it did. I cant see that there is a possibility to turn on or off the IR-device in the bios settings!? I would really like to make it work in Kubuntu to. Im pretty n00bish at Linux but I think I can figure it out if someone would point me in the right direction.

---

### Post by magic-neophyte on 2010-07-05
I cannot bring up the page you mentioned.

You need to install the package lirc

sudo apt-get install lirc

I'll try to let you know when I get my remote to work.

---

### Post by magic-neophyte on 2010-07-05
First install lirc as per sudo apt-get install lirc

Then copy-paste the description of your remote into /etc/lirc/lircd.conf like so: gksudo gedit /etc/lirc/lircd.conf

You have to create a directory for lirc to use in /var/run/lirc, like so:

sudo mkdir /var/run/lirc

Now, the remote sensor is not active by default. To wake it from sleep mode, you need to remove the kernel driver, activate the sensor, and then reload the kernel driver.

You can use the following script (save this to a file (remote.sh) , then chmod +x remote.sh to allow it to run)

#!/bin/bash
/etc/init.d/lirc stop 
rmmod lirc_it87
echo activate > /sys/devices/pnp0/00:09/resources
modprobe lirc_it87
/etc/init.d/lirc start

The above script is courtesy of some website, but I cannot find it right now. 
Thanks goes to the (now sadly) anonymous author.

Run the script. ( type: sudo ./remote.sh into the Terminal )

Check whether lirc is running using: pstree | grep lirc

The remote included with eeebox 1501U in Northern Europe, is the Philips SRM5100
You can get the file from the lirc website, or I've pasted it below. 

To get VLC to work with lirc, all you have to do is this:

Tools->Preferences
Show settings->All (bottom left, select all)
Expand Interface
Select Control Interfaces
Check "Infrared remote control interface"
Save, close, restart VLC
Enjoy!

Thanks to Spectre5 for this great tip.

magic neophyte


#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.
#####################################
# START PHILIPS SRM5100 CONFIGURATION OPTIONS
# inserted 5-7-2010 by me to fix remote funtions
#
# this config file was automatically generated
# using lirc-0.8.3(default) on Tue Jul 15 22:50:21 2008
#
# edited by DavidGSDavies on Wednesday, 23 September 2009 16:52 
# to add codes for the power and chan_up buttons,
# which were previously missing.
#
# contributed by
#
# brand:                       Philips
# model no. of remote control: SRM5100
# devices being controlled by this remote:
#

begin remote

  name  Philips_SRM5100
  bits           16
  flags RC6|NO_HEAD_REP|CONST_LENGTH
  eps            30
  aeps          100

  header       2710   850
  one           463   421
  zero          463   421
  pre_data_bits   21
  pre_data       0x37FF0
  gap          106014
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000

      begin codes
          1                        0xFBFE
          2                        0x7BFD
          3                        0xFBFC
          4                        0x7BFB
          5                        0xFBFA
          6                        0x7BF9
          7                        0xFBF8
          8                        0x7BF7
          9                        0xFBF6
          *                        0x7BE2
          0                        0xFBFF
          #                        0x7BE3
          clear                    0xFBF5
          t                        0x7BA5
          enter                    0xFBF4
          red                      0x7BA4
          green                    0xFBA3
          yellow                   0x7BA2
          blue                     0xFBA1
          tv_rec                   0x7BB7
          guide                    0xFBD9
          tv_play                  0x7BDA
          menu                     0xFBDB
          vol_down                 0x7BEE
          vol_up                   0xFBEF
          mute                     0x7BF1
          chan_up                  0xFBED
          chan_down                0xFBEC
          left                     0xFBDF
          down                     0x7BE0
          right                    0xFBDE
          up                       0x7BE1
          ok                       0xFBDD
          back                     0x7BDC
          i                        0xFBF0
          mce                      0x7BF2
          prev_track               0xFBE4
          next_track               0x7BE5
          rewind                   0xFBEA
          play                     0x7BE9
          forward                  0xFBEB
          rec                      0x7BE8
          pause                    0xFBE7
          stop                     0x7BE6
          power                    0x7BF3
      end codes

end remote

---

### Post by FryinRyan on 2010-07-05
Thanks for the reply and thanks for showing what to put in the lirc-files. But im not getting this to work.

1. The thing I mentioned first:
> cat /proc/bus/input/devices
that is still not showing the infrared remote, its the same list
as I first posted. Does this mean that it doesnt find
my infrared hardware? But this is also strange since I tested
the remote in Windows 7, and it worked there before I removed Win7?
Any ideas about this? Im guessing lirc is of no use unless it actually
finds the hardware first?

2. Do I also need to use IRKICK (KDEs lirc-server) after having installed lirc the way you described?

---

### Post by xaverx on 2010-07-15
try this howto [http://wiki.xbmc.org/index.php?title=HOW-TO_preform_a_Miminal_Ubuntu_and_XBMC_install_on_a_Asus_EeeBox_PC_EB1501#ASUS_Remote_Control](http://wiki.xbmc.org/index.php?title=HOW-TO_preform_a_Miminal_Ubuntu_and_XBMC_install_on_a_Asus_EeeBox_PC_EB1501#ASUS_Remote_Control)

---

### Post by FryinRyan on 2010-07-15
That was the link I had hoped to link to in my first post, I see now that it doesn't work. Anyway it doesn't help as you can see from my output it doesn't list the remote, but the remote worked in windows7, as I stated above.

---

### Post by FryinRyan on 2010-07-15
Also as you can see I, for some reason have 2 powerbuttons in my output, whatever that means? :-/

---

### Post by FryinRyan on 2010-08-05
Bumpety-bump... ?

---

### Post by sircube on 2010-08-10
I have EXACTLY the same problem, let me know if managed to solve it...
thx.

---

### Post by gilson585 on 2010-08-11
I have had a similar problem on a asus mainboard. I found that if you hit the power button on the remote before the kernel loads it works. To try this I suggest you hold the left shift key immediately after post to get the gurb loader screen. This way you can hit the power button on the mce remote b4 it loads anything. Lemme kno if this works.

---

### Post by FryinRyan on 2010-08-13
> **gilson585 said:**
> I have had a similar problem on a asus mainboard. I found that if you hit the power button on the remote before the kernel loads it works. To try this I suggest you hold the left shift key immediately after post to get the gurb loader screen. This way you can hit the power button on the mce remote b4 it loads anything. Lemme kno if this works.

OK I'll try this. Did you also have 2 powerbuttons listen when you ran: cat /proc/bus/input/devices

---

### Post by gilson585 on 2010-08-16
Sorry for takin so long to reply. Had lots going on here. I did try "cat /proc/bus/input/devices" and to my surprise mine looks exactly like yours including the two power buttons. Only exception was I have a diff mouse but even though I can get my usb ir reciever to work it isn't listed.

---

### Post by r2d2chfr on 2010-08-18
Hi, I have exactly the same issue (two power device, and no IR receiver) on ubuntu 10.4.
I tried to push the power button before system load, as mentionned, but it changed nothing.
Any others ideas?

Thanks, Luca

---

### Post by magic-neophyte on 2010-08-18
Aha! I have some new part of the solution. (Sorry for taking so long, I was away on holiday.)

You need to ACTIVATE the remote sensor first!

Use the command:

sudo echo activate > /sys/devices/pnp0/00:09/resources

NOW it should show up in lspci

(See also the fix I posted earlier, now edited to reflect this new info.)

If it doesn't work for you, but you have the exact same machine, let me know.

Good luck!

---

### Post by FryinRyan on 2010-08-18
> **magic-neophyte said:**
> Aha! I have some new part of the solution. (Sorry for taking so long, I was away on holiday.)

You need to ACTIVATE the remote sensor first!

Use the command:

echo activate > /sys/devices/pnp0/00:09/resources

NOW it should show up in lspci

(See also the fix I posted earlier, now edited to reflect this new info.)

If it doesn't work for you, but you have the exact same machine, let me know.

Good luck!

Thanks alot for all your help. I had some problems still but I found a thread over at [xmbc-forum]("http://forum.xbmc.org/showthread.php?t=47651&page=8") and I began by following the 
guide by kalimero (post #76). I did everything except the "Move/link the new modules to the right location:" step,
which someone later in the thread pointed out wasn't needed anymore. 

But there was still problems that the user kreischweide (post #86) pointed out about the ASUS EB1501. That problem was
solved by user anmo6 in post #89. 

Going back to post #76 in the thread after doing what was stated in post #89 then I successfully managed to do:

> If modules are loaded successfully then test remote by:
mode2 -d /dev/lirc0 and press buttons on remote (shipped Asus remote works perfectly)
you should get an output similar to the following in the terminal window when pressing the buttons on the remote:
space 34
pulse 174
space 42834
pulse 174
space 40786
pulse 174
space 42834
pulse 254
space 42754
pulse 182
space 42826
pulse 174
space 40786
pulse 2414
space 802
pulse 438
space 386
pulse 374

Ctrl+c to end test

Test irw - are the signals decoded correctly by lircd
irw /dev/lircd and start pressing buttons on the remote

you should get an output similar to the following:
000000037ff07bf2 00 Home mceusb
000000037ff07bf2 00 Home mceusb
000000037ff07bde 00 Right mceusb
000000037ff07bde 01 Right mceusb
000000037ff07bdf 00 Left mceusb
000000037ff07bdf 01 Left mceusb

Ctrl+c to end test

Also in the above mentiond post #89 when doing:

> 3) echo activate > /sys/devices/pnp0/00:09/resources

I at least, have to be root. So first run sudo su.

And I also think this is a crucial step for us eb1501 owners:

> Also I modified /etc/modprobe.d/lirc.conf to be like
alias char-major-61 lirc_dev
options lirc_it87 irq=5 io=0x2f8

---

### Post by FryinRyan on 2010-08-20
I got my system working now. I found this guide, [http://wiki.xbmc.org/index.php?title=Talk:HOW-TO_preform_a_Miminal_Ubuntu_and_XBMC_install_on_a_Asus_EeeBox_PC_EB1501]("http://wiki.xbmc.org/index.php?title=Talk:HOW-TO_preform_a_Miminal_Ubuntu_and_XBMC_install_on_a_Asus_EeeBox_PC_EB1501") and maybe we only need this info now, but as I said above I did the whole
kalimero guide. 

The last step was making the /sys/devices/pnp0/00:09/resources allways active at boot. That was just a matter of adding the last line explained in the link above.
> 3) create /etc/modprobe.d/lirc.conf and add the three lines

alias char-major-61 lirc_dev
options lirc_it87 irq=05 io=0x2f8
install lirc_it87 echo activate > /sys/devices/pnp0/00:09/resources ; modprobe --ignore-install lirc_it87 $CMDLINE_OPTS


Im going to mark this thread as solved now.:)

---

### Post by el_pazzo on 2010-09-17
hi!
I'm sorry, but i have to reopen this one:
I do have the same problem as stated in your first post, but cannot activate the device. Calling the script from /etc/rc.local doesnt do the trick. also, when i call the activate part as root directly, it gives:

#echo 'activate' > /sys/devices/pnp0/00:09/resources
bash: echo: write error: Device or resource busy

I am on ubuntu 10.04.1 and have an EB1501**P**
but am quite sure that its got the same internals..
Thanks,
/pazz

---

### Post by el_pazzo on 2010-09-18
ok, it seems that the device i have to activate is not 00:09 but 00:0a.
after a while and manually loading the lirc_it87 module it works.
BUT:
Has anyone of you managed to get it working after a suspend/resume?
I know there are threads about this, but this seems to be related to the above mod-prob: i do have /dev/lirc0 after the resume. lircd starts fine 
but irw simply doesn't show any presses.
The strange thin is that after a resume i cannot get this to work again:
I have the same output for the cat ../resources on all devices and all.
I also tried unloading lirc_it87 and reloading it again (also during suspend via /etc/default/acpi-support)..
any comments?
/pazz

---

### Post by rulleguru on 2010-09-19
I've tried every guide but cant get it to work with the eb1501p.
Any complete guides for this device?

---

### Post by Jörn on 2011-08-28
Try installing lirc 0.9.0 from oneric. Worked for me. 

Found the hint on xbmc.org forum  [here]("http://forum.xbmc.org/showpost.php?p=825389&postcount=140").

---

