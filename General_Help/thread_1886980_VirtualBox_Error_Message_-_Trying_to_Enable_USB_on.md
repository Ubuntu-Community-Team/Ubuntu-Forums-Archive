---
title: "VirtualBox Error Message - Trying to Enable USB on Ubuntu 11.10 x64"
date: 2011-11-26
forum: General Help
---

### Post by Kenjigraphics on 2011-11-26
I have a problem with enabling USB on my VirtualBox installation on Ubuntu 11.10 x64. 

[IMG]http://img844.imageshack.us/img844/7538/workspace1002h.png[/IMG]

The picture above basically shows the error being shown on the 'Terminal' after I click OK on the 'vboxusers' Properties. I tried it many times showing the same exact error. 

(users-admin:11567): Gtk-CRITICAL **: IA__gtk_list_store_set_valist: assertion `VALID_ITER (iter, list_store)' failed

Can somebody help me? I'm new to this thing and I already tried the method shown in this forum.
[http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml](http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml)

---

### Post by Sazhen86 on 2011-11-26
I'm not sure what the problem is with the users-admin command as I'm on 10.04 and it works OK for me.  However, the same effect can be achieved by editing the /etc/groups file and adding your user name to the end of the vboxusers line.  You'll need to use sudo to edit the file.

Also, if you're using the non-freeware version of VirtualBox, you might need to download and add the extension pack to get USB 2.0 support.

Hope that helps.

---

### Post by Kenjigraphics on 2011-11-26
> **Sazhen86 said:**
> I'm not sure what the problem is with the users-admin command as I'm on 10.04 and it works OK for me.  However, the same effect can be achieved by editing the /etc/groups file and adding your user name to the end of the vboxusers line.  You'll need to use sudo to edit the file.

Also, if you're using the non-freeware version of VirtualBox, you might need to download and add the extension pack to get USB 2.0 support.

Hope that helps.

Hi. Thanks for the response. I restarted my Ubuntu PC and well, USB works! I'm so happy. :D

---

### Post by Sazhen86 on 2011-11-26
Sweet!  Glad it's working.  Sometimes a reboot works wonders.

---

