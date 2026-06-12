---
title: "Help with n-in-1 card reader"
date: 2011-06-28
forum: General Help
---

### Post by phillyj on 2011-06-28
Hi, I can't seem to get my card reader to work. The USB port on the reader works and sometimes I can read my SD card. Usually, nothing shows up in the media/ folder. I looked at this write-up ( [http://www.cs.sfu.ca/~ggbaker/personal/cf-linux]("http://www.cs.sfu.ca/%7Eggbaker/personal/cf-linux") ) but I'm not sure if this is what I should do.

Here are some info I was able to pull up:

[SIZE=3]**sg_scan -i**[/SIZE]
```

/dev/sg0: scsi0 channel=0 id=0 lun=0 [em]
    HL-DT-ST  DVD-RAM GH22NP20  2.00 [rmb=1 cmdq=0 pqual=0 pdev=0x5] 
/dev/sg1: scsi0 channel=0 id=1 lun=0 [em]
    ASUS      CD-S480/AH        0.89 [rmb=1 cmdq=0 pqual=0 pdev=0x5] 
/dev/sg2: scsi2 channel=0 id=0 lun=0 [em]
    ATA       ST3160023AS       3.20 [rmb=0 cmdq=0 pqual=0 pdev=0x0] 
sg_scan: device /dev/sg3 failed on scsi+ata ioctl, skip: Operation not permitted
/dev/sg4: scsi4 channel=0 id=0 lun=1 [em]
    Generic   USB CF Reader     1.01 [rmb=1 cmdq=0 pqual=0 pdev=0x0] 
/dev/sg5: scsi4 channel=0 id=0 lun=2 [em]
    Generic   USB SM Reader     1.02 [rmb=1 cmdq=0 pqual=0 pdev=0x0] 
/dev/sg6: scsi4 channel=0 id=0 lun=3 [em]
    Generic   USB MS Reader     1.03 [rmb=1 cmdq=0 pqual=0 pdev=0x0]

```[SIZE=3]**sg_map**[/SIZE]
```

/dev/sg0  /dev/scd0
/dev/sg1  /dev/scd1
/dev/sg2  /dev/sda
/dev/sg3
/dev/sg4  /dev/sdc
/dev/sg5  /dev/sdd
/dev/sg6  /dev/sde


```

The SD card slot doesn't seem to be working either. I restarted but it didn't help.
**I'm running WUBI Ubuntu 10.10**

---

### Post by seawolf167 on 2011-06-28
Do you have any drivers available under "Additional Drivers"

---

### Post by phillyj on 2011-06-28
> **seawolf167 said:**
> Do you have any drivers available under "Additional Drivers"


Umm, Could you tell me how to check that thru the command line? I lost the menu bars and have been using the terminal for the past few months. Haven't gotten around to reinstalling Ubuntu yet.

---

### Post by seawolf167 on 2011-06-28
Hit [ALT][F2], then type in "Additional Drivers", it should popup or autocomplete to the correct entry

---

### Post by phillyj on 2011-06-28
> **seawolf167 said:**
> Hit [ALT][F2], then type in "Additional Drivers", it should popup or autocomplete to the correct entry

By Alt-F2, I assume you mean the terminal. That won't work so I use Ctrl-Alt-T to start the Terminal. Anyway, the "Additional Drivers" command doesn't work. What are we trying to access anyway?

---

### Post by seawolf167 on 2011-06-28
[ALT][F2] is the default keyboard shortcut to open the Run dialog box.

i.e. [ALT][F2] then typing in Firefox would open Firefox, so typing "Additional Drivers" will open the drivers program where you could install any available hardware drivers for your devices to provide functionality

---

### Post by phillyj on 2011-06-28
> **seawolf167 said:**
> [ALT][F2] is the default keyboard shortcut to open the Run dialog box.

i.e. [ALT][F2] then typing in Firefox would open Firefox, so typing "Additional Drivers" will open the drivers program where you could install any available hardware drivers for your devices to provide functionality


Yeah, I think you misunderstand. Atl-F2 doesn't work for me. I don't get a run dialog box. If I want to run firefox, I open up the terminal and type firefox.

 I think the GNOME or KDE (I don't know what it is) is broken somehow. My Ubuntu is probably broken but I can't reinstall it yet.

Edit: Can I get the drivers thru Synaptic?

---

### Post by seawolf167 on 2011-06-28
I'm not aware of any way of getting the drivers through synaptic.

You may want to try fixing any broken packages you have

```
sudo apt-get install -f
```

or reinstalling ubuntu-desktop

```
sudo apt-get reinstall ubuntu-desktop
```

and see if that fixes your current desktop problem and possibly your card reader issue

---

