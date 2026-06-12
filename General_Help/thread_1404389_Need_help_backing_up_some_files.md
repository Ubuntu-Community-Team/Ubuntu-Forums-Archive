---
title: "Need help backing up some files"
date: 2010-02-11
forum: General Help
---

### Post by demonic_crow on 2010-02-11
I'm trying to save some of my files from my crashed ubuntu drive but some are lock and say I don't have permission.  I'm using a LiveCd. Is there anyway for me to unlock it or use my username and password on that system to get it thanks.

---

### Post by jken146 on 2010-02-11
Run nautilus as root
```
gksudo nautilus
```

---

### Post by demonic_crow on 2010-02-12
Awesome thanks alot.  Now I can view the files but still won't let me copy it to another hard drive.  I still get the you don't have permission to read it.  I right click on the file and went to the permission to change it to read and write and also tried the create and delete files option and still does it.  Thanks alot for your help.  I'm just really trying to get this done quick so I can install a fresh copy of Ubuntu 9.10 :D

---

### Post by demonic_crow on 2010-02-12
I just looked in the terminal and it say this

ubuntu@ubuntu:~$ gksudo nautilus
(nautilus:3501): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:3501): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3501): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3501): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (process:3539): WARNING **: Couldn't change nice value of process.
totem-video-thumbnailer couldn't open file 'file:///media/e73708c6-a7bb-4c61-8af9-2320e6e327d3/home/demonic/hostel-part-ii-01.ogv'
Reason: Stream contains no data..
** Message: Error: Stream contains no data.
gsttypefindelement.c(863): gst_type_find_element_activate (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/GstTypeFindElement:typefind:
Can't typefind empty stream


** (process:3554): WARNING **: Couldn't change nice value of process.

(totem-video-thumbnailer:3554): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by demonic_crow on 2010-02-12
Ok I finally got everything copied.  I just right click on the file and went to sharing option.  I then choose Share this folder and then I checked: 
Allow others to creat and delete files in this folder
Guest access (for people without a user account)
When I clicked Create share it will run an install to let you do it.  I also had to go back and rigt click the folder and choose Properties, Permissions, then Apply Permissions to Enclosed Files.  I only had to do that on a few that didn't work with just the sharing.  Thought this might help anyone else that might need to do this.

---

