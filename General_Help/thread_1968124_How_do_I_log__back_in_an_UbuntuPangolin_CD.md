---
title: "How do I log  back in an Ubuntu/Pangolin CD ?"
date: 2012-04-28
forum: General Help
---

### Post by Hector23 on 2012-04-28
I must admit I never had a problem with this in all my Linux life, except with Mint -- that was a loong tiem a go! --, which I immediately gave up: I can't log back in the Pangolin CD. 

Blank, ubuntu, pangolin, user, nothing works. I can't reboot because I want to try Gnome-Shell without installing Pangolin, which, it seems, is not downgradable.

This is certainly the most basic question one can ask. People read my posts, I don't get an answer. What's going on?

---

### Post by cariboo on 2012-05-01
Normally the username is ubuntu, and no password is needed, if it doesn't work, I'd suggest you are suffering from a bad burn. 

From your other thread, I'm assuming you are trying to test gnome-shell from the Live CD. Why not just create a small partition about 5GiB in size and do an installation. You can use gparted which is included on t he Live CD to resize Ext4/Ext3 partitions. If you are running Windows, you can use the Windows disk management tool to resize a partition. If you don't like or can't use 12.04 due to hardware reasons, you can use the previously mentioned tools to remove the partition you installed on and regain your hard drive space.

---

### Post by pqwoerituytrueiwoq on 2012-05-01
workaround: after installing gnome shell
[FONT=Courier New]sudo service lightdm restart[/FONT]

---

