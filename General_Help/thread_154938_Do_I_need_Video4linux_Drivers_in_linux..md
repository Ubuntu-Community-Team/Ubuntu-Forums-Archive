---
title: "Do I need Video4linux? Drivers in linux."
date: 2006-04-04
forum: General Help
---

### Post by TmP on 2006-04-04
Hi!

I've been trying to make my tv card work under Ubuntu for quite some time now. With no success.

How can I check if it works?

Here's my lspci feed
>  0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 02)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
0000:00:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: S3 Inc. Savage 4 (rev 04)


and here's my lsmod

> tempest@TmP:~$ lsmod | grep tv
bttv                  141456  2 dvb_bt8xx,bt878
video_buf              19844  1 bttv
i2c_algo_bit            8584  1 bttv
v4l2_common             5888  1 bttv
btcx_risc               4872  1 bttv
tveeprom               12568  1 bttv
videodev                9344  1 bttv
firmware_class          9472  4 dvb_bt8xx,sp887x,bttv,or51211
i2c_core               19728  15 i2c_acpi_ec,i2c_viapro,via686a,i2c_sensor,dvb_bt8xx,nxt6000,mt352,sp887x,dst,tuner,bttv,i2c_algo_bit,tveeprom,cx24110,or51211

I've been blaming my lack of success on MySQL which refused to work. Now I reinstalled the Ubuntu, Mysql works, MythTV installs fine, but i just don't know what to do about my tv capture card.

It's a not very well supported model:
Leadtek win2000XP RM,
based on a bt878 chipset (or at least that's what ubuntu thinks)

So my questions are:
Do I need to download the drivers or are they alredy in Ubuntu? 
Where can I install them,  where are the drivers kept in Ubuntu?

Thanx!

---

### Post by TmP on 2006-04-25
Ok, stupid me.

I'm getting the hang of it now.
My tuner is not recognised right (winfast2000xp rm with a bt878 chip)

I solved the problem basing on this guide:
[http://ubuntuforums.org/showthread.php?t=45220](http://ubuntuforums.org/showthread.php?t=45220)

If you bought a Winfast2000xp card (RM) do this:

1. open terminal 
2. go to /ect
3. type: "sudo gedit modprobe.conf"
4. add this line: "options bttv card=**34** tuner=38"
5. save in /ect
6. should work from the next restart

watch out for some of the other guides to this solution. They suggest adding stuff to modules. This is unnecesary.

Try tvtime. Get it of Synaptics. Type:"sudo tvtime-scanner".
If you prefare xawtv type: "scantv"
If you get an error, check where the tuner got mounted. In my case it was vbi0 instead of vbi.

In that case type:"scantv -C /dev/vbi0"

and btw. I hope that it's fixed in Dapper. If not, who can I inform of this problem? It seems to be drivers related. V4L?

---

