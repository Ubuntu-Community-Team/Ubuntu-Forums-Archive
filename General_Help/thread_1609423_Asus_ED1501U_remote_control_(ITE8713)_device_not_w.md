---
title: "Asus ED1501U remote control (ITE8713) device not work"
date: 2010-10-30
forum: General Help
---

### Post by fishMD on 2010-10-30
After 4 days of tryings I still can't set remote control in work state at Ubuntu 10.10 for using in XBMC (xbmc-standalone), but in Windows 7 working fine.
I try many methods but still no luck.

[http://wiki.xbmc.org/index.php?title=Talk:HOW-TO_perform_a_miminal_Ubuntu_and_XBMC_install_on_a_Asus_EeeBox_PC_EB1501#No_MCE_USB_IR_Receiver]("http://wiki.xbmc.org/index.php?title=Talk:HOW-TO_perform_a_miminal_Ubuntu_and_XBMC_install_on_a_Asus_EeeBox_PC_EB1501#No_MCE_USB_IR_Receiver") : 
```
...
Now try using irw
xbmc:$ irw
Press some keys and you should get some output.
...
```
but my output after reboot:
```
fishmd@eee-tv:~$ irw
fishmd@eee-tv:~$ irw
connect: Connection refused
fishmd@eee-tv:~$
```

[http://wiki.xbmc.org/index.php?title=Talk:HOW-TO_perform_a_miminal_Ubuntu_and_XBMC_install_on_a_Asus_EeeBox_PC_EB1501#No_MCE_USB_IR_Receiver:]("http://wiki.xbmc.org/index.php?title=Talk:HOW-TO_perform_a_miminal_Ubuntu_and_XBMC_install_on_a_Asus_EeeBox_PC_EB1501#No_MCE_USB_IR_Receiver")
same trouble, but after cmd "mode2" i see "killed"

[http://ubuntuforums.org/showthread.php?t=1514806]("http://ubuntuforums.org/showthread.php?t=1514806") also not helped.

lircd with -n option:
```
fishmd@eee-tv:~$ sudo lircd -n
lircd-0.8.7-pre3[2102]: lircd(default) ready, using /var/run/lirc/lircd
### here I run irw
lircd-0.8.7-pre3[2102]: accepted new client on /var/run/lirc/lircd
lircd-0.8.7-pre3[2102]: could not get file information for /dev/lirc
lircd-0.8.7-pre3[2102]: default_init(): No such file or directory
lircd-0.8.7-pre3[2102]: Failed to initialize hardware
```

hardware.conf:
```
# hardware.conf for eb1501 German / Asian Edition
# 
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_it87"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
LOAD_MODULES="true"
LIRCMD_CONF=""
```

lircd.conf:
```
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"
```

Few logs:
```
fishmd@eee-tv:~$ dmesg | grep lirc
[   21.503062] lirc_dev: IR Remote Control driver registered, major 61 
[   21.506764] lirc_dev: lirc_register_driver: sample_rate: 0
[   21.506959] lirc_it87: found IT8720.
[   21.506979] lirc_it87: set default io 0x2f8
[   21.506999] lirc_it87: set default irq 0x5
[   21.507054] lirc_it87: I/O port 0x02f8, IRQ 5.
[   21.507069] lirc_it87: Installed.
[   76.280376] IP: [<f806f48b>] irctl_ioctl+0x2b/0x310 [lirc_dev]
[   76.280413] Modules linked in: aes_i586 aes_generic lirc_it87 lirc_dev binfmt_misc parport_pc ppdev nvidia(P) snd_hda_codec_nvhdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm arc4 ath9k ath9k_common ath9k_hw snd_seq_midi ath snd_rawmidi mac80211 snd_seq_midi_event snd_seq snd_timer snd_seq_device cfg80211 asus_atk0110 lp snd psmouse soundcore shpchp eeepc_wmi xhci_hcd serio_raw i2c_nforce2 snd_page_alloc led_class parport sparse_keymap agpgart usbhid hid ahci r8169 libahci mii usb_storage
[   76.280493] Pid: 1343, comm: lircd Tainted: P            2.6.35-22-generic #35-Ubuntu EB1501/EB1501
[   76.280507] EIP is at irctl_ioctl+0x2b/0x310 [lirc_dev]
[   76.280531] Process lircd (pid: 1343, ti=f4ece000 task=f4eabf70 task.ti=f4ece000)
[   76.280613]  [<f806f460>] ? irctl_ioctl+0x0/0x310 [lirc_dev]
[   76.280721] EIP: [<f806f48b>] irctl_ioctl+0x2b/0x310 [lirc_dev] SS:ESP 0068:f4ecff2c

```

```
fishmd@eee-tv:~$ cat /sys/devices/pnp0/00:09/resources & cat /sys/devices/pnp0/00:09/options
[1] 2078
state = active
io 0x2f8-0x2ff
irq 5
Dependent: 00 - Priority acceptable
  port 0x2f8-0x2f8, align 0x7, size 0x8, 16-bit address decoding
  irq 3,4,5,6,7,2/9,10,11,12 High-Edge
[1]+  Done                    cat /sys/devices/pnp0/00:09/resources
fishmd@eee-tv:~$ 
```

```
fishmd@eee-tv:~$ hal-device '/org/freedesktop/Hal/devices/pnp_ITE8713'
udi = '/org/freedesktop/Hal/devices/pnp_ITE8713'
  linux.hotplug_type = 2  (0x2)  (int)
  pnp.id = 'ITE8713'  (string)
  linux.subsystem = 'pnp'  (string)
  info.subsystem = 'pnp'  (string)
  info.product = 'PnP Device (ITE8713)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_ITE8713'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:09'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)

fishmd@eee-tv:~$ 

```

Did any body make it working? Can help me?

---

### Post by gdi2k on 2010-12-23
I've got the same hardware with exaclty the same problem. Did you manage to get it resolved?

---

### Post by fishMD on 2010-12-23
> **gdi2k said:**
> I've got the same hardware with exaclty the same problem. Did you manage to get it resolved?

No,I install Windows, but think than it's lirc bug. Try use earlier version.

---

### Post by r2d2chfr on 2011-02-22
Hi, 
I also have this problem.
Anyone got this f****g remote working on ubuntu 10.10?
I also tried to compile and install lirc 0.8.6, but I got errrors

Thanks

---

### Post by gdi2k on 2011-02-23
No, never got it sorted, very annoying. Ended up using an unused iPod Touch as a controller instead using an App. It's cool as you can browse movies and music direct on the iPod prior to playing, but it's slower to move around the interface using the onscreen remote. 

If you ever get it fixed, please let me know!

---

### Post by r2d2chfr on 2011-02-23
Mmm, 
I think I will reintall a 10.04, it was working perfectly...

---

### Post by nugator on 2012-05-06
Ok, I finally got my remote to work in XBMC!

I've got an **Asus EB1501P-B0100** bought in Sweden with the "**ITE8713 CIR transceiver**" (reported by *cat /proc/bus/input/devices*).

I'm running XBMC 11.0 (Eden) on my Ubuntu 12.04.

I installed **lirc**:
```
apt-get install lirc
```

This is my */etc/lirc/hardware.conf*:
```
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev lirc_it87"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
LOAD_MODULES="true"
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
REMOTE_MODULES=""
REMOTE_LIRCD_CONF=""
```

My */etc/lirc/lircd.conf*:
```
begin remote

  name  asusremote
  bits           13
  flags RC6|CONST_LENGTH
  eps            30
  aeps          100

  header       2707   837
  one           476   403
  zero          476   403
  pre_data_bits   24
  pre_data       0x1BFF83
  gap          105663
  toggle_bit_mask 0x8000
  rc6_mask    0x100000000

      begin codes
          KEY_POWER                0x1BF3
          KEY_PAUSE                0x1BE7
          KEY_RECORD               0x1BE8
          KEY_STOP                 0x1BE6
          KEY_PLAY                 0x1BE9
          KEY_FASTFORWARD          0x1BEB
          KEY_FORWARD              0x1BE5
          KEY_REWIND               0x1BEA
          KEY_BACK                 0x1BDC
          KEY_INFO                 0x1BF0
          KEY_MENU                 0x1BF2
          KEY_LEFT                 0x1BDF
          KEY_RIGHT                0x1BDE
          KEY_UP                   0x1BE1
          KEY_DOWN                 0x1BE0
          KEY_OK                   0x1BDD
          KEY_VOLUMEDOWN           0x1BEE
          KEY_VOLUMEUP             0x1BEF
          KEY_MUTE                 0x1BF1
          KEY_SCROLLUP             0x1BED
          KEY_SCROLLDOWN           0x1BEC
          KEY_TV                   0x1BB7
          KEY_OPTION               0x1BD9
          KEY_TV2                  0x1BDA
          KEY_OPEN                 0x1BDB
          KEY_1                    0x1BFE
          KEY_2                    0x1BFD
          KEY_3                    0x1BFC
          KEY_4                    0x1BFB
          KEY_5                    0x1BFA
          KEY_6                    0x1BF9
          KEY_7                    0x1BF8
          KEY_8                    0x1BF7
          KEY_9                    0x1BF6
          KEY_NUMERIC_STAR         0x1BE2
          KEY_0                    0x1BFF
          KEY_NUMERIC_POUND        0x1BE3
          KEY_SUBTITLE             0x1BA5
          KEY_ENTER                0x1BF4
          KEY_RED                  0x1BA4
          KEY_GREEN                0x1BA3
          KEY_YELLOW               0x1BA2
          KEY_BLUE                 0x1BA1
      end codes

end remote
```

Start lircd (I think once lirc is installed it will be started at system startup by default):
```
sudo /etc/init.d/lirc start
```

Then I added my custom XBMC button mapping to *~/.xbmc/userdata/Lircmap.xml*:
```
<lircmap>
       <remote device="asusremote">
                <left>KEY_LEFT</left>
                <right>KEY_RIGHT</right>
                <up>KEY_UP</up>
                <down>KEY_DOWN</down>
                <select>KEY_OK</select>
                <start>KEY_MENU</start>
                <back>KEY_BACK</back>
                <record>KEY_RECORD</record>
                <play>KEY_PLAY</play>
                <pause>KEY_PAUSE</pause>
                <stop>KEY_STOP</stop>
                <forward>KEY_FASTFORWARD</forward>
                <reverse>KEY_REWIND</reverse>
                <volumeplus>KEY_VOLUMEUP</volumeplus>
                <volumeminus>KEY_VOLUMEDOWN</volumeminus>
                <channelplus>KEY_CHANNELUP</channelplus>
                <channelminus>KEY_CHANNELDOWN</channelminus>
                <title>KEY_INFO</title>
                <subtitle>KEY_SUBTITLE</subtitle>
                <mute>KEY_MUTE</mute>
                <power>KEY_POWER</power>
                <myvideo>KEY_TV2</myvideo>
                <mymusic>KEY_OPTION</mymusic>
                <mypictures>KEY_OPEN</mypictures>
                <mytv>KEY_TV</mytv>
                <one>KEY_1</one>
                <two>KEY_2</two>
                <three>KEY_3</three>
                <four>KEY_4</four>
                <five>KEY_5</five>
                <six>KEY_6</six>
                <seven>KEY_7</seven>
                <eight>KEY_8</eight>
                <nine>KEY_9</nine>
                <zero>KEY_0</zero>
                <red>KEY_RED</red>
                <green>KEY_GREEN</green>
                <yellow>KEY_YELLOW</yellow>
                <blue>KEY_BLUE</blue>
                <channelplus>KEY_SCROLLUP</channelplus>
                <channelminus>KEY_SCROLLDOWN</channelminus>                
                <star>KEY_NUMERIC_STAR</star>
                <hash>KEY_NUMERIC_POUND</hash>                
        </remote>
...
</lircmap>
```
(Make sure the remote device name above (asusremote) is the same as in lircd.conf.)

I wanted to be able to easily change the audio and subtitle delays so I had to customize even more (not required). I copied and edited remote.xml:
```
cp /usr/share/xbmc/system/keymaps/remote.xml .xbmc/userdata/keymaps/
vim .xbmc/userdata/keymaps/remote.xml

```
I changed the shutdown button to just exit from XBMC:
Changed:       
```
  <power>XBMC.ShutDown()</power>
```
To:            
```
  <power>XBMC.Quit()</power>
```

And under
```
<FullscreenVideo>
```
  I added:
```
  <channelplus>SubtitleDelayPlus</channelplus>
  <channelminus>SubtitleDelayMinus</channelminus>  
```              
  And changed:
```
  <star>NextSubtitle</star>
  <hash>AudioNextLanguage</hash>
```
  To:
```
  <star>AudioDelayPlus</star>
  <hash>AudioDelayMinus</hash>
```

Voila! Start XBMC and enjoy!

---

### Post by gdi2k on 2012-05-06
You're a magician! 

I don't have direct access to that machine any more, but will definitely give it a shot when I do...

---

