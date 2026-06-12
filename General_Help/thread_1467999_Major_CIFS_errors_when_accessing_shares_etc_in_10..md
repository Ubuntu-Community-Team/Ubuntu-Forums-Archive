---
title: "Major CIFS errors when accessing shares etc in 10.04"
date: 2010-05-01
forum: General Help
---

### Post by UrbanSlayer on 2010-05-01
Since upgrading to 10.04 I have had constant CIFS errors in /var/log/syslog

Eg - 
May  1 10:33:46 eclair kernel: [  933.789217]  CIFS VFS: No response for cmd 50 mid 32895
May  1 10:33:46 eclair kernel: [  933.794567]  CIFS VFS: No response for cmd 50 mid 32900
May  1 10:33:48 eclair kernel: [  935.721371]  CIFS VFS: No response to cmd 46 mid 37294
May  1 10:33:48 eclair kernel: [  935.721375]  CIFS VFS: Send error in read = -11
May  1 10:33:48 eclair kernel: [  935.728501]  CIFS VFS: No response to cmd 46 mid 37300
May  1 10:33:48 eclair kernel: [  935.728504]  CIFS VFS: Send error in read = -11
May  1 10:33:48 eclair kernel: [  936.207100]  CIFS VFS: No response for cmd 50 mid 936
May  1 10:33:48 eclair kernel: [  936.210498]  CIFS VFS: Received no data, expecting 1967
May  1 10:33:48 eclair kernel: [  936.210882]  CIFS VFS: No response to cmd 46 mid 37429
May  1 10:33:48 eclair kernel: [  936.210886]  CIFS VFS: Send error in read = -11
May  1 10:33:48 eclair kernel: [  936.214296]  CIFS VFS: No response for cmd 50 mid 946
May  1 10:33:49 eclair kernel: [  937.332619]  CIFS VFS: No response for cmd 50 mid 34680
May  1 10:33:49 eclair kernel: [  937.338233]  CIFS VFS: No response for cmd 50 mid 34687
May  1 10:33:49 eclair kernel: [  937.343464]  CIFS VFS: No response for cmd 50 mid 34692
May  1 10:33:49 eclair kernel: [  937.351129]  CIFS VFS: No response for cmd 50 mid 34703


All shares mount and I can open them etc, but always those errors appear whenever I try and browse to it, read them etc.  These shares are mount from a Windows 2003 Server and no other machine has a problem reading or writing to this machine.  I have changed the network cable and network cards in both machines, with no success.

If I copy a file from a local drive to a CIFS drive, the file on the CIFS drive becomes corrupted.  Can anyone help?  Google has failed me.  I have tried the CIFS option OplockEnabled, but that has not helped.

Thanks!

---

### Post by dino99 on 2010-05-01
is your problem the same: [http://ubuntuforums.org/showthread.php?t=1437447](http://ubuntuforums.org/showthread.php?t=1437447) ?

can we link that problem with a package name ?

is mountall installed ?

or try

sudo dpkg-reconfigure mountall
sudo dpkg --configure -a

note: found a french forum, do you understand french ?
[http://forum.ubuntu-fr.org/viewtopic.php?pid=3393315](http://forum.ubuntu-fr.org/viewtopic.php?pid=3393315)

---

### Post by UrbanSlayer on 2010-05-01
mountall is installed.

I dont think the 2 problems are related as my shares mount with everything in them, I can see the files and launch them, but when browsing the shares, reading files etc, those errors appear.

Also, for example, if it was a video file that was playing VLC, it would eventually crash as it could no longer read it, but it will happen randomly, the file may play for 1min the first time, 4min the second and 10secs the third.

---

### Post by ed64 on 2011-01-09
I experienced this in 10.10 recently.

Going to see if killing hald will help.

To reproduce, need to mount and not use the share for about 10m.

Hmm, nevermind, maverick doesn't have hald.

Anyone experience/fix this in 10.04 or 10.10?

---

### Post by lsutiger on 2011-06-22
I suddenly re-experienced this starting in March. Still looking for a fix.
I had the problem when I upgraded to 9.10. There was a fix and it worked for a while, then in late March it showed up again.

---

### Post by UrbanSlayer on 2011-11-02
Hmm..hadn't realised this was still getting attention.

I haven't managed to fix the problem as such, but found a work around.

Instead of mounting the shares from /etc/fstab, I have put them in a script that is launched from .bashrc in my profile on login. 
Since doing this, I have had 0 CIFS errors/problems with shares on both my Win 2k3 fileserver or new NAS.

---

