---
title: "Trouble with lirc in Ubuntu 10.04"
date: 2010-05-11
forum: General Help
---

### Post by avoa on 2010-05-11
Hi,

I have trouble with lirc after upgrading to Ubuntu 10.04. The lirc behavior is weird. 
Lirc was working in Karmic Koala and during upgrade to 10.04 I haven't made any changes. Actually lirc is used to control Mythtv, which now is not working with remote.
I have checked config files and everything seems to be correct. When I use irw command, I can get correct codes from remote according to config files. When I use command ircat mythtv, then codes are according to lircrc file. So, everything seems to be correct. But Mythtv cannot recognize remote commands. After fresh boot/restart arrow keys are working in Mythtv, but after some time they also stop to respond - weird.
Situation is: remote is sending codes, lirc translates it to correct commands, lircrc translates commands for mythtv, but mythtv cannot receive commands. It seems to be Mythtv problem, but I suspect other reason.
My computer have 2 IR devices: integrated iMON IR receiver and IR receiver in Hauppauge DVB-T card (Hauppauge Nova T-500). It seems, that Ubuntu prefers iMON device, but I want to use Hauppauge. I set Hauppauge permanently to input event7 and after that it starts to work. I suspect that two IR devices can conflict. Anyhow, I didn't succeed to get Mythtv to work with Hauppauge IR device.
Can anybody tell any hints or suggestions, where the problem is and how to fix it? How to deactivate iMON (I'm using iMON LCD panel)?

Avo Aasma

---

### Post by avoa on 2010-05-11
I will add some technical details to previous post.

**Excerpt from /etc/lirc/harware.conf:**
REMOTE="NOVA-T500"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/event7"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge_novat500"

**Excerpt from lircd.conf.hauppauge_novat500**
begin remote

 name  NOVA-T500
 bits           16
 eps            30
 aeps          100

 one             0     0
 zero            0     0
 pre_data_bits   16
 pre_data       0x1
 gap          199999
 toggle_bit      0

     begin codes
         Go                       0x0162
         Power                    0x0074
         TV                       0x0179
         Videos                   0x0189
         Music                    0x0188
         Pictures                 0x00E2
         Guide                    0x016D
         Radio                    0x0181
         ArrowUp                  0x0067
         ArrowLeft                0x0069
         OK                       0x0160
         ArrowRight               0x006A
         ArrowDown                0x006C
         BackExit                 0x009E
         Menu                     0x008B
         VolumeUp                 0x0073
         VolumeDown               0x0072
         PrevCh                   0x016B
         Mute                     0x0071
         ChannelUp                0x0192
         ChannelDown              0x0193
         Record                   0x00A7
         Rewind                   0x00A8
         SkipBack                 0x0195
         Play                     0x00CF
         Pause                    0x0077
         Stop                     0x0080
         Fwdwind                  0x00D0
         SkipFwd                  0x0197

**Excerpt from lircrc:**
################## MythTV Control ######################

#	Remote Button
##	MythTV function


#	Go
##	Go to Main menu
begin
prog = mythtv
button = Go
config = ALT+Z
end

#	Power
##	Info
begin
prog = mythtv
button = Power
config = i
end

#	TV
##	Go to Watch TV
begin
prog = mythtv
button = TV
config = ALT+T
end

#	Videos
##	Go to MythVideo
begin
prog = mythtv
button = Videos
config = ALT+V
end

#	Music
##	Go to MythMusic
begin
prog = mythtv
button = Music
config = ALT+M
end

#	Pictures
##	Go to MythGallery
begin
prog = mythtv
button = Pictures
config = ALT+P
end

#	Guide
##	display EPG
begin
prog = mythtv
button = Guide
config = s
end


**Codes from irw:**
avo@MediaU:~$ irw
0000000000010067 00 ArrowUp NOVA-T500
0000000000010160 00 OK NOVA-T500
000000000001006c 00 ArrowDown NOVA-T500
00000000000100cf 00 Play NOVA-T500
0000000000010077 00 Pause NOVA-T500
0000000000010197 00 SkipFwd NOVA-T500
00000000000100d0 00 Fwdwind NOVA-T500
0000000000010192 00 ChannelUp NOVA-T500
0000000000010193 00 ChannelDown NOVA-T500
^Z
[5]+  Stopped                 irw

**Codes from ircat**
avo@MediaU:~$ ircat mythtv
Up
Space
Down
Return
P
PgDown
Right
Up
Down
^Z
[6]+  Stopped                 ircat mythtv

avo@MediaU:~$ **dmesg | grep lirc**
[   17.598845] lirc_dev: IR Remote Control driver registered, major 61 
[   17.672203] lirc_imon: Driver for SoundGraph iMON MultiMedia IR/Display, v0.6
[   17.672243] lirc_dev: lirc_register_driver: sample_rate: 0
[   17.672329] lirc_imon: Registered iMON driver (lirc minor: 0)
[   17.695065] lirc_imon: iMON device (15c2:ffdc, intf0) on usb<4:2> initialized
[   17.695121] usbcore: registered new interface driver lirc_imon

avo@MediaU:~$ **lsusb**
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 004 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 2040:8400 Hauppauge 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**Excerpt from cat /proc/bus/input/devices**
I: Bus=0003 Vendor=15c2 Product=ffdc Version=0000
N: Name="iMON PAD IR Mouse (15c2:ffdc)"
P: Phys=usb-0000:00:02.0-4/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb4/4-4/4-4:1.0/input/input4
U: Uniq=
H: Handlers=mouse1 event4 
B: EV=7
B: KEY=1f0000 0 0 0 0
B: REL=103


I: Bus=0003 Vendor=2040 Product=8400 Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:01:08.2-1/ir0
S: Sysfs=/devices/pci0000:00/0000:00:08.0/0000:01:08.2/usb3/3-1/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=14afc336 284284d00000000 0 480058000 219040000801 9e96c000000000 90020000000ffd

**avo@MediaU:~$ ls -l /dev/lirc***
crw-rw---- 1 root root 61, 0 2010-05-11 16:31 /dev/lirc0
srw-rw-rw- 1 root root     0 2010-05-11 16:31 /dev/lircd

**Some more details.**
Mythtv frontend log file shows:
2010-05-04 16:35:51.520 LIRC: Successfully initialized '/dev/lircd' using '/home/avo/.mythtv/lircrc' config

When I restart lirc (sudo /etc/init.d/lirc restart), then Mythtv cannot anymore initialize lirc.

When I used Ubuntu Karmic, then lirc worked with Mythtv without problems.
Now after reboot during some time (ca 10 min) some buttons on remote works (arrows, 1, 2, may be some more) and then connection to remote is lost. 
This behavior is weird. Maybe somebody can explain, what is going on and how to fix this. My ideas are exhausted.

---

### Post by avoa on 2010-05-14
Hi again.
I **solved** this problem by myself.
First I upgraded Mythtv, coming with Update Manager. I noticed, that database was also upgraded. After upgrade Mythfrontend started with error message, something like: cannot connect to backend server. Then I completely removed Mythtv and installed it again. After that Mythtv started normally. Then I noticed, that irw don't show correct remote codes. I found, that /etc/lirc/hardware.conf was changed. I updated hardware.conf to previous values. Then I restarted lirc and everything worked fine. Remote can control Mythtv as expected.
I suppose that I was using Mythtv version, that wasn't consistent.

---

