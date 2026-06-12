---
title: "Why is it that I can't keep putting files in CD/DVDs?"
date: 2010-10-08
forum: General Help
---

### Post by jcd29 on 2010-10-08
Whenever I put a few files into a blank CD or DVD, wether it's pictures, music, documents, whatever, and then I use it another day and try to put a few more files into it, Ubuntu won't let me. I used to be able to continue adding files to my CDs in XP, so I'm not sure if there's any way to do that with Ubuntu? It just shows the DVD as (for example) 1.4 GB used, 0 GB free.

---

### Post by Megaptera on 2010-10-09
You aren't perhaps using CD-R / DVD-R instead of CD-RW / DVD-RW by mistake? I know that's a basic question but sometimes it's easy to grab the wrong type off the shelf!

---

### Post by sendblink23 on 2010-10-09
> **Megaptera said:**
> You aren't perhaps using CD-R / DVD-R instead of CD-RW / DVD-RW by mistake? I know that's a basic question but sometimes it's easy to grab the wrong type off the shelf!

^^^  This

Or maybe he means the option in windows to leave the CD *Open not closed... which means you can still  add files into them... but I have never tried it on Ubuntu - and last time I used that was on xp :P

---

### Post by mobilediesel on 2010-10-09
Make sure the program isn't "closing" or "finalizing" the CD or DVD. Even if it's a CD-R instead of a CD-RW it should let you add files over many sessions until the disc is full as long as you don't finalize the disc.

---

### Post by jcd29 on 2010-10-09
Yeah it's CD-R but in XP I can keep the CD open as you mentioned. However, that's without even using a program, I just open the CD-ROM folder itself, and drag files into it, and that's it.

Doing that in Ubuntu after doing it once doesn't seem to work.

---

### Post by cascade9 on 2010-10-09
You need to start with a data or audio project, then open 'properties'

> **3.1.3.&#8195;Audio Project Options**


Before starting the burning process, it is possible to modify some of the burning options.
 	  
Section Select a disc to write to: 		
[LIST]
[*] 		    Click on Properties to open the properties dialogue for the burning device. See [Section 3.6 &#8213; Burning Device Properties]("http://library.gnome.org/users/brasero/2.29/brasero.html#brasero-burning-device-properties") for more information.
[/LIST]

 	      Section Disc options: 		
[LIST]
[*] 		    Leave the disc open to add a data session later 			  Select this option to create a multisession disc, so that it will be possible to add files to the disc at a later date (without erasing it, if it is rewritable).
 			
[/LIST]

 	      
**3.2.1.&#8195;Data Project Options**


Before starting the burning process, it is possible to modify some of the burning options.
 	  
Section Select a disc to write to: 		
[LIST]
[*] 		    Click on Properties to open the properties dialogue for the burning device. See [Section 3.6 &#8213; Burning Device Properties]("http://library.gnome.org/users/brasero/2.29/brasero.html#brasero-burning-device-properties") for more information.
[/LIST]

 	      Section Disc options: 		
[LIST]
[*] 		     			  Increase compatibility with Windows systems 			 			  Select this option if you intend the disc to be used on computers running Windows. Files on the disc will be checked to ensure that their filenames do not contain characters which are invalid on Windows.
 			
[*] 		    Leave the disc open to add other files later 			  Select this option to create a multisession disc, so that it will be possible to add files to the disc at a later date (without erasing it, if it is rewritable).v
 			
[/LIST]

 	      


[http://library.gnome.org/users/brasero/2.29/brasero.html](http://library.gnome.org/users/brasero/2.29/brasero.html)

You have to make sure you select "Leave the disc open to add other files later". ;) 

To "finalise" the disc, you will need to deselect it when you burn the last data onto the drive (though you might get a dialog asking you if you want to finalise if you totally fill the disc).

---

### Post by srs5694 on 2010-10-09
You could also look into the udftools package. This enables you to create a UDF-only disc and treat it like you would a hard disk, mounting it read/write and adding and deleting files at will. In my experience, it only works properly with DVD+RW discs, but the description implies it works with other media type, so perhaps I'm missing something or have something misconfigured.

---

