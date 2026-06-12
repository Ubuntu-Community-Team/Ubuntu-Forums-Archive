---
title: "Placing A Picture On Top Of Background?"
date: 2010-04-11
forum: General Help
---

### Post by tomsubt on 2010-04-11
Too Many Snags with Advice, newbie getting too many people upset, Thank You Anyway..

---

### Post by WinterRain on 2010-04-11
You will need to open the backgroung picture in GIMP (like photoshop) and add the second picture to it, then save the pic when finished. You can then make that pic your desktop wallpaper.

---

### Post by tomsubt on 2010-04-11
> **WinterRain said:**
> You will need to open the backgroung picture in GIMP (like photoshop) and add the second picture to it, then save the pic when finished. You can then make that pic your desktop wallpaper.
how do I bring up the desktop background and then add this picture to it?
I brought up the GIMP image editor and got the picture pasted in it, but dont have the original desktop background up to add it to (I assume you mean paste it)?? Please let me know your thoughts?

---

### Post by spiky001 on 2010-04-11
how about you have clear desktop then print screen open gimp paste in pic then do what you need to, then save it

---

### Post by ajgreeny on 2010-04-11
The default background images are in /usr/share/backgrounds.  Find your chosen one there, open it in gimp, add the new pic to the middle of it or wherever you want it, save it as a new image in home, and then add that image to the choice you see when you right click on desktop and "Change Desktop Background"

---

### Post by tomsubt on 2010-04-11
Ok, I just made a boo boo, I deleted the original desktop background that I really liked from the "Change Background options" and it is not in the background selections anymore, do You know how I can get that back first? Thanks

---

### Post by ajgreeny on 2010-04-11
> **tomsubt said:**
> Ok, I just made a boo boo, I deleted the original desktop background that I really liked from the "Change Background options" and it is not in the background selections anymore, do You know how I can get that back first? Thanks
Click Add in the Change Desktop Background dialog and navigate to /usr/share/backgrounds and find the desktop background you have now removed.  The file should still be there.  After that do what I said above, saving the new version to home.

---

### Post by tomsubt on 2010-04-11
AJGreeny, Thank You, Got it back again.
I will look into and try your instructions tomorrow, Have to get off now.

---

### Post by tomsubt on 2010-04-12
Ok, This is as far as I got, please see the attachment, 
The original background is what I want and I would like to put this picture exactly how it looks (size etc..) directly top of the background wallpaper

How can I do this from here>>>>

---

### Post by tomsubt on 2010-04-12
Hope this attachment opens ok>>>>>

---

### Post by ajgreeny on 2010-04-12
Ok, Here's how to do it.

Open the background image, and the Jesus image in separate gimp windows.
Now right click on the Jesus image and chose "copy".
Now right click on the background image and chose "paste as layer".
Now using the move tool you can move the Jesus image layer to exactly where you want it and then save the new image.

It is probably the layer management that is baffling you, but once you get used to it, it is a very powerful tool.

---

### Post by tomsubt on 2010-04-12
You said>>>  Open the background image, and the Jesus image in separate gimp windows.

How do You open them, I dont see any option.

When I went to Change background image and selected the desktop image I already have on the desktop,there was an option to open that at the bottom but it only took me back to the Appearance Preferences!

---

### Post by Chronon on 2010-04-12
They are both already open in the screenshot you posted.  Select the foreground image and choose "Select All", then "Copy".  Now go to the background image window and choose "Paste".

EDIT: Apparently I mistook the screen shot window for another GIMP window.

---

### Post by fragos on 2010-04-12
The default Ubuntu wallpaper jpegs are in /usr/share/backgrounds. Almost any image file can be used as wallpaper and they need by be located in this folder.

---

### Post by ajgreeny on 2010-04-13
> **tomsubt said:**
> You said>>>  Open the background image, and the Jesus image in separate gimp windows.

How do You open them, I dont see any option.

When I went to Change background image and selected the desktop image I already have on the desktop,there was an option to open that at the bottom but it only took me back to the Appearance Preferences!
I meant open both images with gimp, not just use the background image as the desktop background.  So open the background image in gimp, then open the Jesus pic in gimp, and then do the copy of Jesus with a right click, and paste as layer on to the background image.  It really is not too difficult.

---

### Post by tomsubt on 2010-04-14
> **ajgreeny said:**
> I meant open both images with gimp, not just use the background image as the desktop background.  So open the background image in gimp, then open the Jesus pic in gimp, and then do the copy of Jesus with a right click, and paste as layer on to the background image.  It really is not too difficult.

