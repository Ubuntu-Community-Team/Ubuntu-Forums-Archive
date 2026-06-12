---
title: "irexec with .lircrc doesn't start apps"
date: 2010-10-27
forum: General Help
---

### Post by Netlat on 2010-10-27
Hello, 
I have issues with with my USB remote (ATI/NVidia/X10). irw shows correct codes while pressing buttons, but irexec doesn't execute commands from ~/.lircrc file.

I have defined simple .lircrc with following code:
```

begin
	prog   = irexec
	button = World
	config = echo "Hello world!!!"
end

```

 So, when i try to press "World" button expected behavior is "Hello world!!!". Visible behavior is: Nothing happens.

Lirc is up and running. "irexec -d ~/.lircec" execution is logged as below:
```

Oct 28 00:05:32 m-desktop lircd-0.8.6[4591]: caught signal
Oct 28 00:05:32 m-desktop lircd-0.8.6[4635]: lircd(atilibusb) ready, using /var/run/lirc/lircd
Oct 28 00:05:40 m-desktop lircd-0.8.6[4635]: accepted new client on /var/run/lirc/lircd

```

/etc/lirc/lirc.conf includes file /usr/share/lirc/remotes/atiusb/lircd.conf.atilibusb. Remote section is below:
```

begin remote
  name  Medion_MD8800
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap          139995
  min_repeat      2
  toggle_bit_mask 0x80800000

      begin codes
          Live_TV                  0xF11C
          Photo                    0x5A85
          DVD_Menu                 0xD904
          Rec_TV                   0x6D98
... (some other buttons)
          Next                     0x78A3
          Stop                     0xFD28
          Rec                      0x7CA7
      end codes
end remote

```

/etc/lirc/hardware.conf:
```

REMOTE="ATI/NVidia/X10 RF Remote (userspace)"
REMOTE_MODULES=""
REMOTE_DRIVER="atilibusb"
REMOTE_DEVICE="/dev/lircd"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="atiusb/lircd.conf.atilibusb"
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

```

System: "Ubuntu 10.04.1 LTS", Linux 2.6.32-25-generic SMP x86_64

---

### Post by ningdai on 2010-10-30
Same problem here.

---

### Post by Alessandro74 on 2010-11-23
I am also having this issue.
Remote is working in mythtv and in xbmc, but it won't start applications from the config file lircrc !
@NetLat - did you get anywhere close to working out what is going on?

I am having 99% the same issues as you. My remote is configured a standard MCSE usb remote - irexec is running at startup and all looks ok... I cannot for the life of me work out why it won't start apps.

I have this in my lircrc config:

begin
 *remote = mceusb
 *prog = irexec
 *button = Power
 *config = /usr/bin/xbmc
end

Irw, when running, shows the button press is appearing just fine, but it won't launch ANYTHING! :( :(

---

### Post by whocares02 on 2013-01-24
I have the same problem in Mythbuntu 12.0.4.1 and lirc 0.9.0.

---

