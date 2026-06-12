---
title: "Cannot change the 'Title' of mp3 file"
date: 2010-05-15
forum: General Help
---

### Post by petru.marginean on 2010-05-15
Hi,

I changed the 'Title' of a mp3 file using mp3info:
```
$> mp3info -t Hello Track30.mp3

$> mp3info Track30.mp3
File: Track30.mp3
Title:   Hello                          Track: 
Artist:  
Album:                                  Year:  
Comment:                                Genre:  [255]

$> mp3info -h
MP3Info 0.8.5a Copyright (C) 2006 Cedric Tefft and Ricardo Cerqueira

```However Nautilus shows different Title for the same very file:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=157075&stc=1&d=1273964056[/IMG]

Where comes this "Title" that Nautilus displays?
How can I change it?

Regards,
Petru

---

### Post by angry_johnnie on 2010-05-15
ever tried easytag?

it's in the repository.
i know from experience it does the job.

---

### Post by Spr0k3t on 2010-05-15
If you need to process a large batch of files, check out Ex Falso.  Also something to note, there are different versions of ID3 tags.  Version 1 has a very small set of information which can be set.  Version 2 (currently on release 4 of the V2 diatribe) removes much of the limitations of the length restrictions found in V1.  Then there's the super propriatary component which is not ID3 but backwards compatible due to the outrageous number of additional tags that are hardly ever used.  Of course the super propriatary closed source blackbox tagging is a compilation of collective idiots from Microsoft and iTunes (not apple)... but we'll lump apple in there with the collective idiots because that's just what I do.

---

### Post by demosthenese on 2010-05-15
Just to expand on sprocket's reply. There are different versions of the mp3 tags, and more than one version of the tags can be stored in the mp3 files header. Different programs will handle this differently - so one will display the tag from one version while another will choose another - leading to the different displays you are seeing from the same file.

Ex-falso is ok for editing tags - I use its sister app Quod Libet for playing mp3 files.

However my favourite tag editor is the windows program mp3tag - which is free if not open - and works fine with wine. It will tell you which version of tags are in your headers and allow you to choose which version(s) to write.

---

### Post by petru.marginean on 2010-05-15
Thanks everyone for replies.

I liked mp3info because it was command line, so I can do scripting.
Probably the issues I have is related to the different versions of the tags...

I used easytag, and it worked fine. 

Petru

---

