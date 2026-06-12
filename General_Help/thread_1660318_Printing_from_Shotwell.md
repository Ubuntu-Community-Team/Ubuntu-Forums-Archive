---
title: "Printing from Shotwell"
date: 2011-01-05
forum: General Help
---

### Post by Ian Sinclair on 2011-01-05
At first sight, Shotwell looks good and I like the slideshow provision. I can print, but only one photo per page rather then 4 per A4 page (as I use on Flphoto). If I select a complete album, the Print menu item is greyed out. It seems to be a strange omission.

---

### Post by mike555 on 2011-01-05
You could use Gnome photo printer..

---

### Post by corncob on 2011-02-23
I was going to post my own thread but I'll just give this one a bump.  I tried printing (Canon MP640) pictures from Shotwell for the first time yesterday and it must have taken 5 minutes for the printer to start on each of them?  Is this the usual, does anybody know?  The printing starts almost immediately with Image Viewer.  I also noticed that it only prints one picture per page.  I guess I'll go back to just moving the pictures from the camera to the ~/Pictures/ directory.  I just expected Shotwell to do better.

---

### Post by yorbaclint on 2011-03-29
Hi all,

First off, thanks for trying out Shotwell! It's encouraging to see someone using something we've made.

As of 0.9, it's possible to print more than one image per page; to do this:

[LIST=1]
[*]In any area of the application where it's possible to highlight multiple images, do so.
[*]Choose **File -> Print**....
[*]In the printing dialog, choose **Image Settings**.
[*]Choose **Autosize**, and in the drop-down menu, choose one of the multiple-images-per-page options.
[/LIST]
You can get 0.9 from our [PPA]("https://launchpad.net/ubuntu/+source/shotwell"), or you can get the source from our SVN repository at svn://svn.yorba.org/trunk/shotwell .

---

### Post by gazzatav on 2011-09-24
I'm trying to make the move from F-spot to Shotwell as F-spot is broken in Ubuntu 11.04 and crashes when I try to print.  However the print options in Shotwell leave a lot to be desired:-

Many retailers sell so-called 4x6in photo paper which is really 100x150mm - not the same!  I had successfully set up my own postscript printer definition file to be able to print full bleed on 100x150mm paper.  This used to work perfectly on F-spot.  When I try to print using Shotwell the options are either too limiting or the wrong assumptions are made about the paper in 'Autosize fill the entire page' and the printer rejects the print with the message 'paper mismatch'.

At the moment I don't know whether to spend the time getting F-spot to work or try later versions of Shotwell or go back to Ubuntu 9.04.

---

### Post by corncob on 2011-09-25
Ubuntu 9.04 must be nearing the end of its supported life.  I went back to 10.04 LTS because that will be good to 2013.

---

### Post by gazzatav on 2011-09-25
Silly me, yes I meant 10.04.  In the meantime I have found a work around for Shotwell.  It seems the autosize option still needs you to calculate and enter the resolution.  After a bit of experimentation I'm starting to get passable full bleed pictures though the edges have more chopped off than I would like.

---

