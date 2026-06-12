---
title: "Sound option disappeared"
date: 2010-06-06
forum: General Help
---

### Post by fjctp on 2010-06-06
My laptop(ubuntu 10.04) works great before ( with sounds )

but after reboot,it has absolutely no sound.
There is no sound icon on the top-right panel.

When I try System > Preference > Sound, it show " waiting for sound system to response".
then I try gnome-volume-control in terminal 
and I get the following :

** (gnome-volume-control:3536): WARNING **: Connection failed, reconnecting...

So what is going on?
Thanks

---

### Post by fjctp on 2010-06-09
My sound is back, but when I click System > Preference > sound , the problem is still there.
Please help.

---

### Post by Yellow Pasque on 2010-06-09
Too frequently, the user configuration files for pulseaudio get screwed up. Try removing them to generate new ones:
```
sudo pulseaudio --kill
cd ~
rm -rf .pulse*
```
Log out and log back in.

---

### Post by fjctp on 2010-06-10
I tried, but there are some errors.
>>E: core-util.c: Home directory /home/USERS not ours.
>>E: main.c: Failed to kill daemon: Permission denied

---

