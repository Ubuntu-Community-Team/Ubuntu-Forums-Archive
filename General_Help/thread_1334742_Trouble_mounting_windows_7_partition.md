---
title: "Trouble mounting windows 7 partition"
date: 2009-11-22
forum: General Help
---

### Post by gspat on 2009-11-22
I Just bought a new comp about a month ago and it had a free upgrade for win7 so I jumped on it.

I upgraded vista to win 7 and installed 9.10 on it so I could dual boot.

My main problem is that I can't mount the windows 7 partition at all... I get the following error:

Unable to mount
Authentication is required

Now, I cant figure this out... the live CD didn't need this authentication to mount it when I tried.

I'm not even sure it can be authenticated!(?)

what do I try next?

---

### Post by whitethorn on 2009-11-22
I usually start nautilus then click on my drive with windows 7 on it.  It then asks for authentification I then input my password and it'll mount the drive.  Or if you want to mount it by hand then use sudo before the mount command.

---

### Post by Mze on 2009-11-22
[Check this out.]("http://www.mydigitallife.info/2009/01/09/how-to-avoid-200mb-hidden-system-partition-from-been-created-during-windows-7-installation/")

What's documented there may explain the cause of your problems.

---

### Post by gspat on 2009-11-22
@whitethorn:

That was the first thing I tried, and got the error with.

I can't even get at it with gparted, the only option it really gives me is to reformat it and can't tell how much of the partition is in use. It does recognise it as a NTFS partition though.

@Mze:

The article is interesting, but I have the recovery folder (I did an "in place" upgrade over vista). 

When I was installing 9.10, it did warn me about corruption, but on the partition I was installing 9.10 to.

.:Update

I tried using pysdm to mount the partition (hopefully with authentication) but it does not even see it!?

---

### Post by wilee-nilee on 2009-11-22
> **gspat said:**
> @whitethorn:

That was the first thing I tried, and got the error with.

I can't even get at it with gparted, the only option it really gives me is to reformat it and can't tell how much of the partition is in use. It does recognize it as a NTFS partition though.

@Mze:

The article is interesting, but I have the recovery folder (I did an "in place" upgrade over vista). 

When I was installing 9.10, it did warn me about corruption, but on the partition I was installing 9.10 to.

.:Update

I tried using pysdm to mount the partition (hopefully with authentication) but it does not even see it!?

Did you pre-format the partition for Ubuntu?, if so this is probably the problem. On my computer I left the partition unformatted, this leaves a unallocated space betwen W7 and Karmic about 5Mib, here is a screen shot.
[ATTACH]137257[/ATTACH]

---

### Post by oldfred on 2009-11-23
Win7 has the same issue as Vista. Partitions do not start @ 63.

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

---

### Post by gspat on 2009-11-23
After taking a fresh look at it after work, and searching through these forums (again) I found  out about ntfs-config... It worked like a charm!

Thank you to you guys for the input!

---

