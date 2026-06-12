---
title: "Problem importing images to Shotwell and F-spot"
date: 2012-02-13
forum: General Help
---

### Post by nickdc on 2012-02-13
I'm trying to troubleshoot a problem my partner's just encountered (having persuaded her finally to try Ubuntu!) while organising her photos using Shotwell (v. 0.5.0 on Ubuntu 10.04). She's successfully imported hundreds of images from her camera cards and hard drive over the last few days. Then she captured some stills from some video she'd been working on in Kdenlive, saved as png files in a folder, but when she tries to import them into Shotwell the icons are all greyed out. Opening the folder in the file browser and dragging and dropping any of the images produces a message: "Import complete. 1 unsupported photo skipped", followed by the full path (and nothing unusual there, eg no &). The same happens with F-spot. The files themselves seem fine. They open with Image Viewer; though a weird thing is that if I click on the edit-with-Fspot icon in Image Viewer, the F-spot editor opens fine and I can edit and re-save them with a changed name, but then they still won't import to F-spot or Shotwell. All the icons are greyed out, including the ones for images just opened in the F-spot editor and re-saved. I've done some searching but found nothing that matches this particular problem. Any suggestions anyone?

---

### Post by eric-yorba on 2012-02-13
Shotwell added PNG support in 0.6.1.  Why are you running such an ancient version?

---

### Post by nickdc on 2012-02-13
Thanks for responding. First, it's not just the png files that are causing a problem: we've tried converting them to jpeg but it makes no difference. We're running that version because that's the one in the repositories for Ununtu 10.04. We're running 10.04 after a lot of trial, error and research to get Kdenlive working properly with firewire video capture.

---

### Post by eric-yorba on 2012-02-13
Do other JPEGs work?  What program are you using to do the conversion?

Also, there's at least one PPA that includes Shotwell 0.11 for Lucid.  I can't vouch for it as we don't support this configuration, but it might we worth trying (be sure to backup your Shotwell library first!)
[http://www.omgubuntu.co.uk/2011/08/shotwell-0-11-lucid-users/](http://www.omgubuntu.co.uk/2011/08/shotwell-0-11-lucid-users/)

---

### Post by nickdc on 2012-02-13
Yes, most of the images we've imported are jpegs. My partner used Gimp to convert, and I used F-Shot as explained above. Thanks for the link; I'll give it a try tomorrrow.

---

### Post by serpicojam on 2012-04-29
Have you found a solution for this? I'm using Xubuntu, and since my upgrade to 12.04 I'm having the same issue with both F-Spot and Shotwell. Thanks!

---

### Post by eric-yorba on 2012-05-01
Doesn't sound like the same problem, unless you're (somehow) running Shotwell 0.6 on 12.04...

---

