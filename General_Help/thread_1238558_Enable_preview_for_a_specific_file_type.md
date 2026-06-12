---
title: "Enable preview for a specific file type"
date: 2009-08-12
forum: General Help
---

### Post by chitresh4u on 2009-08-12
I know that its possible to enable preview of files in nautilus by navigating to edit->preferences->preview. This enables preview for all types of files (like pdf, images, etc).

 But I want to enable preview for a specific file type, say for only images (and not other files like pdf, mp3 etc). Is this possible in nautilus ?

---

### Post by starcraft.man on 2009-08-12
Nautilus File Manager > Edit > Preferences > Preview Tab > Select never for file type of choice. Seems images and multimedia (video) is grouped under other since both are the same thing really, video is just pictures moving. You can deselect text and sound files though. You can specify a file size of say (see Only for files smaller...) of 3 mb, that would rule out all video I suppose, or even smaller.

Dolphin (the KDE manager) has a whole section where ya can specify your preferences for previews on a lot of different filetypes.

Is there a particular reason why ya want to disable only some preview?

---

### Post by chitresh4u on 2009-08-12
> **starcraft.man said:**
> Nautilus File Manager > Edit > Preferences > Preview Tab > Select never for file type of choice. Seems images and multimedia (video) is grouped under other since both are the same thing really, video is just pictures moving. You can deselect text and sound files though. You can specify a file size of say (see Only for files smaller...) of 3 mb, that would rule out all video I suppose, or even smaller.

Dolphin (the KDE manager) has a whole section where ya can specify your preferences for previews on a lot of different filetypes.

Is there a particular reason why ya want to disable only some preview?

"Other previewable files" in Nautilus File Manager > Edit > Preferences > Preview Tab  includes pdf as well. I have a lot of pdfs whose size is smaller than 3 mb. When this function is enabled, then all the pdf files start showing previews and it takes some time to load all of them.

I want preview for image files only ( as a like browsing through my image albums). I know there are other photo manager softwares for it. But if this is possible under nautilus then it would have been a bit more useful.

---

### Post by starcraft.man on 2009-08-12
To my knowledge that's the extent of GNOMEs customize on previews. Perhaps there's some hidden options in gconf but I doubt it. Someone maybe could write a script to do this, maybe, I'm not the person though. As I said, Dolphin has a lot more options, GNOME's design focus is simplicity = less options. In addition, I've rarely had people ask to reduce the previews.

An alternative solution is simply to ensure that your images are sorted and stored in location x (like pictures folder) and make sure all your pdfs are in the documents folder. Then when you browse images you won't run across them, organization can never be underestimated. Hope that helps, all I got.

---

### Post by schmolch on 2009-08-24
All the thumbnailer commands are accessible in gconf-editor under  /desktop/gnome/thumbnailers.
There is a list of filetypes and which command gets executed to create these thumbnails.
If you only want to disable some existing thumbnails you can just go to that filetype and deselect "enable".

---

### Post by chitresh4u on 2009-08-24
> **schmolch said:**
> All the thumbnailer commands are accessible in gconf-editor under  /desktop/gnome/thumbnailers.
There is a list of filetypes and which command gets executed to create these thumbnails.
If you only want to disable some existing thumbnails you can just go to that filetype and deselect "enable".
Will check and report when I next login to Ubuntu.

---

### Post by chitresh4u on 2009-08-27
> **schmolch said:**
> All the thumbnailer commands are accessible in gconf-editor under  /desktop/gnome/thumbnailers.
There is a list of filetypes and which command gets executed to create these thumbnails.
If you only want to disable some existing thumbnails you can just go to that filetype and deselect "enable".
Yeah it works. 
You may first need to enable thumbnails in nautilus preferences (Preview tab) and clear exisiting thumbnails by deleting ~/.thumbnails or as explained [here]("http://ubuntuforums.org/showthread.php?t=633524").

---

### Post by chitresh4u on 2009-08-27
Now, is there any way to mark this thread SOLVED ??

Edit: Did it. Thread Tools->Mark this thread as solved.

---

### Post by pt123 on 2010-06-18
> **schmolch said:**
> All the thumbnailer commands are accessible in gconf-editor under  /desktop/gnome/thumbnailers.
There is a list of filetypes and which command gets executed to create these thumbnails.
If you only want to disable some existing thumbnails you can just go to that filetype and deselect "enable".

Thank you so much, HTML previews were crashing nautilus. Now I have them disabled.

---

### Post by nortexoid on 2011-04-16
> **schmolch said:**
> All the thumbnailer commands are accessible in gconf-editor under  /desktop/gnome/thumbnailers.
There is a list of filetypes and which command gets executed to create these thumbnails.
If you only want to disable some existing thumbnails you can just go to that filetype and deselect "enable".

Brilliant! I've been looking for this feature for ages! It's one of the main features I loved about Dolphin that Nautilus lacked.

---

