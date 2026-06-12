---
title: "Changing video formats by changing the extension?"
date: 2010-01-17
forum: General Help
---

### Post by webcabbie on 2010-01-17
If a file ends .flv or .avi and I change it to .mp4 does it really change it to mp4 or is it some kind of... I dont even know.. 

There are tons of software packages to convert video files. They must be needed right? Its really not as easy as changing the file extension right?

---

### Post by ImperialXT on 2010-01-17
Changing the file extension does not change the format of the video. Though it requires a bit of fidling if you want to re-encode it to mp4 you should look at mencoder 'man mencoder'

---

### Post by webcabbie on 2010-01-18
So then how come when I change the file extension the computer and other computers now think its an .mp4?

Does it work well enough that I could change .avi files to .mp4 files by the extension so they will play in a ps3?

---

### Post by audiomick on 2010-01-18
If that works, it is pure luck.

If you change the extension, a player will open and assume it is the other format, but it isn't.

What you are talking about is a bit like putting your cornflakes in a wheetbix box. It might look like wheetbix, but there are still cornflakes inside.;)

---

### Post by shreepads on 2010-01-18
> **webcabbie said:**
> If a file ends .flv or .avi and I change it to .mp4 does it really change it to mp4 or is it some kind of... I dont even know.. 

There are tons of software packages to convert video files. They must be needed right? Its really not as easy as changing the file extension right?

Yes you need an application to change a video format. Try Kino, works for me (though after adding some codecs).

Renaming doesn't change the video format. An intelligent player will not go by just the file extension but will also look inside the file contents to determine the video format. If it can handle it great else will return an error.

---

### Post by mcduck on 2010-01-18
> **webcabbie said:**
> So then how come when I change the file extension the computer and other computers now think its an .mp4?

Does it work well enough that I could change .avi files to .mp4 files by the extension so they will play in a ps3?

The point here is that both .avi and .mp4 are containers, not file formats.

So if you have an avi file that includes, say, video encoded into h.264 format, it's relatively simple job to just change the container format to .mp4. For some players just changing the name might be enough, although that really doesn't change anything in the file itself).(Although not as simple as just changing the file name extension :D)

However actually converting the video itself from one format to another (not just from one container to another) always requires re-encoding the video. One thing doesn't change to something completely other just by changing the file name. If you write a text n Office and rename the file into .jpg it doesn't suddenly become an image. Exactly the same thing with video formats.

Also note that many hardware (and also operating systems like Windows) detect files based on file names. So renaming a file to something else makes it seem like other type of file, while it really isn't. You just end with a file that doesn't work.

(What comes to PS3, it supports both .avi and .mp4 containers. It's just a question if the video & audio you have in those containers is in supported format)

---

