---
title: "nautilus-image-converter preferences"
date: 2011-05-13
forum: General Help
---

### Post by 73ckn797 on 2011-05-13
I have nautilus-image-converter installed for use in Nautilus. I resize several hundred images weekly with it. I would like to change the "image size" and "resize in place" as default preferences, different than what is the standard default. I have looked for a config file and looked in the Configuration Editor but find no options. I know that the nautilus-image-converter is part of Imagemagick but cannot find any info to make the changes.

Any recommendations?

---

### Post by jerrrys on 2011-05-16
i too use nautilus-image-converter.  and its just one of those no frill programs.  working with that many pics, you may want to consider another bulk converter.  Phatch? don't know, i didn't like it, but you may.

---

### Post by debd on 2011-05-16
I just wan to know does imagemagic has a PPA? i never found it in the repos.
or do i need to build it myself?

---

### Post by jerrrys on 2011-05-16
its there

[ATTACH]192337[/ATTACH]

---

### Post by mcduck on 2011-05-16
> **debd said:**
> I just wan to know does imagemagic has a PPA? i never found it in the repos.
or do i need to build it myself?

It's there, but you should keep in mind that it really *is* named "imagemagic**k**". ;)

Probably a reference to Crowley, who made a difference between magic and magick ("the Science and Art of causing Change to occur in conformity with Will").

What comes to the original question in the thread, nautilus-image-converter doesn't have any configuration file or gcnf optionsm, the settings are hard-coded. On the other hand based on it's simple functionality, the executable file is quite likely just a script so you could probably edit it yourself to change the settings. (I'm not sure about this, though, I've never checked if it's a script or a binary file, as I prefer using Imagemagick directly or by writing my own scripts)

(and by the way, it's *not* part of Imagemagick. It just uses Imagemagick to do the work.)

---

### Post by debd on 2011-05-16
thanks mcduck!
this spell difference feels rather like the the way English words are twisted and teased to form their American counterparts....which in the process confuse non-native English speaking people like me :)

---

### Post by 73ckn797 on 2011-05-17
> **mcduck said:**
> What comes to the original question in the thread, nautilus-image-converter doesn't have any configuration file or gcnf optionsm, the settings are hard-coded. On the other hand based on it's simple functionality, the executable file is quite likely just a script so you could probably edit it yourself to change the settings. (I'm not sure about this, though, I've never checked if it's a script or a binary file, as I prefer using Imagemagick directly or by writing my own scripts)

It really is not a game changer if I cannot default it to my preferences. The re-sizer does what I need. I may search around for a way to make the change but can just as easily keep using as is.

---

### Post by hwttdz on 2011-05-17
You can take a look in /usr/share/nautilus-image-converter.glade you can change the items in size_combobox.  And if you want to change the default you're going to need to get the source, and change nautilus-image-resizer.c line 391 to the option you want and rebuild.  I can't svn from where I am (maybe the port is blocked) and apt-get source complained about not being able to verify something, but it should be fine since it's actually in the repo.  
You could also make it in the width_spinbutton and/or height_spinbutton where apparently the first value is the default, but then you'd have to change the radio button every time.  I think the best way would be making your own imagemagick script for it.

---

### Post by Harix on 2011-05-31
I am also very interested in this topic. What I did so far is:

sudo gedit /usr/share/nautilus-image-converter/nautilus-image-resize.glade

Searched for ´resized´ and changed this to my wish...´new´. Saved the file and this changed the default.

Now I try to change the default 1280x960 into 800x600, but without success so far. In the middle of the file the different sizes are noted on the left, but how, what to change it into? Thanks.

---

### Post by mcdragon on 2013-02-12
The current version 0.3.1 seems slightly different compared to what was mentioned here.
There are two files under /usr/share/nautilus-image-converter
[LIST]
[*]nautilus-image-resize.ui
[*]nautilus-image-rotate.ui
[/LIST]
which seem to be QT designer files.
I have no idea on how to change settings in them. I would basically like the default rotate to be 180° and that the file would Rotate and Resize 'in place'

Any ideas?

---

