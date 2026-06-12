---
title: "How to Hide Root/Image Type in File Name in the File Browser"
date: 2009-10-08
forum: General Help
---

### Post by dbsalter on 2009-10-08
Hey all,

I'm basically an Ubuntu rookie, having just switched over (happily) from Window Virus (I mean Vista) a week ago. I've been mostly very happy, but have been looking for an answer to one question for an hour now and can't find one so I'm asking here.

In the file browser (I've looked at Dolphin, Kompressor, Open File, they all seem the same to me), I have pretty much toggled the view to my liking, except that the file names still show the ".jpg" or ".wmv" or whatever. I already have a column for file "Type," and I was hoping there was a way that in the file browser instead of looking at a bunch of "[FileName].jpg" or [Name].mpg" I could make it so the file name alone appeared, e.g. "FileName." When I went in to change the file name by removing ".jpg" from it, it changed the actual file type. I used to be able to do that in Windows without actually changing the file type.

Is there a way I can change the view options in a file browser to just display file names without the ".suchandsuch" or is this just an Ubuntu thing I'm going to have to get used to?

Thanks in advance!

---

### Post by Lars Noodén on 2009-10-09
I looked quickly at dolphin and thunar.  Neither appear to let you truncate the file names.  Keep in mind that the [file type](http://www.iana.org/assignments/media-types/) is **not** dependent on any part of the file name.  You can have an MP3 file named 'music.mp3', 'music.jpeg' or just plain 'music' even though that might be misleading or confusing.

Two of the criticisms with Windows is that it uses the file name to assume the file type and that some of the viewers truncate part of the file name causing users to miss errors.  So it would be surprising if modern systems repeat this design mistake, however familiar it may be to some.  ;)

In dolphin, you can turn off showing the file type this way:

[INDENT][FONT="Courier New"]View-> Adjust View Properties -> Additional Information -> Type[/FONT][/INDENT]

but that will still leave you with the full name of the file.

---