Ok, I got as far as right click and copy of Jesus, but when i went to paste it onto the picture to the left on attachment (its the same as the background you see)
It would not Paste, so I tried to paste it directly on to the backgroung (on desktop) and that would not work?

---

### Post by Chronon on 2010-04-14
As others have said, both images need to be opened in the GIMP.

---

### Post by fragos on 2010-04-14
After pasting an image it exists as a layer and to make it part of the image it must be merged and saved.

---

### Post by tomsubt on 2010-04-14
As others have said, both images need to be opened in the GIMP

I thought they were opened in gimp I clicked on gimp image editor in applications, is that not right?  Is it possible I dont have gimp installed yet?

Fragos, Thanks  I will be keeping mind what you said

---

### Post by fragos on 2010-04-14
> **tomsubt said:**
> As others have said, both images need to be opened in the GIMP

I thought they were opened in gimp I clicked on gimp image editor in applications, is that not right?  Is it possible I dont have gimp installed yet?

Fragos, Thanks  I will be keeping mind what you said

GIMP is likely not the default viewing ap so you'll need to right click an image icon and specifically select it.

---

### Post by jocko on 2010-04-14
> **tomsubt said:**
> As others have said, both images need to be opened in the GIMP

I thought they were opened in gimp I clicked on gimp image editor in applications, is that not right?  Is it possible I dont have gimp installed yet?You do have gimp installed. It is open in your screenshot.
In your screenshot you have only one of the images open in gimp, and from what I understand from your posts you are trying to paste directly to the desktop. You need to open *both* files in separate gimp windows, copy the smaller file and paste it in the gimp window where the other one is open.
You obviously have figured out how to open *one* image in gimp (the jesus picture in your screenshot), now just do the same to open the other (the desktop background image). 

In a file browser (nautilus), browse to where the desktop background files are (/usr/share/backgrounds), find the background you want to change, right click it and choose "open with" --> "gimp image editor".

---

### Post by tomsubt on 2010-04-15
ok, I dont know now if Gimp is installed or not, I went to look at all the installed items and Gimp had a green box next to it, which I would assume it is installed, but when I right click a picture as instructed and scroll down the Open With Options, Gimp is NOT one of them. Please see attachment, Thanks

---

### Post by Chronon on 2010-04-15
> **tomsubt said:**
> ok, I dont know now if Gimp is installed or not, I went to look at all the installed items and Gimp had a green box next to it, which I would assume it is installed, but when I right click a picture as instructed and scroll down the Open With Options, Gimp is NOT one of them. Please see attachment, Thanks

I see GIMP right in the list.  It's between gedit and Image Viewer.

---

### Post by tomsubt on 2010-04-15
Ok, I will start at beginning here, please see attachment and notice when I right click the background I want there is NO option to open it in Gimp Editor, is this the shot I am suppose to right  click?

---

### Post by Chronon on 2010-04-15
You need to locate it in the file browser.  That's some sort of wallpaper dialog.  Go to "Places" and find the images from there.  You obviously know how to do this because the previous screen shot was of the "Open With" dialog.

You can also just open the GIMP and then use its "Open" dialogs to open the appropriate files.  This is pretty basic file management stuff and isn't any different from what you would do in Windows.

The information present in this thread should be enough to allow you to accomplish your task.  If you still don't understand how to copy and paste an image perhaps you should consult some tutorials, which you can locate by searching with a search engine like Google.

---

### Post by tomsubt on 2010-04-15
Actually I have been copying and pasting with no problem in windows for years but I dont see the options come up in ubuntu, I guess they are situated differently.
Any way I will follow your instructions and see what happens, however I will not be on this pc again until next week.
Talk to you Guys then, Thank You

---

### Post by Chronon on 2010-04-15
Copy and Paste are located in the Edit menu of GIMP, just like in most Windows applications.  If you open both images in the GIMP then copy and paste should be an almost trivial operation.  (One final hint: pay attention to what region you have selected before trying to copy.)

---

### Post by fragos on 2010-04-15
Open both images in GIMP. Select the window you want to cut from and use one of the selection tools to outline what you want to cut. Ctrl-C performs the cut to the clipboard just like in Windows. Now select the target window and Ctrl-V to paste. The item pasted will be placed in a new layer. Select the layer with the pasted image and when your cursor is positioned on the object the icon will change to 4 arrows. Hold down the left mouse button and move the object where you want it. If at this point you Save you will be prompted to merge the layers which you want to do and a new combined image is created.

---

### Post by tomsubt on 2010-04-20
Quote>>If you open both images in the GIMP then copy and paste should be an almost trivial operation.

