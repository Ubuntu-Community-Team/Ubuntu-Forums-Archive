---
title: "Changing Default Icons For Video Files?"
date: 2009-11-16
forum: General Help
---

### Post by joelandsonja on 2009-11-16
I would like to change the default icons for all of my AVI and MPG files to a specific icon, but I don't know how. 

I realize you can change certain icons by right clicking the file and clicking on the little Icon Button in the Properties menu, but it doesn't seem to work for changing icons for specific file types.

Any suggestions are appreciated!

---

### Post by joelandsonja on 2009-11-17
*Bump*

---

### Post by joelandsonja on 2009-11-17
*Bump*

---

### Post by joelandsonja on 2009-11-19
*Bump*

---

### Post by Vaphell on 2009-11-19
i guess icons are taken from /usr/share/icons/<themename>/<size>/mimetypes

i don't know if you can override default settings by putting the icon in your home somewhere, but replacing it in mentioned system directories, in the directory of the theme you use should do the trick.

---

### Post by joelandsonja on 2009-11-23
For some reason I simply cannot get this thing to work ... 

When I read the instructions to replace the icons that you sent me, it seemed easy enough for me to change, but for some reason the icons I want to change doesn't seem to show up when I try to find it in the icon folders. I'm also not sure how I would change the icons that appear as_ a screen shot_ since It seems to be defaulting the icon to the first frame of the video itself. 
 
Here's a screenshot of what I mean ... 
 
[http://www.flickr.com/photos/44912149@N02/4125694339/in/datetaken](http://www.flickr.com/photos/44912149@N02/4125694339/in/datetaken)
 
As you can see it is mixing the icons with either an icon of the first frame of the video, or that annoying clock icon. All I want to do is default all MPEG files to one particular icon of my own choosing. Your instructions seem simple enough, but I can't seem to find the icon I want to change.

---

### Post by Minsky on 2009-11-23
You may have Show Thumbnails enabled in Nautilus. Go into Nautilus and then go to **Edit>Preferences**. Click on the **Preview** tab, and set **Show Thumbnails** to **Never**. That may do the trick.

---

### Post by joelandsonja on 2009-11-23
Hmm ... that fixed half the problem! 

Unfortunately I still have the clock icons showing on some of the files, but now the icons that were once thumbnails have changed to the orange filmstrip icons. (Which I can live with) 

Would there be another setting that is effecting the other icons which makes them default as the clock icon?

---

### Post by Minsky on 2009-11-24
Go into your Home folder and press **CTRL-H** to display the hidden files. You should see a folder called **.thumbnails**. Goto **.thumbnails>fail>gnome-thumbnail-factory** and delete everything in there. These are the thumbnails that Nautilus failed to display and substituted with a clock icon instead. All your video files should now have the filmstrp icons which I think you can change by replacing them in the location Vaphell suggested.

---

