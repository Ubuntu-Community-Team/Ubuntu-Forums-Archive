---
title: "Shotwell doesn't display all pictures."
date: 2011-02-07
forum: General Help
---

### Post by Dragonbite on 2011-02-07
I've imported my pictures into Shotwell, but not all of them are showing up.

For instance, I have an event (White Water Rafting) where 25 of the 48 pictures got imported correctly.  The rest of them were placed in this 2008/12/28 folder and this folder is not visible in Shotwell so I cannot move them into the album.

I can manually move the pictures to their proper dates, but how do I add them to the database?

One caveat, the pictures are stored in an accessible /home/SHARE/Pictures/Photo directory so my wife and I can both import into the same place and have access (while the kids have read-only access).  I placed the .shotwell directory with all of the database information in /home/SHARE/Pictures/.Shotwell and linked our local .shotwell directory in our home folders to this shared location version.

I am wondering if there is a way to:
[LIST=1]
[*]Force the inclusion of these pictures that are not showing up?
[*]Force the database to re-create the thumbnails/scan for particular dates
[*]or should I remove (rename) the database, move the files to where they should be and re-import the entire structure (minus the "copy to ... " option)
[/LIST]

---

### Post by Monitor Inc on 2011-03-05
I have come up against something similar.
I collect photos on a portable hard disk and import them into Shotwell on my home PC.
Shotwell copies all the photos to the hard disk, and they are all visible if I click <Last import> 
But some are missing from the main catalogue <Photos>
The missing photos are the ones taken with my phone's camera. The files have a create date, but no date in the metadata.
Shotwell files and catalogues by date.  Is this problem just Shotwell not coping with no  metadata?

The obvious work around is to edit a date into the matadata, and then they are imported correctly.  But this is long winded.

Should (or could) Shotwell use the file create date if there is no metadata?

May 2011.  After upgrading to 11.04 this appears to have been corrected.

---