Ok, I can open the picture in Gimp editor but not the background that I have on my desktop.
Here is what I did to try to open my background picture in Gimp, I went to "Change desktop background" and my background picture was there, when I click on it Nothing happens, so I click on "Add" and click on the name of the background picture i have and there is NO option to open in Gimp anywhere.
What am  I doing wrong? Thanks

---

### Post by fragos on 2010-04-20
Your desktop background is a special case of viewable image you can find the Ubuntu supplied desktop images at /usr/share/backgrounds. Any images you may have used as backgrounds are stored wherever they were when assigned as a background.

---

### Post by tomsubt on 2010-04-20
Ok, I finally got the screen up you guys are talking about but I still dont see the option to open it in Gimp, please see attachment, this is what I have after clicking on my desktop background.

---

### Post by jocko on 2010-04-21
> **tomsubt said:**
> Ok, I finally got the screen up you guys are talking about but I still dont see the option to open it in Gimp, please see attachment, this is what I have after clicking on my desktop background.
????
Browse there in a *file *browser (nautilus, which is the program you use to browse through the folders of your file system), not a *web* browser (firefox, which is the program you use to browse the internet).

To open a file browser, just click any folder in your "places" menu or double click a folder on your desktop. To get to /usr/share/backgrounds, first click the "Open parent folder button" (That's the button with the up arrow in the file browser's tool bar) for as many times you can until it get's greyed out. Now you should see the root (/) of the file system, which should contain a bunch of folders (boot, bin, etc, home, usr ...). Double click the "usr" folder, then the "share" folder and finally the "backgrounds" folder. Now you are in the /usr/share/backgrounds folder, and you should see the file you are interested in.

Or open gimp, click file-->open, and then browse to the  /usr/share/backgrounds folder in gimp's "open file" window.
Or, if you can't figure out how to use the mouse, press Alt+F2 and type:
```
nautilus /usr/share/backgrounds
```

---

### Post by tomsubt on 2010-04-21
Quote>>> Browse there in a file browser (nautilus, which is the program you use to browse through the folders of your file system), not a web browser (firefox, which is the program you use to browse the internet).<<<<

Is This Nautilus something I have to install first? I dont see it?

---

### Post by jocko on 2010-04-21
> **tomsubt said:**
> Quote>>> Browse there in a file browser (nautilus, which is the program you use to browse through the folders of your file system), not a web browser (firefox, which is the program you use to browse the internet).<<<<

Is This Nautilus something I have to install first? I dont see it?
Did you even read the rest of my post? I explained how to open nautilus and use it to browse to the folder like I would explain it to my grandmother. Can you open a folder and see it's contents? That's nautilus.

---

### Post by tomsubt on 2010-04-21
> **jocko said:**
> Did you even read the rest of my post? I explained how to open nautilus and use it to browse to the folder like I would explain it to my grandmother. Can you open a folder and see it's contents? That's nautilus.

Ok, After a Long Talk with Jocko's Grandmother, I finally figured it out, but when saving it to desktop I got a permission denied, please see attachment

---

### Post by fragos on 2010-04-21
That destination folder belongs to root. Rather than getting into file permissions the easy way to handle this is to store your new background in the Home folder. Click the saved image file to open the viewer. The viewer should have a menu option to make the image a background and you're done. I use Gthumb instead of the default viewer so I don't remember the exact menu items.

---

### Post by Jive Turkey on 2010-04-21
I think the missing clue for you here is that you need to open both images in gimp and create a third image.

If you copy both of the pictures to your home folder, and paste this code into a terminal (click Applications > Accessories > Terminal).

```
gimp ~/JESUS\ Internet\ Explorer\ Wallpaper.jpg & & gimp Daisy.jpg
``` *replace "Daisy.jpg" with the name of the background image you want.
 this will bring up two gimp windows, find the jesus picture, right click on jesus select "Edit > Copy," select the background window and right click anywhere on the background picture and select "Edit > Paste As > New Layer.  This will put jesus on the top left corner.  

Find the tool box palette and click on the Move tool, it looks like a crossthen click on jesus and while holding down the mousebutton move jesus to where you want him. You can play around with resizing jesus using the scale tool from the toolbox too.

To save the file use "File > Save As..." and select a place to save your file.  You will get a warning about jpeg not supporting layers or something where you need to click "export" and "save." You can then add your new file to the desktop backgrounds from the "change desktop bkground" window.

I could have just made it for in a fraction of the time it took to write this but for the whole teach a person to fish thing.

---

