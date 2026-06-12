---
title: "Custom made screensaver"
date: 2010-01-24
forum: General Help
---

### Post by bug67 on 2010-01-24
While looking for even *more* screensavers, I came across an interesting article here:

[http://www.freesoftwaremagazine.com/columns/customizing_your_screensaver](http://www.freesoftwaremagazine.com/columns/customizing_your_screensaver)

I decided to give it a shot.  I have a BMW motorcycle and kinda have a BMW motorcycle theme going on with my desktop.  I thought modifying the "Floating Ubuntu" screensaver to a floating BMW logo screensaver would be kick a**!

Here's what I did:

Opened a root shell:

```
sudo -s
```

Then, I made a file name for my screensaver:

```
cd /usr/share/applications/screensavers
cp ubuntu_theme.desktop bmw-floaters.desktop
```

I then edited my new bmw-floaters.desktop file by typing:

```
gedit bmw-floaters.desktop
```

I changed all the "floating ubuntu" stuff to the following:
```

[Desktop Entry]
Name=Floating BMW
Comment=BMW logo floating around the screen
Exec=floaters /home/myusername/Pictures/IconsPNG/BMW.png
TryExec=floaters
StartupNotify=false
Terminal=false
Type=Application
Categories=GNOME;Screensaver
OnlyShowIn=GNOME

```

And saved the file and *closed the terminal* (*this is where I think the problem is happening maybe*)

Then, when I go to System > Preferences > Screensaver, I am able to  select my new "BMW Floaters" screensaver!  Everything works fine.  I am able to see it in the small preview window and in the large, full screen  preview.  However, when it actually comes time for the thing to kick on for real, I just get a blank screen; no floating BMW logo.  

*Now, I'm a real terminal n00b and don't really know what I'm doing.  Remember above when I wrote that I saved and *closed the terminal*?  Well, I'm getting a message saying that a process is still running and if I close, it will kill all running processes.  Is this why my custom screensaver isn't working right?  Am I leaving something incomplete?

I know this is a really long and drawn out blah, blah, blah but, I'd really like to know how to make this work.  So, if any of you terminal gurus know what I'm doing wrong, I would greatly appreciate some help and guidance.  Thanks!

:popcorn:

---

### Post by bug67 on 2010-01-25
Not sure I got this in the correct forum.  :confused: 

bump.

---

### Post by bug67 on 2010-01-25
Nevermind.  It seems I wasn't patient enough.  All appears to be well.  We have floating BMW logos on the screen.  :D

---

### Post by schworak on 2010-09-01
Simple and yet so wonderful!

Just used this to create my own GL1800 screen saver. So easy!

---

### Post by inameiname on 2010-09-01
This doesn't seem to be working for me. I've done exactly as mentioned, AND even see my version of the floating Ubuntu screensaver in /usr/share/applications/screensavers, however it isn't showing up in my list of Screensavers. I've opened it several times and even restarted, but nothing.

Anybody know why?

---

### Post by Andrew_P on 2010-12-21
> **inameiname said:**
> This doesn't seem to be working for me. I've done exactly as mentioned, AND even see my version of the floating Ubuntu screensaver in /usr/share/applications/screensavers, however it isn't showing up in my list of Screensavers. I've opened it several times and even restarted, but nothing.

Anybody know why?

The floaters executable module may not be able to handle the image file format that you supplied.  It appears that floaters was written specifically to handle .svg files, since they're continuously scalable with no loss of sharpness, as well as supporting variable transparency.  (The transparency effect is observable in the GNOME Floating Feet screen saver when two or more images overlap.)  Others have reported success with .jpg files and .png files.  However, I've found that it doesn't always work even with known-good .svg files:  The image appears for 1-2 seconds during preview and then fades into blackness, not to be seen again, and *never* appears when the screen  saver is activated normally or triggered manually with Brightside.  It's too finicky &#8212; or buggy. Just a guess, but the GNOME x-screensaver utility may be saving information in a cache somewhere, and if bad information gets written there for a customized screen saver, it may be having difficulty updating it with changes.  Try using the touch command in a root terminal window to update the timestamp of your .desktop file and see if that helps.  Also, double-check the name of your image file and make sure that you've spelled it *exactly* correctly in the .desktop file, including capitalization, punctuation and path.  I've also noticed that none of the files in the /usr/share/applications/screensavers directory use anything except hyphens in the the image file names and exactly one period in the name to define the extension.  Some GNOME utilities apparently get confused by more than one period in file names.

You may remember the [After Dark]("http://en.wikipedia.org/wiki/After_Dark_(software)") screensavers from Berkeley Systems, written for the Apple Macintosh around 1990.  Soon thereafter it was ported to Windows 3.1, running on MS-DOS, and it worked better and was totally configurable from dialog boxes, with the user never having to resort to Notepad or other text editors to change the image in its versions of floating image modules.  That was over 20 years ago!  This whole x-screensaver concept in GNOME is seriously in need of updating to the 21st century.

---

