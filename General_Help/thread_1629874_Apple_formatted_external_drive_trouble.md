---
title: "Apple formatted external drive trouble"
date: 2010-11-24
forum: General Help
---

### Post by CorrosiveMonkey on 2010-11-24
Hi,

My friend had a mac and has an external harddrive formatted to Apples file system.  And some folders on it couldn't be read by anything but her mac.  The mac unfortunately fell out of a window.  So I tried to have a go at getting the files off of the external harddrive on my Ubuntu system.

At first the external harddrive showed up in the sidebar of Nautilus, and its called Vicky

I ran chmod 004 /media/Vicky

and it was still viewable in the sidebar but non of the folders or files on the harddrive were showing up.  I could run ls /media/Vicky and the files and folders were listed.  But I could not cd /media/Vicky

Than I ran chmod a+r /media/Vicky and it disappeared from the sidebar.  But like before I could run ls on it fine.  cd still doesn't work.  But I can go filesystem -> media -> Vicky through nautilus ok, but still no files or folders

Does anyone know how I can get it so that files and folders appear again and make it show up in the sidebar.  And fix the permissions problem.

Thanks
James

---

### Post by nothingspecial on 2010-11-24
I have never even seen a mac.

However, I do know that you have to disable journaling on an hfs+ file system to get it to mount rw in linux.

How you do that without a mac, I don`t know

---

