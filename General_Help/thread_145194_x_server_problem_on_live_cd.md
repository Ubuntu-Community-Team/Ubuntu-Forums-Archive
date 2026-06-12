---
title: "x server problem on live cd"
date: 2006-03-15
forum: General Help
---

### Post by rhomsy on 2006-03-15
Hi, I hope someone can help me.  I am trying to avoid using M$ at work, and I want to switch to ubuntu.  I have a new P4 with integrated intel graphics chipset.  I don't want to install ubuntu until I'm sure it works from the live cd.  

when I boot the breezy live cd, it seems to go fine until it tries to launch x.  i just get a blank screen.  With Dapper Flight 5, when it tries to goto x, i get "snow/static".  I've read the wiki and some posts from this forum, and I see people talking about editing the x.conf file... but to be honest, I can't seem to piece together what to do.  

I'm assuming that ubuntu can't seem to autoconfig my graphics chipset.  How can I fix this.  Will the final release of Dapper fix these problems?  If so, maybe I should just wait... or is that wimpy?

Thanks in advance for any help anyone can give me.  I can't stand booting into Windows XP every morning.  I want to get this working.

---

### Post by Aine on 2006-03-15
I think with the live CD it might not support intel and nvidia too well, I can't remember. Anyhow, my advice would be install Ubuntu, then you can update your packages and xorg.conf to use the intel drivers.

---

### Post by bluevoodoo1 on 2006-03-15
I had problems with a Live CD yesterday. Here's what I did... You can type

```
sudo dpkg-reconfigure xserver-xorg
```

it will bring up a dialog for configuring the video. To be safe you can choose "vesa" as the driver and it should work. Then back at the command line type...

```
sudo /etc/init.d/gdm restart
```

that should hopefully work. 

I can't get my computer to run a LiveCD after I upgraded to a video card rather than using the onboard video. Here's what I did to fix that. (This might also be an idea if the first thing mentioned above doesn't work). 

Back at the command line check your video bus location with...

```
lspci
```

Make note of its number. Here's an example... the line in red is what Ubuntu recognizes at 01:05.0, but my monitor is now plugged into my nvidia card 02:09.0 so in the "dpkg-reconfigure" dialog I had to change the location to 02:09.0. 
```

bluevoodoo1@ubuntu:~$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5833 (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5838
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4347 (rev 01)
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4348 (rev 01)
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4345 (rev 01)
0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 1a)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4349
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller (rev 01)
[COLOR="Red"]0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5834[/COLOR]
0000:02:08.0 Ethernet controller: 3Com Corporation 3Com 3C920B-EMB-WNM Integrated Fast Ethernet Controller (rev 40)
[COLOR="DarkGreen"]0000:02:09.0 VGA compatible controller: nVidia Corporation: Unknown device 0326 (rev a1)[/COLOR]
0000:02:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:02:0c.0 CardBus bridge: ENE Technology Inc CB710 Cardbus Controller (rev 02)
0000:02:0c.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
```

Run "sudo dpkg-reconfigure xserver-xorg" again and when it asks for the location of your video bus make sure you type the correct one in (the one you wrote down). When it finishes ```
sudo /etc/init.d/gdm restart
``` should get you up and running.

EDIT: You might not need the "sudo" in front of the commands. I used them in the Live CD, but you probably won't need them (you *will* need them if you choose to install Ubuntu)

---

