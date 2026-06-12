---
title: "ID3v2 editor for MP3s?"
date: 2006-03-25
forum: General Help
---

### Post by bluemax on 2006-03-25
It seems like every audio app on Linux only supports ID3v1 tag editing. This is very annoying, because when I edit the ID3 tags of an MP3, I want to edit both versions so they look the same, or sometimes I just want to remove all the tag info, which I cannot do.

So, I noticed there are a couple command-line ID3 editors but that seems too cumbersome and tedious. What I want to know is, are there any graphical ID3v2 editing tools out there? Whether it's part of an audio app or standalone I don't care, I just want to be able to edit *both* tags!

---

### Post by John.Michael.Kane on 2006-03-25
[http://www.linux.org/apps/AppId_1716.html](http://www.linux.org/apps/AppId_1716.html)
[http://openfacts.berlios.de/index-en.phtml?title=Linux_MP3_HOWTO/ID3_Editing](http://openfacts.berlios.de/index-en.phtml?title=Linux_MP3_HOWTO/ID3_Editing).
[http://id3lib.sourceforge.net/](http://id3lib.sourceforge.net/)
[http://www.audiott.com/](http://www.audiott.com/)
[http://linux.softpedia.com/get/Multimedia/Audio/PGID3-Tag-Editor-8982.shtml](http://linux.softpedia.com/get/Multimedia/Audio/PGID3-Tag-Editor-8982.shtml)
[http://www.faqs.org/docs/Linux-HOWTO/MP3-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/MP3-HOWTO.html)
[http://www.vorbis.com/software/#linux](http://www.vorbis.com/software/#linux)


Hope this helps.

---

### Post by Matt Yun on 2006-03-25
Try [EasyTag]("http://freshmeat.net/projects/easytag/"); it has support for both ID3v1 and v2.  

You should add the Penguin Liberation Front multimedia repository to your /etc/apt/sources.list (either edit the file or do it from Synaptic):

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

Then do "sudo apt-get update && sudo apt-get install easytag", or search for easytag in the "Add Application" menu.

---

