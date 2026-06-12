---
title: "trash crashes nautilus"
date: 2009-09-22
forum: General Help
---

### Post by tudor117 on 2009-09-22
When I open my trash, a window opens, closes and then all the icons on my desktop disappear. 
This happens to 2 of the 3 users on my system. Both of which have items in their trash and which have all the administrative privileges. The other user can open the trash fine, however they are just the default desktop user and have nothing in the trash.

In the terminal i get:
```
$ nautilus

** (nautilus:10796): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: unknown format for key 'dorina_mount/usershare_acl' as it contains 'Everyone:F,'.  Assuming that the share is read-only

(nautilus:10796): GLib-GIO-CRITICAL **: g_file_info_get_name: assertion `G_IS_FILE_INFO (info)' failed

** (nautilus:10796): WARNING **: Got GFileInfo with NULL name in trash:///, ignoring. This shouldn't happen unless the gvfs backend is broken.


(nautilus:10796): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

```The folder "dorina_mount" is in my home directory and is a windows share.

Any help is appreciated.

---

### Post by tudor117 on 2009-09-22
bump

---

### Post by tudor117 on 2009-09-22
bump

any ideas?
i dont mind losing whats in the trash
but i would like to empty it

---

### Post by ElTimo on 2009-09-23
I'm having the same problem. Running nautilus in a terminal yields the following:```
tim@Cygnus-X1:~$ nautilus trash:/

(nautilus:10732): GLib-GIO-CRITICAL **: g_file_info_get_name: assertion `G_IS_FILE_INFO (info)' failed

** (nautilus:10732): WARNING **: Got GFileInfo with NULL name in trash:///, ignoring. This shouldn't happen unless the gvfs backend is broken.


(nautilus:10732): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nautilus:10732): GLib-GIO-CRITICAL **: g_file_info_get_name: assertion `G_IS_FILE_INFO (info)' failed

** (nautilus:10732): WARNING **: Got GFileInfo with NULL name in trash:///, ignoring. This shouldn't happen unless the gvfs backend is broken.


(nautilus:10732): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

```
I've tried reinstalling gvfs and gvfs-backends, but nothing had any effect. First person to solve it gets a cookie :D

---

### Post by ElTimo on 2009-09-23
Figured out a workaround. If you really need to get at something in the trash, it's located in ~/.local/share/Trash/files. HTH

---

### Post by tudor117 on 2009-09-23
Thanks :)
I guess that's ok for now.
Hope karmic won't have this problem.

---

### Post by tudor117 on 2009-09-23
How very weird, I can delete all the files by right clicking on the trash icon an going "Empty Trash"
Than I can open the trash fine. But once there's a file in it, it undergoes the same problem as before.

---

### Post by dawian on 2009-10-11
got the same problem, started happening two days ago on jaunty. it happens when i click "computer" from the places menu, or, if i try to open trash with something in it (empty trash performs fine). desktop crashes - all icons disappear and if i have terminal opened, i get the same message as above. if i start nautilus from terminal, desktop items reappear, but as soon as i close nautilus or terminal window, they disappear again.

---

### Post by tudor117 on 2009-10-11
Just a quick update.
It crashes for me too when I open "Computer".
However a fix is to run:
```
daemon nautilus
```That way when you close the nautilus viewer, the icons will remain (until you decide to crash it again).

---

### Post by bizna on 2009-10-28
> **tudor117 said:**
> Just a quick update.
It crashes for me too when I open "Computer".
However a fix is to run:
```
daemon nautilus
```That way when you close the nautilus viewer, the icons will remain (until you decide to crash it again).

And if you want to have Nautilus re-open after the crash, just use the -r option:```
daemon nautilus
```

Dotan

---

### Post by matborda on 2009-11-14
It crashes when I open:

- Trash when it isn't empty

- Computer

- Network

Maybe it is interesting to note that after the crash I can manage to have again the icons on the Desktop by opening the Trash (empty) from the tray icon. But it doesn't happen the same if I open with nautilus other folders...

By the way...any fix?

Ciaooo

---

### Post by tudor117 on 2009-11-15
To fix it I did a clean install of Karmic.
It fixed this problem.

---

### Post by matborda on 2009-11-15
**tudor117**, what do you mean with a "clean install"?

As I heard that Karmic has in turn some problems with bugs,etc., I prefer to wait for an update...

---

### Post by tudor117 on 2009-11-15
I didn't do an upgrade I just reinstalled. I found the problem's gone in Karmic.

And, I suppose I was one of the lucky ones who didn't get any bugs/problems from the upgrade :)

---

### Post by rapsodia on 2010-02-03
I got  something similar about Nautilus-Share_Message maybe its a hint of the problem. 
mine crashes when I click on trash or network.

Initializing nautilus-dropbox 0.6.1
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (nautilus:4747): WARNING **: Unable to add monitor: Not supported

(nautilus:4747): GLib-GIO-CRITICAL **: g_file_info_get_name: assertion `G_IS_FILE_INFO (info)' failed

