---
title: "Unable to mount iPhone DBus error -- &quot;Mountpoint already registered&quot;"
date: 2011-04-25
forum: General Help
---

### Post by dpol on 2011-04-25
"Unable to mount iPhone 
DBus error 
org.freedesktop.DBus.Error.InvalidArgs: 
Mountpoint Already registered" 

The above error appears upon plugging in my iPhone 3GS using a USB
connection on Ubuntu 10.04. Attempting to transfer tracks to the iPhone
(using Rythmbox) results in this error:
:confused:
"Error Transferring Track
Error while getting peer-to-peer dbus connection:
The name :1.140 was not provided by any .service files"

The interesting part is that I can unmount the iPhone get back into
Nautilus and the iPhone icon will still be there on the left side pane.
Unmounting from Nautilus does not get rid of the iPhone icon until I
physically disconnect the USB cable from the iPhone. Clicking on the unmount/eject icon next to the iPhone icon in Nautilus removes the unmount/eject icon, but it does not remove the iPhone from the left side pane.  My other USB devices, such as the 2TB external iOmega hard drive, exhibit identical behavior. I'm guessing that this is a gvfs bug since it appears very similar to other gvfs bugs that I've found from a couple of years ago.  I am using gvfs 1.6.2-1ubuntu1~ppa1. 

My iPhone used to sync work perfectly using this same Ubuntu PC as late as November 2010. There were no changes made to the iPhone, only updates to Ubuntu -- I'd like to emphasize updates; no new software was installed on this Ubuntu PC. 

Can anyone suggest the best course of action that I could take to again be able to use my iPhone with Ubuntu?

---

### Post by burhangondal on 2011-04-30
+1.... exact same question from me....:(

---

### Post by thecrucialgary on 2011-05-02
[http://www.multimediaboom.com/iphone-not-recognized-after-upgrading-ios-4-2-in-ubuntu-heres-how-to-solve-the-problem/](http://www.multimediaboom.com/iphone-not-recognized-after-upgrading-ios-4-2-in-ubuntu-heres-how-to-solve-the-problem/)

---

### Post by Gary_inNYC on 2011-05-13
After installing packages from the ppa, my ipod touch 2g using iOS 4.2.x mounts and is usable BUT, it still brings up the same "mountpoint already registered" prompt.

---

### Post by kracheck on 2011-05-14
I can confirm the same issues with a new iPod Touch 4G (version4.1).

I also wonder if you also have music appearing in the Ubuntu media player, but that is not playable or does not appear on the iPhone/iPod ?

---

### Post by dpol on 2011-05-15
My iPhone worked perfectly a few months ago using the solution described at [http://www.multimediaboom.com/iphone...e-the-problem/](http://www.multimediaboom.com/iphone...e-the-problem/), but something must have changed since then -- I was only installing updates to 10.04 since then; no new software.

---

