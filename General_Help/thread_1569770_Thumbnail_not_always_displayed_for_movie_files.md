---
title: "Thumbnail not always displayed for movie files"
date: 2010-09-07
forum: General Help
---

### Post by Christian Knudsen on 2010-09-07
I've got a fairly small problem that still annoys me a bit. When I download some movie files (mpegs), the preview thumbnail isn't always shown (see attached screenshot).

I can't figure out why it won't show the preview image for some files. It doesn't seem to have anything to do with the size of the file, as both smaller and bigger files get their preview shown, and all the files are mpegs, so it has nothing to do with file type...

---

### Post by Ginsu543 on 2010-09-08
That one file may not have a thumbnail because its size is over the limit set in Nautilus for making thumbnails. To check, open Nautilus and go to Edit --> Preferences --> Preview. Go to the options under "Other Previewable Files". I believe the default setting for "Only for files smaller than" is 10 MB. Change it to a bigger value (I always set it to the 4 GB max). See if a thumbnail is generated for your file in question.

What you might also want to try is to clean out your thumbnail cache and force Nautilus to regenerate the thumbnails. To do this, go to your /home/<user name> folder and delete the contents of the .thumbnail folder. It's a hidden folder (notice the "." in front of the name), so you may have to hit Ctrl+H to see it.

---

### Post by papibe on 2010-09-08
I'm not pretty sure that that Nautilus's setting works as intended, since most all of my movies are far > 10Mb and are thumbnailed by Nautilus.

In my case, only the movies whose codec are not installed are not able to be thumbnailed.

If Ginsu543's tip doesn't solve your problem. you may try to double click the movie (so it's open by the default app - probably Totem). If you aren't able to see the movie, you may follow the Totem's suggestion to search for a suitable plugin.

Good Luck!

---

### Post by Christian Knudsen on 2010-09-08
The other files with previews are both smaller and bigger than the one that doesn't have a preview. And they're all the same format (mpeg). It's probably just Nautilus acting up...

I'll try to set "Only for files smaller than" to 4GB and see if this helps in the future.

EDIT: I have very old thumbnails in the .thumbnail folder from files that have been deleted long ago. Aren't the thumbnails automatically deleted when the file is?

---

### Post by papibe on 2010-09-08
Having similar problems, I continued researching on this issue. These are my findings:

Gnome (Nautilus) uses an thumbnailer application to produce thumbs. The defualt Gnome thumbnailer for video is totem-video-thumbnailer. Check this:
```
$ man totem-video-thumbnailer 
```

There are several thumbnailer apps that can be installed to embellish the navigation on Nautilus. Go to the Software Center and search for "thumbnailer".

There is a way to manually add a new thumbnailer app by following these instructions:

[INDENT][Installing a Thumbnailer Program]("http://library.gnome.org/devel/integration-guide/stable/thumbnailer.html.en")[/INDENT]

It seems that the best candidate (or replacement) for mpeg files would be: ffmpegthumbnailer (available at Software Center). In the project home page there is more info on how to do this:

[INDENT][How can I use ffmpegthumbnailer in Nautilus?]("http://code.google.com/p/ffmpegthumbnailer/wiki/Faq")[/INDENT]

I haven't tried yet, but if anyone do, please report back here.

Regards.

---

### Post by Mayki8513 on 2010-09-23
> **Christian Knudsen said:**
> I've got a fairly small problem that still annoys me a bit. When I download some movie files (mpegs), the preview thumbnail isn't always shown (see attached screenshot).

I can't figure out why it won't show the preview image for some files. It doesn't seem to have anything to do with the size of the file, as both smaller and bigger files get their preview shown, and all the files are mpegs, so it has nothing to do with file type...

the only thing with file type is if you can play it in totem or not,
obviously, it won't create thumbnails for files it can't play,
I was actually very irritated at this today,
but I found this out:
thumbnails are stored in ~/.thumbnails
if you cd to that directory,
you will see 2 folders.
fail + normal.
good thumbnails are saved in normal,
failed, obviously in failed.
so after having this same issue and spending a couple hours mad at my computer,
I finally came across a few threads that helped a little,
if you delete the "fail" folder,
nautilus will reattempt to create the thumbnails,
if it fails however,
it will be saved in fail again,
you can keep deleting the folder and refreshing,
but that's annoying,
here's what I did:
in "fail" there is another folder,
"gnome-thumbnail-factory"
that's where the thumbnails are saved,
in there,
so...
I changed the permissions of that folder to 000 so NOTHING can be saved in it :P
because nautilus can no longer save the thumbnail,
it keeps re-attempting,
until of course it finally makes a good thumbnail,
then it will be saved in "normal"
and you won't have to worry about it,
I don't think this is the best way of fixing it,
but it worked for me :D
it did take some files almost a minute to create the thumbnail,
but hey,
once it's made you don't have to worry about it right?
also,
if you do come across a file that just won't make one for some reason,
you can easily assign one yourself by right clicking -> properties,
and clicking on the thumbnail button,
so if you do have a file like that,
just take a snapshot of a movie frame and assign that ;)

---

