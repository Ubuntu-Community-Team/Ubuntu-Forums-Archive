---
title: "Non-linear video Editor that actually works?"
date: 2006-06-21
forum: General Help
---

### Post by CyberAngel on 2006-06-21
I need to edit some videos (add transition effects, more sounds in some points of the clip, delete sounds in certain points of the clip etc)
The options I have seen so far are cinelerra, kino and kdenlive but none of them actually works...

Kino and kdenlive can`t even load my video files (xvid files or mpeg2 converted by avidemux) and cinelerra (install used the x86_64 rpm package from the official site using alien) load the files but I cannot edit them at all. It crashes so easily and the half of the things doesn`t work as it should work (At least as I have read from some tutorials that should work).
Any program that actually works like Adobe Premiere????

Thanks in advance!

---

### Post by risbac on 2006-06-21
One of the most promising projects is Diva. But as it says, it's a project. You can't do so many things with the current version of the soft. But you can check it out for the future:

[www.diva-project.org](www.diva-project.org)

---

### Post by fsman on 2006-06-21
Cinelerra is IMO most list Premiere.

That said, doing any editing using Xvid(MPEG4) or MPEG2 isn't a good idea. They aren't designed for NLE (B/P frames etc).

In an ideal world your source material should be either MJPEG or DV codec - the container should be quicktime for Cinerlerra. I think you will find great stability in cinelerra from that point on.

Lots of guides linked from [http://cvs.cinelerra.org/docs.php](http://cvs.cinelerra.org/docs.php)

---

### Post by siriusnova on 2006-06-21
I use MainActor, it's not free but then free NLE's really suck at the moment..

i like it.

edit - [http://www.mainconcept.com/site/?id=954](http://www.mainconcept.com/site/?id=954)

Oh and also you can download the "trial" version, the only difference between that and the regular version is that it needs a key which you can buy from MainActor. The Trial Version is fully functional and just watermarks your video so you can play around with it.

---

### Post by CyberAngel on 2006-06-21
I tried again to load on cinelerra the mpeg2 files and it seems to work better than the xvid files....

I tried MainActor too but I get a few segmentation faults sometimes....

Anyway thanks... I will try mostly those two progs and we`ll see..

---

### Post by dolson on 2006-07-02
There's another one called Pitivi but it doesn't do a hell of a lot at the moment. I'm very discouraged at this, but I wouldn't even know where to start on coding my own or contributing to one.

This is unfortunate... We really need a good video editor.

---

### Post by claydoh on 2006-07-02
I would suggest trying out[ LiVES]("http://lives.sourceforge.net/")
It has a good feature set, it may be able to do what you are looking for.
There is an [Ubuntu repository available]("http://lives.sourceforge.net/index.php?do=downloads"), as well, scroll way down near the bottom for the info

---

### Post by CyberAngel on 2006-07-03
[QUOTE=dolson]There's another one called Pitivi but it doesn't do a hell of a lot at the moment. I'm very discouraged at this, but I wouldn't even know where to start on coding my own or contributing to one.

This is unfortunate... We really need a good video editor.[/QUOTE]

I tried that pitivi and it is veeeeeeeeeeeeeryyyy very buggy at the moment.

[QUOTE=claydoh]I would suggest trying out LiVES
It has a good feature set, it may be able to do what you are looking for.
There is an Ubuntu repository available, as well, scroll way down near the bottom for the info[/QUOTE]

The package is for i386 and I am using amd64 so I cannot use it :(
I tried to compile LiVES from source but no luck :(

The best one that I found so far is MainActor that it is commercial but even this one crashes when I am going to add some titles on my video :(

---

### Post by fsman on 2006-07-04
a suggestion for successful video editing.

Firstly, your source material should use a format and codec that lends itself well for NLE. Xvid and Mpeg2 at not good formats for video editing - which may be why you are having problems.

The trick is to capture using a container (e.g. quicktime or dv) and a codec (MPJEG or DV) that are designed for video editing. If you use containers such as avi or codecs such as mpeg2/4 you will almost certainly have problems. To learn about codecs have a look at the doom9 website.

If your source material is DV. then use kino to capture (remember to set the container to quicktime). Then edit the video using kino or for powerfull features use cinelerra.

If your source material is via a capture card use mpjegtool's LAVREC command to capture the material in MJPEG format - google for more info. Now is this case you need to edit using cinelerra (kino only supports DV material).

A good intro site is [http://www.robfisher.net/video/](http://www.robfisher.net/video/)

finally, if using kino - use the export function to save the project as mpeg2 (DVD) or xvid. For cinelerra is prefer to output the final video in the same format as the source (dv or mjpeg) and then use avidemux to convert to mpeg2 or xvid.

Hope this helps.

---

### Post by theToolman on 2006-07-07
I got kino working in dapper by switching to quicktime codec; any other seemed to crash on record..

I just had to chmod user:user /dev/raw1394

---

### Post by cleentrax on 2006-07-08
> **dolson said:**
> There's another one called Pitivi but it doesn't do a hell of a lot at the moment. I'm very discouraged at this, but I wouldn't even know where to start on coding my own or contributing to one.

This is unfortunate... We really need a good video editor.

Well, we need a good image editor, and a good GUI web design app, and a good audio composition app... There are very few mature professional Linux apps at the moment. But they will come. Meanwhile, I'm dual-booting.

---

### Post by danielph on 2006-09-16
> **cleentrax said:**
> Well, we need a good image editor, and a good GUI web design app, and a good audio composition app... There are very few mature professional Linux apps at the moment. But they will come. Meanwhile, I'm dual-booting.
Have you given GIMP a fair trail for image editing?
Web design - Bluefish, Screem, Quanta or NVU. The last 2 are  WYSISWYG

With regards to video editing I think Cinelerra seems have the most features, but I would like to see a little more stability.

---

