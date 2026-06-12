---
title: "Plymouth splash issue 11.04 &quot;SP5100 TCO timer: mmio address 0xyyyyyyy already in use&quot;"
date: 2011-07-26
forum: General Help
---

### Post by amadis2009 on 2011-07-26
Been having a problem with my plymouth splash ever since I udgraded to Natty.I had some major resolution issues at first, which I seem to have fixed. But now my plymouth screen flashes for just a second or two and then I get another splash screen (in the wrong resolution, by the way), with just the Ubuntu text in white on a purple background and then some boot message text.

“SP5100 TCO timer: mmio address 0xyyyyyyy already in use”

There's more text after that but the screen disappears before I can read it all. The only time I can really see my plymouth boot screen is during shutdown. Anyone have any idea how to fix this?

---

### Post by amadis2009 on 2011-07-27
Looks like this is a compatibility issue between the drivers for my ATI video card and plymouth. (See the first post in this thread. [http://http://ubuntuforums.org/showthread.php?t=1436634]("http://http://ubuntuforums.org/showthread.php?t=1436634")) My only option at this time would be to switch to the slower open-source driver and disable compiz and emerald in order to avoid more graphics compatibility problems. For the time being I'm going to stick with the ugly boot screen and consider getting a different video card while hoping a fix to this problem happens before I have to make that choice.

---

### Post by tonywhelan on 2011-07-31
> **amadis2009 said:**
> Looks like this is a compatibility issue between the drivers for my ATI video card and plymouth.  ......For the time being I'm going to stick with the ugly boot screen and consider getting a different video card while hoping a fix to this problem happens before I have to make that choice.

There is a list of reports about this on launchpad - see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/740011]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/740011")

Looks like they fixed it in one of the updates but its back again. I'm just living with it for now, as I spent enough $$ on my video card and I'm not about to buy another :)

---

### Post by maddogg360 on 2011-08-26
I noticed that if I did a memtest86+ test everything is back to normal after a reboot

---

### Post by novikov on 2012-01-23
temporal way to use the system:
  
  during boot select "repair"
  select "normal boot"
  you'll be put into the command line (tty1). Enter your pass
  type "sudo service gdm start"
  done, you can now work as usual.
  
  Later today I'll try the last method mentioned here.
  > > I noticed that if I did a memtest86+ test everything is back to normal after a reboot

---

### Post by msnathan on 2012-01-30
Hi All,

Got it Fixed... Its working for me with out any issue.

Steps:

1. **echo 'blacklist shpchp' >> /etc/modprobe.d/blacklist-ath_pci.conf**

2. **echo 'blacklist sp5100_tco' >> /etc/modprobe.d/blacklist-watchdog.conf**

Reboot and check.

:) 

Thanks,
Swaminathan M

---

### Post by luissil on 2012-06-18
> **novikov said:**
> temporal way to use the system:
  
  during boot select "repair"
  select "normal boot"
  you'll be put into the command line (tty1). Enter your pass
  type "sudo service gdm start"
  done, you can now work as usual.
  
  Later today I'll try the last method mentioned here.
  > > I noticed that if I did a memtest86+ test everything is back to normal after a reboot

sorry, were do I can select "repair"??? my system doesn't boot at all... I only can see the grub, then select any option, and the "...sp5100 tco timer... mmio alredy..." error appears, after that, nothig happens...

> **msnathan said:**
> Hi All,

Got it Fixed... Its working for me with out any issue.

Steps:

1. **echo 'blacklist shpchp' >> /etc/modprobe.d/blacklist-ath_pci.conf**

2. **echo 'blacklist sp5100_tco' >> /etc/modprobe.d/blacklist-watchdog.conf**

Reboot and check.

:) 

Thanks,
Swaminathan M

What can I do if my system doesn't boot at all?

---

### Post by Redblade20XX on 2012-06-18
> **luissil said:**
> sorry, were do I can select "repair"??? my system doesn't boot at all... I only can see the grub, then select any option, and the "...sp5100 tco timer... mmio alredy..." error appears, after that, nothig happens...



What can I do if my system doesn't boot at all?

Try using a live cd and going into a live session. Mount your computer hdd and edit those files.

Also try and blacklist this module,
```
SP5100_tco
```

---

### Post by Doume on 2012-06-18
> **msnathan said:**
> Hi All,

Got it Fixed... Its working for me with out any issue.

Steps:

1. **echo 'blacklist shpchp' >> /etc/modprobe.d/blacklist-ath_pci.conf**

