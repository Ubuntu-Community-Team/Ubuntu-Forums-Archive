---
title: "How to autostart samba daemon?"
date: 2009-08-09
forum: General Help
---

### Post by UranUtan on 2009-08-09
Hi,

Using Ubuntu 9.04 x64. I could install and configure samba following various tutorials found by internet seaches. However, each time I reboot the computer, the samba dsamon is stopped. I have to run manually the command below to get it working
> sudo /etc/init.d/samba restart

Is it samba standard design? How can I make samba start automatically at each reboot?

Thanks in advance for any help.

---

### Post by Monicker on 2009-08-09
A forum search should reveal a good number of posts regarding this.  Such as the following:  [http://ubuntuforums.org/showthread.php?t=151004](http://ubuntuforums.org/showthread.php?t=151004)

---

### Post by UranUtan on 2009-08-10
System > Administration > Services:

The Folder Sharing Service (samba) is checked. And yet I still need to start it manually.

---

### Post by warp99 on 2009-08-10
You can set the default runlevels to start the Samba script at boot with the following command:

```
sudo update-rc.d samba start 20 2 3 4 5 . stop 19 0 1 6 .
```

If for some reason Samba still does not want to start you can change the script boot order so Samba will start later:

First issue this command:

```
sudo update-rc.d -f samba remove
```

Then follow with the modified boot order runlevels:

```
sudo update-rc.d samba start 40 2 3 4 5 . stop 19 0 1 6 . 
```

You can change the boot order to a higher number if needed, all the way up to 99. Type "man update-rc.d" at the prompt for more information. Also look in the directory /etc/rc2.d for a better understanding of boot script ordering.

---

### Post by chmmr on 2009-12-26
> **UranUtan said:**
> System > Administration > Services:

The Folder Sharing Service (samba) is checked. And yet I still need to start it manually.

I'm running 9.10, and I don't see Services in the Administration menu anymore... where did it go?

---

### Post by chmmr on 2009-12-27
I was able to use the cmdline + init scripts steps described above to get samba auto-starting, but I'm still curious as to if it's just my system or if the "Services" view disappeared in Karmic / GNOME 2.28.  I know I remember seeing and using it in previous versions.

---

### Post by UranUtan on 2010-01-28
Still using Ubuntu 9.04 x64. Some how the instructions in post #4 don't work for me. I have tried a few combinations. The last one was 
```

sudo update-rc.d -f samba remove
sudo update-rc.d samba start 60 2 3 4 5 . stop 40 0 1 6
```

After log in If I type
```
smbclient -L MyComputerName.local -U%
```

I always get an error [COLOR="Red"]Connection to MyComputerName.local failed (Error NT_STATUS_CONNECTION_REFUSED)[/COLOR]

The only solution is to type manually **sudo /etc/init.d/samba restart** after I log in. Could that be because there is something wrong in smb.conf?

---

