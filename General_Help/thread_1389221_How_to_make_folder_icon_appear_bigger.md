---
title: "How to make folder icon appear bigger?"
date: 2010-01-24
forum: General Help
---

### Post by myromance123 on 2010-01-24
Hi there, I've made some of my own icons in Gimp and saved them as .pngs. The problem is, when I use them they always appear smaller than the system default icons. Is there no way to make them as the same size as the system icons?

I read somewhere that GNOME (which is what I use) uses .png .svg and .xpm. I am only able to save as .png with GIMP, is there a way to get .svg and .xpm extension capabilities with GIMP?

These are the icons (only two):
1. [HJ-Split Folder]("http://i335.photobucket.com/albums/m460/myromance123/HJ-Folder-Icon.png")
2. [Blood Frontier Folder]("http://i335.photobucket.com/albums/m460/myromance123/blood-folder-icon.png")


Is there maybe a specific way to make folder icons that I am not following?

Thanks for any help.

Using Ubuntu 9.10, Desktop edition.

---

### Post by mcduck on 2010-01-24
That sounds like you are leaving too much empty space around the icon itself in your picture files. Also note that icons are treated as squares, you'll want to make your icon image a square as well. (meaning no 340x270 files, make that 340x340 instead)

And yes, Gimp does support XPM and many other formats, just select what you want in the save dialog. You shouldn't have to install or configure anything to get support for these formats, they are all there by default.

SVG however is a vector image format, and Gimp is a bitmap editor. If you want SVG images you need to create them in a vector drawing program, like Inkscape for example.

---

### Post by myromance123 on 2010-03-29
Hmm I am unable to save in .xpm. There is no extension when I'm choosing to save in the desired format.

 What am I missing? Why would I not have it? Could it be named something else?

---

### Post by Gemnoc on 2010-03-29
There are a few ways to save a file in Gimp.

1) In the Save dialog, under the browser, click besides "Select filetype" (might not be the exact wording, my system is in French). Do not click the pull-down menu that's over it, this is a display filter only.

Browse the list, you'll see it listed as "pixmap X image". It's the 26th choice.

OR

2) In the Save dialog, in the name field, just rename the extension to .xpm.

I just tried with one of your icons. It works.

---

### Post by myromance123 on 2010-03-31
Thank you Gemnoc!

 I was always looking in the display filter menu ( I thought it was saving options).

 I just realised there was a Select Filetype option there. Yep, I can see the .xpm filetype. Thanks :D

---

### Post by Gemnoc on 2010-03-31
> **myromance123 said:**
> Thank you Gemnoc!

 I was always looking in the display filter menu ( I thought it was saving options).
I know! I'm always looking there too! It's a case of bad UI, in my opinion.

 > I just realised there was a Select Filetype option there. Yep, I can see the .xpm filetype. Thanks :D
My pleasure! ;)

---

