---
title: "Thumbnail Video Files, .avi .flv ect"
date: 2009-11-12
forum: General Help
---

### Post by nexoncore on 2009-11-12
How do you make it so all Media Files show thumbs rather than icons. I have checked the folder settings for preview and everything seems fine in there, even raised the file size limits.

I have VLC installed, and right now the media files are hit and miss with thumbs, most of the collection I have is .flv .avi and about 2% actually show the thumbs.

---

### Post by Minsky on 2009-11-12
Go into your **Home** folder and press **CTRL-H** to display the hidden files. You should see a folder called **.thumbnails**. Goto **.thumbnails>fail>gnome-thumbnail-factory** and delete everything in there. Your thumbnails should then reload and be displayed properly

---

### Post by nexoncore on 2009-11-12
Didnt work, it just generated thumbs for the ones which origionally worked, not the ones which didnt.

---

### Post by Minsky on 2009-11-12
I assume that you've set **Show thumbnails:** to **Always**, and **Only for files smaller than:** to **4GB**, in that case try logging out and then back in right after you've deleted the files and see if that works. If not, then make a backup of the **Fail** folder in **.thumbnails** and delete it (it should regenerate), and then check if the thumbnails have reloaded properly, this has worked for me in the past. Don't forget to use the **-R** flag if you're using the **cp** command to make the backup, so that the subfolder gets backed up as well.

---

### Post by nexoncore on 2009-11-12
Still not working

---

### Post by Minsky on 2009-11-12
I've got a couple of more things that we could try.

Make a backup of your **.thumbnails** folder, then open a terminal window and type:

```
rm -rf ~/.thumbnails

```

making sure that there isn't a space between the forward slash and full stop, then type:

```
killall nautilus
```

When nautilus is restarted, it will begin creating all the thumbnails again.

If your thumbnails are still not showing then type:

```
gconf-editor
```

and goto **desktop>gnome>thumbnailers**. Scroll down and you'll see a section of keys labelled **video@*file extension***. Click on each key and make sure that the **enable** box in the right hand pane has a tick/check mark in it.

If that doesn't work, then I think that it could be a codec issue.

---

### Post by Minsky on 2009-11-13
Just a thought, have you tried playing the files in Movie Player? If the above doesn't work, double click on one of the files so that they open up in MP and you may get a message pop up asking if it can search the internet for missing codecs. If so, accept all the suggested codecs and after they have finished loading, delete fhe **Fail** folder in **.thumbnails** again. If you get no joy with that, then I'm afraid its back to the drawing board.

---

### Post by 6205 on 2009-11-13
I'm not sure how thumbnail gerating works, but propably it's bounded only to Gstreamer. So if you use VLC or Mplayer and don't have installed all Gstreamer multimedia plugins, it will not work. But that's only my assumption..

You can try to install >

gstreamer-plugins-bad
                 -bad-multivers
                 -ugly
                 -ugly-multiverse
                 -ffmpeg
                 -pitfdll
                 -w32codec (available in medibuntu repository)

With these codecs is default Totem movie player able to play almost everything and thumbnail generation should work now.

---

### Post by Minsky on 2009-11-14
You could be right, it did cross my mind that it could be a missing gstreamer plugin. If Nexoncore opens a video file in MP, it should automatically search for any missing plugins.

---

### Post by nexoncore on 2009-11-16
I didn't consider that, but I don't have movie player since I stripped it out since I use VLC, I will test that now.

Its not completely solved the issue, but adding totem back has made the amount of files generating thumbs go from about 10% to about 90%. Guess I was a fool to remove totem.

---

### Post by budhi1976 on 2010-03-14
Thanks for the tips,

It works nicely for me. I just reinstall Karmic on my PC and realized that the thumbnails aren't loading, after I installed those plugins below and delete the files recommended by Minsky, now all my thumbnails load perfectly.


cheers,
> **6205 said:**
> I'm not sure how thumbnail gerating works, but propably it's bounded only to Gstreamer. So if you use VLC or Mplayer and don't have installed all Gstreamer multimedia plugins, it will not work. But that's only my assumption..

You can try to install >

gstreamer-plugins-bad
                 -bad-multivers
                 -ugly
                 -ugly-multiverse
                 -ffmpeg
                 -pitfdll
                 -w32codec (available in medibuntu repository)

With these codecs is default Totem movie player able to play almost everything and thumbnail generation should work now.

---

