---
title: "Folder Icons? Set Personal Folders"
date: 2011-04-03
forum: General Help
---

### Post by techunit on 2011-04-03
Hey guys I doubt I will actually get a good answer but I'll give this a shot.

I have moved all my music to the dropbox folder to be synced.
That however isn't the problem.

I changed the folder icon to the music icon and added it to my Personal Photos. However the little icon doens't reflect the change.

Would do think?[http://dl.dropbox.com/u/4087635/Selection_018.jpeg]("http://dl.dropbox.com/u/4087635/Selection_018.jpeg")

---

### Post by Learning Linux 2011 on 2011-04-03
Is that little icon in the "Places" menu or somewhere else?

---

### Post by techunit on 2011-04-03
I don't technically have a places menu. Because I don't have a gnome-panel. I mean why doesn't setting a custom icon via the preferences get it reflected in the Personal section of nautilus-elementary.

---

### Post by Learning Linux 2011 on 2011-04-03
It isn't the same icon re-sized, it is a different icon altogether.

Icons are usually stored in "usr/share/icons".

The icons are not the same sizes, there are different icons for menus, etc.  You may just be using a generic icon.

---

### Post by techunit on 2011-04-03
I am quite aware. I chose an icon quite specifically as being scalable for that very reason. I chose the icon from /usr/share/icons/faenza/places/folder_music.svg

I am not stupid, I am asking if there is a reason or am I missing something. Thanks for the attempt though.

---

### Post by Learning Linux 2011 on 2011-04-03
Yeah, this might be above my pay grade lol.  I just noticed you have 700 posts, sry if I offended you.

What menu is that picture from?  It is from the Nautilus elementary file manager?

Also, It may not be of much help, and I don't mean to insult you if it isn't, but my icons folder has different sizes, 16x16, 22x22, etc. and different sizes are used for different things.  Is that the case with your menu? Saying what the menu is from may help others.

---

### Post by techunit on 2011-04-03
I suppose I could have provide more information on the image. The screenshot is of nautilus-elementary's personal folders section. In laymans terms thats the advanced file brower.

No offense was taken. Please bean count doesn't mean much if you specialize.

I know more about UI customization and grub than I do about all kinds of things. But after running the ubuntuvideotutorials.org website I have learned more than I can remember.

I was happier to see someone make an attempt to help! Thanks a lot for giving it a go! More often than not my problems go right over the heads of people and my forum posts get ignored. :)

---

### Post by Jouke74 on 2011-04-04
You can simply change the icon of any folder by opening the folder properties in Nautilus, under the tab Basic, click on the Icon over there, then browse for the icon that you want. No special tricks needed.

---

### Post by Learning Linux 2011 on 2011-04-04
> **Jouke74 said:**
> You can simply change the icon of any folder by opening the folder properties in Nautilus, under the tab Basic, click on the Icon over there, then browse for the icon that you want. No special tricks needed.

I think he already did that. I think his question is, how do you change the icon in the [COLOR=Black]*menu*[/COLOR] of Nautilus?

---

### Post by techunit on 2011-04-04
@Jouke74 Yes I did that in the first place. I want to know how to get the change reflected in the Personal section of Nautilus-elementary.

Image attached.[http://dl.dropbox.com/u/4087635/Dropbox_019.jpeg]("http://dl.dropbox.com/u/4087635/Dropbox_019.jpeg")

---

### Post by Krytarik on 2011-04-04
In those menu, Nautilus only sets the special icons for directories specified in "~/.config/user-dirs.dirs", in your case it's the directory specified for "XDG_MUSIC_DIR". The same applies to the "Places" menu. Do you also need to regularily access the directory specified for those (the default is "~/Music")? If not, simply set it to your Dropbox directory.

Greetings.

---

### Post by Learning Linux 2011 on 2011-04-05
I figured out how to do this on my machine
That menu you are referring to is just using a generic 16x16 icon called "folder.png" which is located in your /usr/share/icons/(whatever theme you are using) folder, so you would need to change that icon.


Go into your /usr/share/icons/(whatever theme you are using) folder

go into your 16x16 folder 

then into the "places" folder inside that.

You will see all of the folders that Nautilus is using for that menu.  Rename "folder.png" into something else like "folder2.png". (That should be the folder you are referring to). 

Then make a copy of your "folder-music.png" folder (or whatever icon you want)
and then paste it in that same directory, so there will be a copy of the music folder.  Then there should be two copies of the same icon, one named "copy".

Then rename that copied folder: "folder.png"


Then go back up two levels to (whatever theme you are using) and move or rename the "icon-theme.cache" file temporarily (apparently it stores some sort of icon cache)

Then close Nautilus and reopen it


Then you can put the "icon-theme.cache" file back or rename it back to normal.  Then close and open Nautilus again.


That should do it!  It worked on mine.

---

### Post by Learning Linux 2011 on 2011-04-05
I just re-read your post and I noticed you were talking about the scalable icon.

What I described above might not be relevant to you.  

Your problem might have something to do with that "icon-theme.cache" file in your /usr/share/icons/faenza folder

It seems like if you rename that file (or move it to the desktop or something) and close Nautilus then re-open Nautilus, then rename that file back to normal (or put it back into the folder),
and then close and open Nautilus again, that might solve the problem.

---

### Post by Jouke74 on 2011-04-05
Can you delete the old link to the folder in the nautilus menu, and simply re-drag the folder into the places part of nautilus? 

(sorry about not reading first post well enough).

---

### Post by techunit on 2011-04-05
Jouke74 Not a problem. I'll take a look at the problem again.

I am sure there must be an easier way.

---

### Post by techunit on 2011-04-05
Krytarik thank you for your input. It helped alot.

If I want to set the icon for Dropbox do I need to put an icon somewhere for it?

---

