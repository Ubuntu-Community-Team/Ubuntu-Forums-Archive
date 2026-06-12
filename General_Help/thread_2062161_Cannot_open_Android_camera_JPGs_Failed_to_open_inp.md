---
title: "Cannot open Android camera JPGs: Failed to open input stream"
date: 2012-09-24
forum: General Help
---

### Post by edm1 on 2012-09-24
If I connect my Galaxy Nexus to my laptop using the USB cable, I am unable to view pictures I took using the phone's camera. When I try to open one of the photos I get the error 'Failed to open input stream'. Any suggestions? Thanks.

---

### Post by dcstar on 2012-09-24
> **edm1 said:**
> If I connect my Galaxy Nexus to my laptop using the USB cable, I am unable to view pictures I took using the phone's camera. When I try to open one of the photos I get the error 'Failed to open input stream'. Any suggestions? Thanks.

Try copying them to your system and opening them there.

---

### Post by edm1 on 2012-09-24
I cant even copy them to the computer. I get the error 'Error getting file: -6: Not Supported'.

Strangely, there is a photo that I cropped on the phone and I can access/copy this cropped photo without problems.

---

### Post by zappadragon on 2012-11-08
I am having the same problem. Any other ideas?

---

### Post by Mark Phelps on 2012-11-09
The nexus uses ICS or JB -- and in both cases, Google removed the previous option of mounting the filesystem in Mass Storage mode.  So now, it's extremely difficult, if not impossible, to mount the filesystems for these phones without special drivers provided only for MS Windows.

---

### Post by 68pontiac on 2012-11-10
> **Mark Phelps said:**
> The nexus uses ICS or JB -- and in both cases, Google removed the previous option of mounting the filesystem in Mass Storage mode.  So now, it's extremely difficult, if not impossible, to mount the filesystems for these phones without special drivers provided only for MS Windows.

Not totally true. Instead of relying on USB Mass Storage Android is now using MTP (Media Transfer Protocol) to transfer media to other systems. (For those who care, it was a decision made during the Honeycomb release cycle to help with partitioning internal and external storage and which ones are seen by other systems.) When I need to push or pull media to my devices I use a native program, gMTP. I believe it's in the Ubuntu repositories.

Give it a shot, works like a charm for me!

---

