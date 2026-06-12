---
title: "Ugly Solution to Photo Printing Problems"
date: 2006-04-23
forum: General Help
---

### Post by robglinka on 2006-04-23
Hey all, long time listener, first time caller... Sorry about the length, I get wordy.

  I am having a bit of trouble with photo printing, I designed a solution, but it is ugly and not ideal. I was hoping that someone might be able to give me some tips, and if not, maybe other people can use my solution.

  **Specs:**
    Dapper Drake Flight 6
    gnome
    nautilus file manager
    HP Photosmart 7960 (but this solution will work with any USB printer that has an on-screen way to print pictures from flash cards)

  **Problem:**
    My HP printer has a 4x6 photo tray designed to print 4x6 borderless photos.    
    gThumb won't print on anything but 8.5x11 (or preinstalled paper sizes like A4)
    GIMP always wants to add margins to anything I print.

  **Solution:**
    Add a 32mb compact flash card that permenently lives in the printer's card slot.
    Create a nautilus script that gives me a right-click menu to put jpgs onto printer card. (the flash card mounts as write only by root, so I can't just drag and drop)
    Pull card out of printer for a second, then reinsert.
    Print from printer's on screen menu.

 As you can see, this isn't a pretty solution, but it works 100% of the time, and it gives perfect print-outs.

 Here's a copy of my nautilus-script. The printer mounts as "/mount/usbdisk". I also have a nautilus-script to delete the pictures that I have already printed, and ones to mount and unmount the disk. (I got a little script happy).

```

#!/bin/sh
# Stolen from the interweb and edited for my needs by Rob G.
# Copy To Printer:  copies the selected file(s) to printer CF Card
# (if able)

DIR="/media/usbdisk"

for arg 
do
   # test if the print directory exists
   # if [! -d /media/usbdisk/dcim/ ]
   #  then
   #    gksudo mkdir /media/usbdisk/dcim/
   #  fi
   # test is object already exists
   if [ -f "$DIR"/"$arg" ];    then
      MSG="File: '$arg' already exists. Overwrite?"
      if    
         gdialog --title "Overwrite?" --defaultno --yesno "$MSG" 200 100 
      
      then
        # overwrite object
        gksudo cp "$arg" "$DIR"/"$arg"
      fi
   else
     # create object
     gksudo cp "$arg" "$DIR"/"$arg"
   fi

done

```

-Rob

---

### Post by dantum on 2006-05-10
Long time listener and second time caller here.

I too have the same issue with my HP 8450 printer. I think yours is very similar and has that card reader built in. I was unable to print anything but A4 size paper which came out flawlessly.

Unfortunately, i'm a bit of a photography enthusiast and really need that photo tray working as well as being able to print 13x18 cm paper from the main tray. Whatever i do with setting, the error message comes up saying the output is larget than paper size.

I know i can stick pics on my card and print them by using the printer settings directly but that is really not what i need. 

Would be nice to hear from more people. 

Dan

---

### Post by king20878 on 2006-06-07
Hi,

I just recently got photo printing working flawlessly with an HP PSC 2350 by setting up a second printer in CUPS using the web interface to specify the paper size, print quality, etc.  When wanting to print on regular letter size paper I choose the one printer, and if I want to print 4x6 full bleed photo, I choose the other.  Let me know if you would like more details about this.

BTW instructions for getting the admin login for the web interface (localhost:631) working are in the forums.

- Jeffrey

---

### Post by AZMel on 2006-06-07
[QUOTE=king20878]Hi,

...  Let me know if you would like more details about this.


- Jeffrey[/QUOTE]

Please!  I have my printer, HP PSC 8450, Printing the test page perfectly on the 4x6 paper using your hints.  However the photos are printing too small.  What did you do?! :-D 

Mel

---

### Post by king20878 on 2006-06-08
[QUOTE=AZMel]Please!  I have my printer, HP PSC 8450, Printing the test page perfectly on the 4x6 paper using your hints.  However the photos are printing too small.  What did you do?! :-D l[/QUOTE]

I think that is sometimes a problem/feature of the application you may
be printing from.  I find that gthumb provides the best interface for
everyday printing.  eog always puts a border around the photo.  Is it
printing much smaller? or just not printing to the edges?  Also if your photos are not exactly 4x6 in dimension, it will not fill the whole page.  You may need to crop the photo.  gthumb has a good cropping interface for this.

Try gthumb and let me know how it goes.

---

### Post by AZMel on 2006-06-10
[QUOTE=king20878] You may need to crop the photo.  gthumb has a good cropping interface for this.

Try gthumb and let me know how it goes.[/QUOTE]

Works perfectly once I set the margins to 0.  I also had to make sure the picture shows up in the preview when sending to the printer.  Excellent work!  

Thanks!

Mel

---

