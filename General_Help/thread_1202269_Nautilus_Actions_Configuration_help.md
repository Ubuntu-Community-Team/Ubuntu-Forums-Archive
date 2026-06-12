---
title: "Nautilus Actions Configuration help"
date: 2009-07-02
forum: General Help
---

### Post by mike0020 on 2009-07-02
I'm trying to use Nautilus Actions Configuration to add a menu item for php files that will open terminal and have the command to run the script ready for me to run. For example, if I were to right click foo.php and select my custom menu item, I want terminal to open and have the first line look like this:

```
mike@mike-desktop:~$ php '/path/to/foo.php'
```

That way all I would have to do is press enter and it would run. When trying to do this through Nautilus Actions Configuration I get a segmentation fault error when trying to restart Nautilus and I'm not sure why. 

If anyone can help me correctly select the right options in Nautilus Actions Configuration for this I would be very grateful.

---

### Post by mthalis on 2009-07-02
Try > sudo php '/path/to/foo.php'

---

### Post by mike0020 on 2009-07-02
> **mthalis said:**
> Try

Where would I put that?

---

### Post by ricardisimo on 2009-08-17
I would greatly appreciate help with nautilus-actions as well. I'm hoping to add several ImageMagick functions to nautilus right-click. If someone could simply walk me through, for example, "Rotate image left 90°", I would be greatly appreciative, and will gladly post any other variations I can derive from that example.

I thank any kind souls in advance for taking pity on me.

---

### Post by Johnny B on 2009-08-17
nautilus-actions is easy if you know the terminal commands

[[IMG]http://img29.imageshack.us/img29/2393/screenshot1mca.th.png[/IMG]](http://img29.imageshack.us/i/screenshot1mca.png/)

(you have to log out and back in for changes to take effect)

---

### Post by Johnny B on 2009-08-17
convert original.jpg -rotate -90 new.jpg - Rotate the image to the left (anticlockwise)
convert original.jpg -rotate 90 new.jpg - Rotate the image to the right (clockwise) 

so it would be:
path: convert
paramaters: %f -rotate 90 %f_new.jpg

(%f instead of %m so you can select multiple files)

---

### Post by ricardisimo on 2009-08-17
Thanks for replying. I've got it to work, sort of... Couple of things:
[LIST=1]
[*]The commands won't do anything at all outside of /home/ricardisimo
[*]Why won't /usr/bin/mogrify work instead of "convert"?
[*]Under "Condition" > "Filenames" I put "*.jpg ; *.jpeg ; *.jpe ; *.gif ; *.bmp ; *.png ; *.tif ; *.tiff ; *.pbm ; *.pgm ; *.pnm ; *.ppm" and then under "Action" > "Parameters" I have "%f -rotate -90 %f"... works fine except for the first problem. The second "%f" may or may not even be necessary, and certainly not if I can get mogrify to work.
[*]What is "Profile 1", and why does it keep showing up? Why can't I just edit "Main"?
[/LIST]

---

### Post by Johnny B on 2009-08-17
im sure you could use mogrify or whatever you want, i was not aware of that command
if your using it outside your home directory, and need permission, you could just add gksu to the path

i have no idea why you cant edit main, thats weird

---

### Post by Post Monkeh on 2009-08-17
while we're dealing with people who know how to use nautilus actions, i'd appreciate it if someone could have a go at solving my little dilema.

[http://ubuntuforums.org/showthread.php?t=1228239](http://ubuntuforums.org/showthread.php?t=1228239)

---

### Post by ricardisimo on 2009-08-17
> **Johnny B said:**
> im sure you could use mogrify or whatever you want, i was not aware of that command
if your using it outside your home directory, and need permission, you could just add gksu to the path

i have no idea why you cant edit main, thats weird

I don't need sudo to mogrify files outside of home, so why would nautilus->mogrify need it?

When I say outside of /home/ricardisimo, I mean absolutely any folder other than my home folder, including subfolders of my home... As in, /home/ricardisimo/Pictures is off limits! Odd, don't you think?

I can edit Main, but I also have to edit "Profile 1" every time. Why is that?

I asked the folks at GetDeb to make the latest version of nautilus-actions available as a deb, and I'm hoping some of these quirky behaviors will mysteriously disappear with an update. We'll see.

Anyone have a foolproof version of this rotate action that I could copy in the meantime? Should I just keep tinkering with the basics that we have already mentioned here? Thanks.

---

