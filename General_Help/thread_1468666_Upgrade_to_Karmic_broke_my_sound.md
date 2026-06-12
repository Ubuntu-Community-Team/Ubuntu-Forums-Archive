---
title: "Upgrade to Karmic broke my sound"
date: 2010-05-01
forum: General Help
---

### Post by Admiral Yi on 2010-05-01
Hello,
Just upgraded to Karmic using the update manger. After the update, sound is no longer working. When I go to system>preferences>sounds and go to the Hardware tab it says there are no devices to configure. Any ideas on what I can do?

---

### Post by Shadow12313 on 2010-05-01
You could try updating to the new lucid lynx.

---

### Post by Admiral Yi on 2010-05-02
I was planning to soon. Do you think it would be better to re-install using the disk this time?

---

### Post by GSF1200S on 2010-05-02
> **Admiral Yi said:**
> I was planning to soon. Do you think it would be better to re-install using the disk this time?

Officially, Ubuntu supports upgrading. While upgrades have gotten a lot less painful than they used to be, I would still suggest doing a clean install if you have the time and you have backups/nothing to lose. 

As for your sound issue, the only thing I can suggest is:
```
sudo apt-get remove pulseaudio
sudo killall pulseaudio
sudo /etc/init.d/alsa-utils restart
```
You can try rebooting after this, but it may not work. If you have no device to configure, then it would seem that you have a chipset not supported. If the above commands dont work, post the results of:
```
lspci
```
and
```
cat /proc/asound/cards
```
and maybe someone will be able to help you. Admittedly I dont know much about linux sound- just enough to get me by.

---

### Post by Admiral Yi on 2010-05-04
Those top commands didn't help. The last one produced pages and pages od this repeated:
```
Invalid card number.                                                                                                                           
Usage: amixer <options> [command]                                                                                                              
Available options:                                                                                                                             
  -h,--help       this help                                                                                                                    
  -c,--card N     select the card                                                                                                              
  -D,--device N   select the device, default 'default'                                                                                         
  -d,--debug      debug mode                                                                                                                   
  -n,--nocheck    do not perform range checking                                                                                                
  -v,--version    print version of this program                                                                                                
  -q,--quiet      be quiet                                                                                                                     
  -i,--inactive   show also inactive controls                                                                                                  
  -a,--abstract L select abstraction level (none or basic)                                                                                     
  -s,--stdin      Read and execute commands from stdin sequentially                                                                            
Available commands:                                                                                                                            
  scontrols       show all mixer simple controls                                                                                               
  scontents       show contents of all mixer simple controls (default command)                                                                 
  sset sID P      set contents for one mixer simple control                                                                                    
  sget sID        get contents for one mixer simple control                                                                                    
  controls        show all controls for given card                                                                                             
  contents        show contents of all controls for given card                                                                                 
  cset cID P      set control contents for one control                                                                                         
  cget cID        get control contents for one control
```

Lspci came up with this, which seems to suggest that my sound card was found:
```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
**00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller**
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
02:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
03:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

And that last command turned up:
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfbff8000 irq 22
```

Hope all this is helpful to someone.

---

### Post by dino99 on 2010-05-04
install paprefs and gnome-alsamixer (set prefs as you want)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

