---
title: "Cannot change login screen background in 11.10"
date: 2012-01-18
forum: General Help
---

### Post by Anthony A on 2012-01-18
For some reason my login screen background will not change. I tried with Ubuntu Tweak and Simple Lightdm Manager. I set the background with these programs and when I log out the background remains the default one. Any suggestions?

---

### Post by heshoots67 on 2012-01-18
[http://www.addictivetips.com/ubuntu-linux-tips/change-ubuntu-11-10-logon-screen-background-with-lightdm-manager/](http://www.addictivetips.com/ubuntu-linux-tips/change-ubuntu-11-10-logon-screen-background-with-lightdm-manager/)

Hope this works out for you.

---

### Post by sarin_cv on 2012-01-18
Is your wallpaper located in an unmounted partition??

---

### Post by Anthony A on 2012-01-19
> **heshoots67 said:**
> [http://www.addictivetips.com/ubuntu-linux-tips/change-ubuntu-11-10-logon-screen-background-with-lightdm-manager/](http://www.addictivetips.com/ubuntu-linux-tips/change-ubuntu-11-10-logon-screen-background-with-lightdm-manager/)

Hope this works out for you.

As I said in my first post, I tried that program and it didn't work.

---

### Post by Anthony A on 2012-01-19
> **sarin_cv said:**
> Is your wallpaper located in an unmounted partition??


It's located on the partition I'm booted from.

---

### Post by Xgen on 2012-01-19
What does 'gksu gedit /etc/lightdm/unity-greeter.conf' indicate as your background? I usually change it there.

---

### Post by Anthony A on 2012-01-19
> **Xgen said:**
> What does 'gksu gedit /etc/lightdm/unity-greeter.conf' indicate as your background? I usually change it there.

It indicates the background I selected with Ubuntu Tweak and Lightdm Manager but thats not the background that shows up when I log out or in. The default background still shows.

---

### Post by Toz on 2012-01-19
Anything relevant in the log file (/var/log/lightdm/x-0-greeter.log)? 

Is the image accessible (e.g. not in encrypted home directory, viewable by all)?

---

### Post by Anthony A on 2012-01-19
I managed to change the background with Simple Lightdm  Manager finally. I had been in Gnome Shell when I was trying unsuccessfully. I tried logging into Unity and then setting the background with Simple Lightdm Manager and it worked. Don't know why it wouldn't work in Gnome Shell.

---

### Post by Anthony A on 2012-01-19
> **Toz said:**
> Anything relevant in the log file (/var/log/lightdm/x-0-greeter.log)? 

Is the image accessible (e.g. not in encrypted home directory, viewable by all)?

Yes the image is accessible.  The log is rather lengthy.

---

