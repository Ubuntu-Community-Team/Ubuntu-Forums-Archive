---
title: "Photo Printing Software??"
date: 2010-09-30
forum: General Help
---

### Post by gallifrey on 2010-09-30
Hello, 
        simple question really. Can anyone recommend some decent photo printing software. I have tried Gnome Photo Printer and PhotoPrint. 
Photoprint would be perfect, but for some reason doesn't like my printer. 
Gnome Photo Printer doesn't give me the control I need over layout, or resolution, paper type, etc. 
Shotwell and Gthumb don't seem to have the facility to print multiple photos in one go on a single sheet. So I am kind of stuck. 

Does anyone have any suggestions or ideas??

---

### Post by davidmohammed on 2010-09-30
[Picasa]("http://www.ubuntugeek.com/howto-install-picasa-3-5-in-ubuntu.html") I find is the best - even though its a wine app, it works just find in linux.

---

### Post by sikander3786 on 2010-09-30
F-Spot has also got the printing abilities.

---

### Post by onaridge on 2010-12-02
I had the same problem in Gnome, no control over printer properties which is a shame as I like the set up options for the prints. Where in Fstop is the setting for the printer properties found? I looked there first and couldn't find anything.

---

### Post by mjc1 on 2010-12-23
> **gallifrey said:**
> Shotwell and Gthumb don't seem to have the facility to print multiple photos in one go on a single sheet.

gThumb can, in fact, print multiple photos on a single page.

- Mike

---

### Post by onaridge on 2010-12-23
mjc1 I downloaded Gthumb and cannot print at all. When I click on print nothing happens and I can't even find anything in the manual on printing. Please help? It looks like a viewer only.

---

### Post by yorbaclint on 2011-03-29
Hi,

If you'd like to give Shotwell another go, 0.9 now supports printing more than one image per page.  To do this:

[LIST=1]
[*]In any area of the application where it's possible to highlight multiple images, do so.
[*]Choose **File -> Print**....
[*]In the printing dialog, choose **Image Settings**.
[*]Choose **Autosize**, and in the drop-down menu, choose one of the multiple-images-per-page options.
[/LIST]
Version 0.9 is available from the Shotwell [PPA]("https://launchpad.net/ubuntu/+source/shotwell"), or you can get the source from our SVN repository at svn://svn.yorba.org/trunk/shotwell .

---

### Post by onaridge on 2011-04-23
Yorba, I would love to try that version but here is my problem. In order to install the latest Shotwell I need Vala version 0.11.7 and the only vala I found and installed was version 0.10. I am stumped. Can't find that version anywhere and that's the version the terminal tells me I need (Shotwell requires Vala compiler 0.11.7 or greater.  You are running 0.10.4.)

---

### Post by eric-yorba on 2011-04-26
> **onaridge said:**
> Yorba, I would love to try that version but here is my problem. In order to install the latest Shotwell I need Vala version 0.11.7 and the only vala I found and installed was version 0.10. I am stumped. Can't find that version anywhere and that's the version the terminal tells me I need (Shotwell requires Vala compiler 0.11.7 or greater.  You are running 0.10.4.)
You only need Vala if you're installing from source.  You can grab Vala version 0.12 from the vala-team PPA:
[https://launchpad.net/~vala-team/+archive/ppa]("https://launchpad.net/%7Evala-team/+archive/ppa")

---

### Post by bstjon on 2011-09-27
hi folks, i too am trying to print multiple photos per page, have Shotwell 0.9.3 but when I go to print --> image settings --> autosize and select 8 images per page, still only prints one image per page.  Though the one image is the proper size.  any ideas?

---