2. **echo 'blacklist sp5100_tco' >> /etc/modprobe.d/blacklist-watchdog.conf**

Reboot and check.

:) 

Thanks,
Swaminathan M

Thanks a lot for this tip : That fixes my boot problem :popcorn:
This message start to be displayed after an upgrade of Ubuntu 12.04 64 bits

---

### Post by luissil on 2012-06-23
> **Redblade20XX said:**
> Try using a live cd and going into a live session. Mount your computer hdd and edit those files.

Also try and blacklist this module,
```
SP5100_tco
```

Thank you, i really don't now how, but my pc starts normally, but, i tried the solution and, "permission denied"??:

```
luis@luis-casa:~$ sudo echo 'blacklist shpchp' >> /etc/modprobe.d/blacklist-ath_pci.conf
bash: /etc/modprobe.d/blacklist-ath_pci.conf: Permission denied
luis@luis-casa:~$ echo 'blacklist sp5100_tco' >> /etc/modprobe.d/blacklist-watchdog.conf
bash: /etc/modprobe.d/blacklist-watchdog.conf: Permission denied
luis@luis-casa:~$ sudo echo 'blacklist sp5100_tco' >> /etc/modprobe.d/blacklist-watchdog.conf
bash: /etc/modprobe.d/blacklist-watchdog.conf: Permission denied

```

---

### Post by Redblade20XX on 2012-06-23
> **luissil said:**
> Thank you, i really don't now how, but my pc starts normally, but, i tried the solution and, "permission denied"??:

```
luis@luis-casa:~$ sudo echo 'blacklist shpchp' >> /etc/modprobe.d/blacklist-ath_pci.conf
bash: /etc/modprobe.d/blacklist-ath_pci.conf: Permission denied
luis@luis-casa:~$ echo 'blacklist sp5100_tco' >> /etc/modprobe.d/blacklist-watchdog.conf
bash: /etc/modprobe.d/blacklist-watchdog.conf: Permission denied
luis@luis-casa:~$ sudo echo 'blacklist sp5100_tco' >> /etc/modprobe.d/blacklist-watchdog.conf
bash: /etc/modprobe.d/blacklist-watchdog.conf: Permission denied

```

Did you check to see if those files exist?

-Red

---

### Post by luissil on 2012-06-23
> **Redblade20XX said:**
> Did you check to see if those files exist?

-Red

mmm :confused:

```
luis@luis-casa:/etc/modprobe.d$ ls
alsa-base.conf             blacklist-framebuffer.conf   dkms.conf
blacklist-ath_pci.conf     blacklist-modem.conf         fglrx.conf
blacklist.conf             blacklist-oss.conf           oss-compat.conf
blacklist.conf~            blacklist-rare-network.conf  vmwgfx-fbdev.conf
blacklist-cups-usblp.conf  blacklist-rt2800pci.conf
blacklist-firewire.conf    blacklist-watchdog.conf

```

---

### Post by Redblade20XX on 2012-06-23
> **luissil said:**
> mmm :confused:

```
luis@luis-casa:/etc/modprobe.d$ ls
alsa-base.conf             blacklist-framebuffer.conf   dkms.conf
blacklist-ath_pci.conf     blacklist-modem.conf         fglrx.conf
blacklist.conf             blacklist-oss.conf           oss-compat.conf
blacklist.conf~            blacklist-rare-network.conf  vmwgfx-fbdev.conf
blacklist-cups-usblp.conf  blacklist-rt2800pci.conf
blacklist-firewire.conf    blacklist-watchdog.conf

```

My fresh install doesn't have those files so please forgive me for that post. Also did you create those conf files?

Anyways try and use a text editor instead of echoing it directly into the file.

```
sudo nano <config_file_name>
```
or 
```
sudo gedit <conf_file_name>
```

-Red

---

### Post by luissil on 2012-07-04
> **Redblade20XX said:**
> My fresh install doesn't have those files so please forgive me for that post. Also did you create those conf files?

Anyways try and use a text editor instead of echoing it directly into the file.

```
sudo nano <config_file_name>
```or 
```
sudo gedit <conf_file_name>
```-Red

Sorry, i'm not an expert, once the file is open in gedit what should I do?

Thank you for your help...

---

### Post by oldbearbone on 2012-08-30
After I executed "sudo bash", both of the echo orders worked fine.

---

### Post by Doume on 2012-10-06
> **luissil said:**
> Thank you, i really don't now how, but my pc starts normally, but, i tried the solution and, "permission denied"??:



You've to be root to write into those files

---

