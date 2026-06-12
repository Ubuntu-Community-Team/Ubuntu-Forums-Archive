---
title: "no longer able to use &quot;sudo&quot; command"
date: 2012-09-26
forum: General Help
---

### Post by jktjs on 2012-09-26
Whilst attempting to install some tricky software (for astronomical data reduction) I hit software installation problems running as sudo. I therefore tried the same thing running as my normal user, after modifying the permissions of /usr:

chmod -R 777 /usr

This was intended to be a temporary mod and seems to have been a bad idea. I now cannot log in or run commands as superuser:

>> sudo su

or 

>> sudo chmod -R 755 /usr

gives the error message

"sudo: must be setuid root"

Various other things are wrong (e.g. my battery and networking is no longer detected according to KDE). 

Is there anything I can do to fix this, or have I misguidedly put myself on the path to a full reinstallation?

Thanks for any help!

---

### Post by Lars Noodén on 2012-09-26
I think that a re-installation might be in order.

---

### Post by nothingspecial on 2012-09-26
> **lars noodén said:**
> i think that a re-installation might be in order.

+1

---

### Post by HiImTye on 2012-09-26
you could load a liveUSB and manually set permissions for all files/folders in /usr/ but I would advise (which I rarely do) to just reinstall.

---

### Post by shaktiman1234 on 2012-09-26
What i get from your problem is that you gave 777 permission to /var folder in your root directory.
A clean install is recommended and next time take precaution before you use chmod, chgrp, chown commands.

---

### Post by HiImTye on 2012-09-26
> **shaktiman1234 said:**
> next time take precaution before you use chmod, chgrp, chown commands.
it's generally a bad idea to chown, chmod or chgrp anything outside of /home/ unless it's a removable drive or a mount point that you set (or you know for sure what you are doing)

---

### Post by prshah on 2012-09-26
> **jktjs said:**
> gives the error message
"sudo: must be setuid root"


You can boot into recovery, and change permissions on /usr/bin/sudo to 4755 (setuid root and executable). Note that in the recovery mode's (root) terminal option, you do not need to use sudo. For good measure, change kdesudo permissions as well.

Your sudo should then look like:```
Wed Sep 26 @16:12:31:~$ ll /usr/bin/sudo
-rwsr-xr-x 2 root root 71288 Jun  1 09:23 /usr/bin/sudo

```

I THINK (absolutely not sure) that re-installing the problematic packages should fix permissions. Eg, if sound is giving a problem, consider reinstalling it as ```
sudo apt-get install --reinstall phonon
```

If you have the time, and would like to experiment before re-installing, try installing the kde-desktop meta package```
sudo apt-get install --reinstall kubuntu-desktop
```

Hopefully, you won't have to download anything at all, unless you have run a recent apt-cache clean (purge old apt .deb files from cache).

AT YOUR OWN RISK only, sorry about that.

---

### Post by prshah on 2012-09-26
OK, just ran a small test, and the "--reinstall" seems to work.```
Wed Sep 26 @16:22:35:~$ [color=red]ll `which dvdisaster `[/color]
-rwxr-xr-x 1 root root 577176 Oct 16  2010 /usr/bin/dvdisaster
Wed Sep 26 @16:22:41:~$ [color=red]sudo chmod 500 /usr/bin/dvdisaster [/color]
Wed Sep 26 @16:23:11:~$ [color=red]ll /usr/bin/dvdisaster [/color]
-r-x------ 1 root root 577176 Oct 16  2010 /usr/bin/dvdisaster
Wed Sep 26 @16:23:21:~$ [color=red]sudo apt-get install --reinstall dvdisaster[/color]
..
After this operation, 0 B of additional disk space will be used.
..
Preparing to replace dvdisaster 0.72.1-2 (using .../dvdisaster_0.72.1-2_amd64.deb) ...
...
Setting up dvdisaster (0.72.1-2) ...
Wed Sep 26 @16:23:44:~$ [color=red]ll /usr/bin/dvdisaster [/color]
-rwxr-xr-x 1 root root 5

```

So, it may be worth a try. However, at your own risk only, please.

Good luck.

---

### Post by jktjs on 2012-09-26
Thanks all for the suggestions.

I tried failsafe but it still required the sudo command.

I then booted from USB, mounted /dev/sda1 and set the permissions on /usr to 755. This is clearly far too simple a fix (as suspected) and failed. 

Looks like that reinstall is heading my way!

---