** (nautilus:4747): WARNING **: Got GFileInfo with NULL name in trash:///, ignoring. This shouldn't happen unless the gvfs backend is broken.


(nautilus:4747): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault


any ideas guys ?

edit: 
- BTW I should add this is happening in 9.04
- I got rid of the "Nautilus-Share-Message" by installing samba. somehow I think it got uninstalled I am pretty sure I installed anyways..
- and also as I said it would crash when clicking on trash and network what I did was to add trash icon to the the panel and then right click on it then press "empty trash" after that clicking on the trash does not crash nautilus. Clicking on the network still crashes it.

---

### Post by pushkarajthorat on 2010-04-05
I am also facing the same issue on ubuntu 9.04, when i see /var/log/messages I found this:

[FONT="Courier New"]Apr  6 09:36:36 laptop kernel: [  434.979036] nautilus[2511]: segfault at 656d614e ip b7875aa6 sp bfdd8020 error 4 in libglib-2.0.so.0.2200.4[b781f000+b4000]
Apr  6 09:38:29 laptop kernel: [  548.182467] nautilus[3077]: segfault at b793222c ip b78cd912 sp bfa7ea70 error 7 in libgobject-2.0.so.0.2200.4[b78b3000+3c000]
Apr  6 09:39:35 laptop kernel: [  614.652088] nautilus[3241]: segfault at 1 ip b7959aa6 sp bfabcb80 error 4 in libglib-2.0.so.0.2200.4[b7903000+b4000]
Apr  6 09:48:37 laptop kernel: [ 1155.875820] nautilus[3404]: segfault at 8 ip b79dd81d sp bff56580 error 4 in libpango-1.0.so.0.2400.1[b79c9000+40000]
Apr  6 09:49:42 laptop kernel: [ 1220.942932] nautilus[3722]: segfault at 3 ip b7941aa6 sp bf9a49f0 error 4 in libglib-2.0.so.0.2200.4[b78eb000+b4000]
Apr  6 10:00:29 laptop kernel: [ 1867.900978] nautilus[4039]: segfault at 676e6908 ip b777c312 sp bfefde74 error 6 in libglib-2.0.so.0.2200.4[b7746000+b4000][/FONT]

when I tried to run nautilus computer: or nautilus --no-desktop computer: and also I cannot open trash or network for nautilus, 'nautilus /' works fine.

---

### Post by RedSingularity on 2010-04-05
I have been having the same problem for a while now.  I researched it and it seems there is a bug report on it.

---

### Post by pushkarajthorat on 2010-04-05
> **RedSingularity said:**
> I have been having the same problem for a while now.  I researched it and it seems there is a bug report on it.

Can you please post the link of bug report here?

Google locates something when we search this, but that link goes to japnese page and i dont know japanese :).
[http://www.google.co.in/search?hl=en&q=nautilus+segfault+at++ip++sp++error+6+in+libglib-2.0.so.0.2200.4&btnG=Search&meta=&aq=f&aqi=&aql=&oq=&gs_rfai=](http://www.google.co.in/search?hl=en&q=nautilus+segfault+at++ip++sp++error+6+in+libglib-2.0.so.0.2200.4&btnG=Search&meta=&aq=f&aqi=&aql=&oq=&gs_rfai=)

---

### Post by pushkarajthorat on 2010-04-06
Link of the bug:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/515336](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/515336)

---

