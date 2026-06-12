---
title: "picture editor like irfan ?"
date: 2011-09-28
forum: General Help
---

### Post by ottosykora on 2011-09-28
I would like to have some simple fast picture editing tool like irfanview under windows.

Irfan seems not to exist for linux, gimp would do it all, but this is not I am looking for, gimp is too complex for that.

Need something simple, copy a pic somewhere from, can be also in browser, paste it into some program and can make simple operations like cut parts of it or so.

Any idea?

---

### Post by yetiman64 on 2011-09-28
I have used irfanview under Windows in the past, although I can't tell you of a single editor under Linux that will match it function for function, most if not all of its functions can be done in Linux with a few different programs/techniques.

For very simple image editing and thumbnail viewing I use **gthumb**, see the attached image for the edit menu in gthumb (In Natty). For more advanced editing I switch to **gimp**, this can be done easily from within gthumb by right clicking on the opened image, select "open with" then select "gimp".

For batch image resizing I use the **imagemagick** package and some of its commands in the terminal, **mogrify** in particular for batch resizing. When I was using Nautilus (I am currently using Thunar and pcmanfm file managers) it was possible to batch rename images with a script (**nautilus renamer**).

These methods have allowed me to switch my image editing needs over to Linux fully. There is a python based program (not in the repos afaik) I tried out a while back that would go close but I found it unintuitive and a bit hard to use. Unfortunately I can't recall the name of it, if I remember it/find it again, I'll edit this post with the info.

Cheers from yetiman64

---

### Post by coldraven on 2011-09-28
Have a look at Pinta 
[http://pinta-project.com/](http://pinta-project.com/)

---

### Post by lookitseman on 2011-10-11
Holy cox, I didn't even know gthumb had the ability to edit images.  This is exactly what I was looking for, thank you!

---

### Post by Barney-R on 2011-10-20
Thanks you YetiMan64. You've solved half of a problem of mine. I've installed gthumb, which has enabled me to resize an image, but is there an easy way of adding a white panel with text to a .jpg?[CENTER][LEFT]_I'll explain as briefly as I can, but first, how do I stop this panel underlining everything I type? I've tried Ctrl+U, and I've also tried clicking on the "Underline" icon, but nothing works._

Funny. It was just that one paragraph that was underlined. To explain though. My computer may be going in for repair and perhaps a few improvements and, being a bit paranoid, I've removed most of my personal files and (I hope) overwritten them by creating and then deleting a very large TrueCrypt file.

The work will all be hardware-related, so no more than minimal access will be needed to the operating system. I've created a temporary user account with auto-log-in and limited privileges, but want to use a .jpg image as wallpaper.

I now want to add a small white panel, overlaid on the wallpaper image, showing the temporary password for this account in case it's needed. I've tried gimp, but couldn't make sense of it or get it to do what I wanted.

Please remember I'm still a comparative newbie, only having been using Ubuntu (10.10, 64-bit) since March or April this year.

Using $eattle $pyware and "Paint", the job would take a couple of minutes at most, but this purpose-built machine has been Linux-only from new, and I intend to keep it that way.

Any suggestions welcome.

[/LEFT]
[/CENTER]

---

### Post by yetiman64 on 2011-12-01
> **Barney-R said:**
> ... I've installed gthumb, which has enabled me to resize an image, but is there an easy way of adding a white panel with text to a .jpg?..

Firstly, sorry for the late reply, I've been away from internet access for the last 6 weeks or so.
That job is one I would switch to gimp to complete, the toolbar in gimp has both a "text box" tool and if needed a "bucket fill" tool for colouring the box white (may be needed if the background is a transparency).

Hope that helps for the text in a jpg aspect of your post, cheers from yetiman64

---

### Post by Barney-R on 2011-12-02
Thanks for that YetiMan64, and now it's my turn to apologise for the late reply. My main computer's been away being fixed, and I forgot to copy my log-in details to the spare machine.

I've done what I wanted to do, with your help. Thanks again.

---

### Post by marko on 2012-07-10
just wanted to give you props on the referral to 2 excellent alternatives - gthumb and mogrify.  short of some odd features (like rotating images by degree, and simple panoramas), i am wine free!  ;)

two quick things i'll share:

- highlighting multiple images with gthumb, use F2 - %D{%y%m-%d%H%M%S}%E to rename by date

- mogrify -resize 1280x1280 *.jpg to make long edge one size, no matter the rotation

---

