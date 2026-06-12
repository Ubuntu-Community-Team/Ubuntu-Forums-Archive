---
title: "Ubuntu 10.10 on HPtx2000"
date: 2011-01-20
forum: General Help
---

### Post by Fuitab on 2011-01-20
Hello all
I recently installed Ubuntu 10.10 on my sister's HPtx2000 since she isn't going to use it anymore and it worked better than I expect. The touchscreen works without any additional driver tweaking and installation <3, the wireless works fine, the sound works.

I listed those because when i was installing, I was looking around at other people that did this and those were the problems they had (but those was of an old OS).

Well anyways, what I want to ask is about the stuff that doesn't work and the stuff I want to do:
The buttons that flip the screen and etc doesn't work. Is there a way to map them and flip the orientation of the screen? And the other buttons too, like the media button. Is there a way to map them to open VLC or something?
Does anyone know any tablet programs for Ubuntu? E.g a simple text program that can convert stuff written to neat, typed font? A way to write text into a google search bar using the stylus? And while we're on this, is there a way to map a left click on the touch screen? In Windows, the left click could be mapped to: a). a side button of the pen, b) the top button of the pen, and c) holding the pen down onto the touchscreen.

I also have another question which is more general. 
Can anyone tell me how to use Samba to access a public folder of a Windows computer? And to access the printer connect to the Windows computer? Some of the tutorials I found were only for folders and printers on the Ubuntu computer.

Thank you for taking your time to read this ;)

---

### Post by Favux on 2011-01-20
Hi Fuitab,

> The buttons that flip the screen and etc doesn't work. Is there a way to map them and flip the orientation of the screen? And the other buttons too, like the media button. Is there a way to map them to open VLC or something?
We're down to 1 bezel button from 2 with the more recent kernels.  Have never had more than 2 of the 4 bezel buttons working.  It was the DVD and media button and now it's just the media button.  Mine calls up Rhythm Box.  Since it looks like a Q we used to call it the Q key and mapped it to a rotation script.  See the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1") for button mapping.  There is also a link to what we know about the bezel buttons buried in Notes.

Fortunately I don't use that bezel button for rotation anymore.  I just use Magick Rotation for automatic rotation.  See:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)  I don't actually need the Q key for Rythym Box either since I have it on my Cairo Dock (Glx Dock).  Just haven't bothered to map it to anything yet.
> Does anyone know any tablet programs for Ubuntu? E.g a simple text program that can convert stuff written to neat, typed font? A way to write text into a google search bar using the stylus?
You'll want CellWriter.  It has letter recognition and also toggles into an onscreen keyboard.  It's the default in Magick.  You'll also want Xournal and you may want to look at EasyStroke.
> And while we're on this, is there a way to map a left click on the touch screen? In Windows, the left click could be mapped to: a). a side button of the pen, b) the top button of the pen, and c) holding the pen down onto the touchscreen.
The stylus tip by default is the left button.  The stylus button can be mapped to right or middle click.  The eraser is a "left click" i.e. works in programs that support it like Gimp and Xournal if you configure the extended input devices or whatever.  I'm not quite sure what you are asking.

For a xsetwacom script to control your TX2000 see post #2 on the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496756&postcount=2").  It's attached to the bottom of the post in a tar with other tablet pc scripts.

---

### Post by Fuitab on 2011-01-20
Thank you so much! I really appreciate you using your time to help me.

---

### Post by Mark Phelps on 2011-01-21
> **Fuitab said:**
> 
Does anyone know any tablet programs for Ubuntu? E.g a simple text program that can convert stuff written to neat, typed font? 
Cellwriter lets you input individual characters, one per cell.

If you're asking about a general handwriting recognition program like Windows Journal, last time I checked, there was no such thing.  Also, there is no convert-handwriting-to-text app for Linux, either. Since I use Journal every day, these were some of the main reasons for going back to using Windows with my Tablet PC.

> A way to write text into a google search bar using the stylus? 
Again, I believe the answer is no.

---

### Post by Favux on 2011-01-21
Hi Mark,

Once again a little ray of sunshine in our lives.  Why do you bother?
> [QUOTE]A way to write text into a google search bar using the stylus? Again, I believe the answer is no[/QUOTE]
That is exactly what CellWriter is for.  Either with letter entry or the onscreen keyboard feature, just like in Windows.  Allow me to direct you to a video of a HP TX2 using Magick Rotation, ginn, and Onboard in Maverick:  [http://www.youtube.com/watch?v=CH6kxNRYz20](http://www.youtube.com/watch?v=CH6kxNRYz20)  You can see him type in a document and use the keyboard in menus.

This isn't fantasy, this is with currently available stuff in Maverick for multi-touch capable devices.
> If you're asking about a general handwriting recognition program like Windows Journal, last time I checked, there was no such thing. Also, there is no convert-handwriting-to-text app for Linux, either. Since I use Journal every day, these were some of the main reasons for going back to using Windows with my Tablet PC.
That might change in the near future.  There are several active open source OCR projects now.  Also with the World Wide Web Consortium working on Digital Ink standards, see [W3C Invites Implementations of Ink Markup Language (InkML)]("http://www.w3.org/News/2011.html#entry-8986")  and [http://www.w3.org/TR/2011/CR-InkML-20110111/](http://www.w3.org/TR/2011/CR-InkML-20110111/) there may be another route to handwriting recognition.

---

