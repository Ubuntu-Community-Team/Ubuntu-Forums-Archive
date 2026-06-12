---
title: "Problem with tovid"
date: 2009-09-12
forum: General Help
---

### Post by causeitsme on 2009-09-12
I converted an .avi file with tovid and everything went well until the end. It gave me an error that there was a problem and I would be unable to burn the disk. Below is a copy of the last part of the log.

Note: the video name has been replace with *'s in the log below.

Running command: makexml -quiet -overwrite -dvd -menu "/tmp/Untitled_menu_1.mpg" "/tmp/*******.avi.tovid_encoded.mpg" -out "/tmp/Untitled_disc"
--------------------------------
makexml
A script to generate XML for authoring a VCD, SVCD, or DVD.
Part of the tovid suite, version 0.31
[http://www.tovid.org](http://www.tovid.org)
--------------------------------
Adding a titleset-level menu using file: /tmp/Untitled_menu_1.mpg
The file /tmp/*******.avi.tovid_encoded.mpg was not found.  Exiting.

The weird thing is that the file *******.avi.tovid_encoded.mpg does exist in the /tmp folder. Has anyone seen this happen before? Is there anyway I can still burn this to DVD and watch on my standalone DVD player?

---

### Post by stderr on 2009-09-12
I haven't tried tovid myself yet; devede seems to work fine for me. I like to create an ISO with it, and burn it with something like:

cdrecord -v file.iso
or right click the ISO & write to disc, or any other method.

I'd just re-encode the video myself using such a tool. As it stands, you haven't gotten a menu, etc.

---

### Post by causeitsme on 2009-09-13
> **stderr said:**
> I haven't tried tovid myself yet; devede seems to work fine for me. I like to create an ISO with it, and burn it with something like:

cdrecord -v file.iso
or right click the ISO & write to disc, or any other method.

I'd just re-encode the video myself using such a tool. As it stands, you haven't gotten a menu, etc.

Funny you mention devede, I've actually got a .iso of this video sitting in my /Videos folder from using devede. When I burned the .iso it left me with a 37 second long video of a background image with 'Title 1' written across it. Even though the .iso is over three GB in size. 

I really don't care which program I use but, I'd like to have something to work. 

Since I've already got the ~.avi.tovid_encoded.mpg and the Untitled_menu_1.mpg can't these be combined by some command via terminal and then burned?

---

### Post by stderr on 2009-09-13
Yes, that's the DVD menu it created automatically. You can customise that to your heart's content within the GUI, and even tick the box to tell it to go straight to title 1 without displaying the menu.

Alternatively, you could select the title 1 menu option ;)

You need a DVD structure to burn first (either in an image format like ISO, or a folder structure like you find under VIDEO_TS). I don't see how _just_ an mpg for the menu could produce a working DVD menu. I think tovid was interrupted too early on.

---

### Post by causeitsme on 2009-09-13
> **stderr said:**
> Yes, that's the DVD menu it created automatically. You can customise that to your heart's content within the GUI, and even tick the box to tell it to go straight to title 1 without displaying the menu.

Alternatively, you could select the title 1 menu option ;)

You need a DVD structure to burn first (either in an image format like ISO, or a folder structure like you find under VIDEO_TS). I don't see how _just_ an mpg for the menu could produce a working DVD menu. I think tovid was interrupted too early on.

OK, I see what you are saying about the title 1 thing. I tried putting it in the dvd player and got a 'can't read this disc' error. So I just walked myself through the devede process again and realized I had converted it with the PAL checkbox ticked. I guess that's why it won't read the disc on the dvd player but will show the title screen when opened with Movie Player on the computer. I'm gonna convert and burn it again using NTSC with devede and see if that'll do the trick.

Thanks for your replies. It'll be a while before I can get back to you to let you know if it works.

---

### Post by causeitsme on 2009-09-13
OK!! I got it. Devede did the trick. It was my mistake the first time I tried it and had it set to PAL instead of NTSC.

Sorry to gum up the works with something I'd overlooked.

Although I didn't find out what was up with tovid I do at least have a DVD I watch on my TV.

Thanks stderr!!

---

### Post by stderr on 2009-09-14
Ah yes, that's an easy mistake to make, I very nearly did that myself yesterday. :) No problem, glad it worked out for you!

---

