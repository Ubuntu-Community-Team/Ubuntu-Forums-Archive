---
title: "Installing Irfanview in Wine??"
date: 2009-12-30
forum: General Help
---

### Post by delogren on 2009-12-30
Howdy,

I've been trying to install Irfanview in Wine, but no joy.  Here' what I did, and the results.  What am I missing here?


del@dell-desktop:~/Desktop$ wine iview425_setup.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\del\\Desktop\\iview425_setup.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\del\\Desktop\\iview425_setup.exe" failed, status c0000135
del@dell-desktop:~/Desktop$ 


--del

---

### Post by howefield on 2009-12-30
Read this

[https://help.ubuntu.com/community/Wine/IrfanView](https://help.ubuntu.com/community/Wine/IrfanView)

---

### Post by spcwingo on 2009-12-30
It's just telling you that you need MFC42.DLL.  Once you get your hands on it just drop it in your /home/your_user_name/.wine/drive_c/windows/system32 folder.  IrfanView even after installed takes a little tweaking to get it going (editing of the i_view32.ini file).

---

### Post by switch10 on 2009-12-30
the gimp does everything that irfanview will do..  what are you doing, resizing images?

---

### Post by delogren on 2009-12-30
> **spcwingo said:**
> It's just telling you that you need MFC42.DLL.  Once you get your hands on it just drop it in your /home/your_user_name/.wine/drive_c/windows/system32 folder.  IrfanView even after installed takes a little tweaking to get it going (editing of the i_view32.ini file).

That's done, thanks,

But it still doesn't seem to be in Wine.

I'm still missing something.

--del

---

### Post by delogren on 2009-12-30
> **switch10 said:**
> the gimp does everything that irfanview will do..  what are you doing, resizing images?

It's kind of a long story...  But I'll try to keep it short..

I'm trying to come up with a tutorial for Windoze users who are trying to process raw data from an imaging run on a telescope in New Mexico, without spending $$Hundreds on software.  Do a search for Lightbuckets.com to get an idea of what I'm up to..

The problem is how to convert a Huge TIFF (64MB) file into something that's small enough to send to friends or plop on the web.  The Windoze version of Gimp cuts a 16 bit Tiff to 8 bits before it will eat it, losing data..  Ifranview does not.

I only wanted Irfanview in Wine because it's so much easier to deal with snapping screen shots and writing html in a linux system than 'doze.

--del


[LEFT]
[/LEFT]

---

### Post by lkraemer on 2010-02-15
I had several old R/C Plane Plans scanned by Zephyr Printing in Iowa.
All but three files would not load into any Graphics Program because
they were scanned at 600 DPI versus 300 DPI.  What could I do to
get them viewable?

As an example the original file Temp00405.Tif with Width x Height
of 21600 x 33712 and file size 3.27MB would not load with anything I tried. WHEW!!!!!

I installed IRFANVIEW version 4.23 in Ubuntu 9.10.
[http://www.wine-reviews.net/wine-reviews/wine/irfanview-423-on-linux-with-wine.html](http://www.wine-reviews.net/wine-reviews/wine/irfanview-423-on-linux-with-wine.html)

Then I loaded the image in IRFANVIEW then Rotated Right/Left as required.

Use IMAGE -> RESIZE/RESAMPLE Image (CNTRL R) and use right side menu to select
HALF for 16856 x 10800 Pixels.  (This won't affect the image's contrast or brightness)
Keep the DEFAULT DPI selection. (600 DPI) You can decrease the color to 1 Bit Per Pixel.
Save the image as Temp00405c.Tif, then Load into Gimp, Inkscape, or Windows Adobe Photoshop.

Crop as necessary.

Might apply to the large files you are working with.

The Batch processing works great for large files since they don't have to be loaded.

lk

---

### Post by Richard1979 on 2010-02-15
21600 x 33712 :O

That's pretty hardcore...

---

### Post by nechus on 2010-03-20
The information on the winehq.org on how to install IrfanView 4.25 in wine are quite useful:

1. Get the mfc42.dll file from a Windows machine and copy it to the system32 folder in .wine.

2. Install IrfanView 4.25. Then go to the .wine>...>irfanview folder and delete i_view32.ini

Done!

---

