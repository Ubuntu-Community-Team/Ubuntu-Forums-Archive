---
title: "Graphics"
date: 2006-03-24
forum: General Help
---

### Post by sprinkles on 2006-03-24
Hello again.
I've managed to abstain from Windows for almost two weeks now.
Tonight I tried to play a DVD. In Totem the frame rate was very bad, even when the window was very small, and in Mplayer, the framerate was a bit better, but still unwatchable. In Windows this system plays DVDs with absolutely no trouble.
It's an AMD Athlon XP 1800+ with an S3 ProSavage 64MB graphics card, and 384MB of RAM (Naughty I know.)

I also notice that the OpenGL screensavers run at a very slow framerate as well. Is there any reason why Ubuntu wouldn't be fully using my graphics card? I know it's no longer top-end, but it works OK in Windows.

Thanks,
Richard John

---

### Post by noob_Lance on 2006-03-24
you can try to turn DMA on. its in in the ubuntu wiki somewhere.. if i remember right.. its something like

/dev/hdparam {
    dma=1
}

dont use thatbecause i KNO im wrong... but its along those likes. I had the same problem until i did that.. now everything is perfectly fine :D

---

### Post by sprinkles on 2006-03-24
It's already on :(

---

### Post by dickm35 on 2006-03-24
[QUOTE=sprinkles]It's already on :([/QUOTE]
You can use hdparm utility with ANY version of Linux. It comes with all of them.
Open a terminal and type the following.
hdparm -c3d1k1 with just about all the hardrives made since 1998..
Your complete system will really kick butt then.

---

### Post by sprinkles on 2006-03-24
Hi,
Thanks for that, but I can't seem to get it to work - sorry if I'm being stupid, I'm a complete newb!

[QUOTE=Terminal]richard@Llama:~$ hdparm -c3d1k1

hdparm - get/set hard disk parameters - version v6.1

Usage:  hdparm  [options] [device] ..

Options:
 -a   get/set fs readahead
 -A   set drive read-lookahead flag (0/1)
 -b   get/set bus state (0 == off, 1 == on, 2 == tristate)
 -B   set Advanced Power Management setting (1-255)
 -c   get/set IDE 32-bit IO setting
 -C   check IDE power mode status
 -d   get/set using_dma flag
 --direct  use O_DIRECT to bypass page cache for timings
 -D   enable/disable drive defect management
 -E   set cd-rom drive speed
 -f   flush buffer cache for device on exit
 -g   display drive geometry
 -h   display terse usage information
 -i   display drive identification
 -I   detailed/current information directly from drive
 --Istdin  reads identify data from stdin as ASCII hex
 --Istdout writes identify data to stdout as ASCII hex
 -k   get/set keep_settings_over_reset flag (0/1)
 -K   set drive keep_features_over_reset flag (0/1)
 -L   set drive doorlock (0/1) (removable harddisks only)
 -M   get/set acoustic management (0-254, 128: quiet, 254: fast) (EXPERIMENTAL)
 -m   get/set multiple sector count
 -n   get/set ignore-write-errors flag (0/1)
 -p   set PIO mode on IDE interface chipset (0,1,2,3,4,...)
 -P   set drive prefetch count
 -q   change next setting quietly
 -Q   get/set DMA tagged-queuing depth (if supported)
 -r   get/set device  readonly flag (DANGEROUS to set)
 -R   register an IDE interface (DANGEROUS)
 -S   set standby (spindown) timeout
 -t   perform device read timings
 -T   perform cache read timings
 -u   get/set unmaskirq flag (0/1)
 -U   un-register an IDE interface (DANGEROUS)
 -v   defaults; same as -mcudkrag for IDE drives
 -V   display program version and exit immediately
 -w   perform device reset (DANGEROUS)
 -W   set drive write-caching flag (0/1) (DANGEROUS)
 -x   tristate device for hotswap (0/1) (DANGEROUS)
 -X   set IDE xfer mode (DANGEROUS)
 -y   put IDE drive in standby mode
 -Y   put IDE drive to sleep
 -Z   disable Seagate auto-powersaving mode
 -z   re-read partition table

ATA Security Options:
 --security-freeze              Freeze security settings (until next reset)
 --security-unlock PWD          Unlock drive, using password PWD (DANGEROUS)
 --security-set-pass PWD        Lock drive, using password PWD (DANGEROUS)
 --security-disable PWD         Disable drive locking, using password PWD (DANGEROUS)
 --security-mode MODE           Specify user/master password and high/maximum security
        u       user password, high security
        U       user password, maximum security
        m       master password, high security
        M       master password, maximum security
[/QUOTE]

---

### Post by jay310 on 2006-03-24
you need give it the device like /dev/hda

---

### Post by akiro.yamamoto on 2006-03-25
Specify something like this:
```
hdparm -d1 /dev/hdc
```
/dev/hdc is MY DVD drive so YMMV ;)

---

