---
title: "SFTP not working anymore. Please help!"
date: 2009-08-03
forum: General Help
---

### Post by joech on 2009-08-03
Hi,

I followed the directions in the tutorial elsewhere on this forum ([http://ubuntuforums.org/showthread.php?t=128206](http://ubuntuforums.org/showthread.php?t=128206)) and  was able to set up sftp in a chrooted jail on intrepid and everything was working fine until after (I think) I upgraded to jaunty. Now, when I use WinSCP to access the system, I get the following error:

"Connection has been unexpectedly closed. Server sent command exit status 1.
Cannot initialize SFTP protocol. Is the host running a SFTP server?"

Any help with getting this working again is much appreciated.

Thanks
Joe

---

### Post by joech on 2009-08-03
Never mind! I was able to get it working again. It seems the upgrade process reset the setuid root step. I reran the following step from the tutorial and everything is back to the way it was before! Joy! Hopefully this will help someone else with the same issue.



[COLOR=Blue]In order for the chrooting process to work, "/usr/lib/rssh/rssh_chroot_helper" has to be setuid root. (Note: this path is relative to real root, not chroot root.) To setuid root, run the command:
[/COLOR]  	[COLOR=Blue]Code:[/COLOR]
 	[COLOR=Blue]sudo chmod u+s /usr/lib/rssh/rssh_chroot_helper[/COLOR]

---

