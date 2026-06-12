---
title: "Locked folder"
date: 2010-02-03
forum: General Help
---

### Post by tsm124 on 2010-02-03
I recently copied files from my mac partition to an extra hard drive then deleted the original mac partition. The folders are showing up as locked and i can not access them is their away to get around this, so that i can get to my files and open them up.


[SOLVED]
solution: Copy files over to other drive after using the terminal command stated below.Then copy the files to your main drive and your good to go.

Thanks guys!

---

### Post by mgichoga on 2010-02-03
Just a wild guess but they probably carried uid from the previous file system. You could check the folder permissions to see if you have read+write privileges. Right click the folder > Properties > permissions.

---

### Post by tsm124 on 2010-02-03
it says 501-user#501 

folder access: create and delete files


group: dialout

folder access: none

you are not the owner you cannot change these permissions.

---

### Post by bumanie on 2010-02-03
Type > gksudo nautilus in terminal and then you should be able to navigate to and access the files. Be careful as you are in the super user graphical mode with that command, so anything you do, will be pretty much permanent.

---

### Post by tsm124 on 2010-02-03
now i can open the files with this but i cannot edit them.
Thanks so much for at least being able to open the files!

---

### Post by tsm124 on 2010-02-03
these are the errors i get in terminal when i try to open the file or copy it 
** (nautilus:2899): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2899): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2899): WARNING **: No marshaller for signature of signal 'ShareCreateError'

** (process:3104): WARNING **: Couldn't change nice value of process.

** (process:3121): WARNING **: Couldn't change nice value of process.

** (process:3161): WARNING **: Couldn't change nice value of process.

** (totem-video-thumbnailer:3161): WARNING **: Could not take screenshot: no last video frame

** (totem-video-thumbnailer:3161): WARNING **: Could not take screenshot: no last video frame

** (process:3270): WARNING **: Couldn't change nice value of process.

** (process:3287): WARNING **: Couldn't change nice value of process.

** (nautilus:2899): WARNING **: Hit unhandled case g-io-error-quark:21 in fm_report_error_setting_group

** (process:4222): WARNING **: Couldn't change nice value of process.

(nautilus:2899): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.config/user-dirs.dirs


** (totem:4248): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name

** (process:5484): WARNING **: Couldn't change nice value of process.

---

### Post by tsm124 on 2010-02-03
Is there a way to reset a files permissions?

---

### Post by tsm124 on 2010-02-03
Have an idea, the terminal command lets me copy files to other hard disks, so ill copy it to my ipod then open up the files on my macbook pro and last but not least  unlock them.

HOPE THIS WORKS!!!!

---

### Post by bumanie on 2010-02-03
What version of ubuntu are you using? Is it up to date with the latest packages etc? I have quickly read some stuff from others who had this problem in the past, one found updating everything cured the issue, others didn't. In terminal try > sudo apt-get update && sudo apt-get upgradeType y and hit enter if there are packages to install. This will at least ensure you have the latest packages installed, then try accessing/copying the files again.Can't promise that this will help, but ensuring the system is up to date, won't hurt.

---

### Post by tsm124 on 2010-02-03
Yep system is up to date.
Thanks for the help though, right now im hoping for this ipod trick to work.

---

### Post by bumanie on 2010-02-03
Yeah, it is not a bad idea to copy the files to another device and try any operations from there, so that if anything goes wrong, you still have the original files in tact that can be copied again.

---

### Post by tsm124 on 2010-02-03
Nice i was able to copy it to a different drive and from there just copy it to my ubuntu drive thanks guys that terminal command helped A LOT like big time.

---

### Post by scouser73 on 2010-02-03
**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

---

