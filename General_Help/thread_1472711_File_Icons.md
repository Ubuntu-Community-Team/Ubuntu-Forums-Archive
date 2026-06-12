---
title: "File Icons"
date: 2010-05-04
forum: General Help
---

### Post by Qbert on 2010-05-04
I just got Lynx installed on one of my media servers. So far, so good, but I got a question. All of my movie files have covers associated with them through iTunes that show up when browsing, but only half of them show up. Is there a way to make them all show or a way to make a picture the file icon?  Thanks for any help.

---

### Post by Qbert on 2010-05-06
Did I post this in the wrong section?

---

### Post by Ginsu543 on 2010-05-07
I'm not quite sure I understand what your problem is. I'm assuming that you are browsing through your movie files using Nautilus. Are you having trouble with Nautilus not showing the icons for your movie files as thumbnails but as generic movie icons? If so, you may want to open Nautilus and go to Edit --> Preferences. Click on the Preview tab and take a look at the settings under "Other Previewable Files." Set the "Only for files smaller than:" setting to 4 GB. This will ensure that Nautilus will generate a thumbnail for every file up to 4 GB in size (which will cover most if not all of your movie files). Of course, you can set it to whatever value you think is appropriate. Hope that helps.

---

### Post by Qbert on 2010-05-09
Thanks for the reply Ginsu.  Yes, that is my problem.  I have thumbnails attached to all my files via iTunes.  0 through the letter D don't show up at all.  After than it's about 80% that do show up.  My machine has two drives.  If I copy and past one of the files the preview shows up, but if I move it back it goes away again.  I tried your suggestion, but it didn't seem to work for me.  Is there some way I can force it to show up?  The drive is formatted NTFS I believe as it used to be in my Windows PC.  Would that make a difference?  Thanks again.

---

### Post by Ginsu543 on 2010-05-09
I have all my media files (photos, music, and video) on two of my four 1 TB Western Digital Caviar Black drives, and both of them are formatted in NTFS (I wanted to make sure that I can access these files from both Ubuntu and Windows). I don't have any trouble on my machine getting Nautilus to display thumbnails, so I don't believe NTFS itself is the problem.

In Nautilus --> Preferences --> Preview tab, do you have the "Show thumbnails" radio button set to "Always?" I as only because in Karmic, Nautilus would display thumbnails of files on my NTFS volumes (which are not listed in fstab and so are not mounted automatically at boot-up) with "Show thumbnails" set to "Local Files Only" (the default setting), but in Lucid I had to change it to "Always" for those thumbnails to be displayed.

If that doesn't work, I don't know how else to deal with your problem.

---

### Post by Qbert on 2010-05-12
Thanks again Ginsu.  Perhaps I'm looking at this the wrong way.  How do I delete and attach a preview to a file in 10.04?  Thanks.

---

### Post by Qbert on 2010-05-27
OK, I figured out by hitting the properties page and clicking the icon, I can attach a picture to the file.  The problem is the new preview files are much smaller than the ones carried over from iTunes.  Anyway to fix that?  Thanks for any help.

---

### Post by Qbert on 2010-11-24
I figured later that if you hit the ctrl button and move the mouse wheel up or down, it'll make the icon previews larger or smaller.  If you just put the files in another folder and adjust them, you can get them to the right size.

---

