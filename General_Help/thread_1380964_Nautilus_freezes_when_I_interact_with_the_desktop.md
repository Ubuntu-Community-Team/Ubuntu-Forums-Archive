---
title: "Nautilus freezes when I interact with the desktop"
date: 2010-01-14
forum: General Help
---

### Post by averybigfish on 2010-01-14
I have no idea what I did or how I did it, but I believe this problem is of my own making. I tried to switch off the desktop at another time using gconf-editor, but I think I may have accidentally changed other settings that I wasn't supposed to. I tried to change them back, but I couldn't get it fixed.

Anyhow, please help me out. There seems to be no other details regarding this problem.

Further details:
When I run nautilus /home/adriaan/Desktop it give the following output:

(nautilus:2433): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

[and the following, after quite a while of waiting]
(nautilus:2433): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(nautilus:2433): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by averybigfish on 2010-01-14
Found the problem: one of the files on my desktop, surprisingly. Well, that is what is suspected at least. I had a jpg file that I had opened with Inkscape, edited, and accidentally saved as a jpg again. Ultimately, it was a jpg file with svg content. The guess is that nautilus was trying to load a preview, and crashed with the jumbled jpg content.

---

### Post by junapp on 2010-01-17
turns out I had the exact same problem. I opened filename.jpg with inkscape, edited it, and saved it as filename.jpg. It was an svg file which when I opened with inkscape "inkscape filename.jpg" showed the svg, but with a "image not loaded" type icon where the image should have been (circular reference type thing I guess).

This was seriously crashing nautilus even when I was browsing and trying to open other images in the ~/Pictures folder and other subfolders.

Thanks for mentioning this - I was playing with inkscape a few nights ago and had completely forgotten but your post triggered my memory - THANK YOU - nautilus was going bonkers and I thought it had to do with dropping a network drive between laptop lid closures. Seems deleting the offending filename.jpg fixed my issue.

---

### Post by averybigfish on 2010-01-18
Absolutely no problem. I'm glad the post actually did some good :)

---

### Post by stoneage on 2010-06-10
*bump*

I exported three files from Inkscape, .ps, .eps and inkscape .svg onto the Desktop.

I was getting the same error trying to launch nautilus from a terminal. Since the last thing I did was generate those files, I removed them and problem solved....... :)

The original file I traced in Inkscape was large, around 150 MB. I don't know how large the exported files were, as I was trying to access their Properties when nautilus went down. They may or may not have been large(I doubt it, they were uncomplicated), but trying to read them must be what broke nautilus.

---

### Post by axxter on 2010-07-25
I know this is an old post, but it helped me solve a "freezing" problem I was having with Nautilus.
I'd saved a .svg file to my home folder, and Nautilus would freeze (gray out) every time I tried to access this.
Removing the .svg file seems to have been the fix. 

Thanks for this thread.

---

### Post by stuartcnz on 2010-08-01
I'm having this same problem now. 

How do you go about deleting the offending file?

---

### Post by stuartcnz on 2010-08-01
Figured it out. It didn't work with a GUI, but by opening a terminal and using the rm command sorted it.

$ rm /home/stuart/Pictures/file.gif   

or where ever your offending file happens to be.

---

### Post by PrivateSNAFU on 2010-10-01
[SOLVED]

Thank you, this fixed my problem.  Should this be reported as a bug because if nautilus freezes when it cant create an icon this is a problem.  For every day users, having to go in to the terminal and delete a svg file could be a problem.

Thanks to you all for your help

Love to all the ubuntu community


Dan

---

### Post by junapp on 2010-10-16
seems to affect more than a few people.
[http://ubuntuforums.org/showthread.php?t=1597469](http://ubuntuforums.org/showthread.php?t=1597469)

---

### Post by abdusamed on 2010-10-25
I'M having exactly the same problem.. i don't have any SVG files open!! I can't [****-delete] any files without nautilus freezing!

See picture for the files opened

---

### Post by abdusamed on 2010-10-26
w00t ... i fixed it. For me it was vineyard the latest one in beta causing the problem. For some reason it's 'pyton' wine wasn't working properly with nautilus. All I had to do is uses 'open file' to find the pyton and manually delete them using terminal

$rm [link to the directory]

I recommend to install pcmanfm. I had to use rm because pcmanfm was having segmentation error when I tired to delete the open files. Faulty buggy phyton files were to blame

---

### Post by brion@cbkidder.com on 2011-02-02
I had exactly the same problem today; VERY frustrating. I resaved the jpg images used in my Inkscape SVG file to jpg with preview using GIMP, and that alone didn't do the trick so I converted the tiff files used in the Inkscape SVG to jpg with preview, and that fixed the trouble. As soon as the image jpgs were able to show their icon preview, the SVG file was able to show its preview, and Nautilus stopped crashing.

This could as easily have happened with Adobe Photoshop and Illustrator, but then we'd be out a thousand bucks and frustrated. At least now we're only frustrated!

---

