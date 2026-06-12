---
title: "CD Burning seems broken in Maverick"
date: 2010-10-28
forum: General Help
---

### Post by gustav.franzsen on 2010-10-28
Am running Ubuntu 10.10 Maverick Meerkat (did an in situ upgrade from Lucid) quite happily, except for the following issue I ran into:

I place a new cdr in drive
Open as folder
Copy mp3's onto it
Click Write to CD
Stick with default selections
Process starts, but when cd is burnt ends with error message.
Saved brasero log - it ends with this:

"
BraseroChecksumImage called brasero_job_error
BraseroChecksumImage finished with an error
BraseroChecksumImage asked to stop because of an error
	error		= 27
	message	= "Some files may be corrupted on the disc"
BraseroChecksumImage stopping
BraseroChecksumImage closing connection for BraseroChecksumImage
Session error : Some files may be corrupted on the disc (brasero_burn_record brasero-burn.c:2862)
"
The files (incl folder structure) seems to be on the cd, but will not play.

I take exactly the same source and media-type to a Lucid-machine, do exactly the same and the cd burns fine?

Seems to be a Maverick-issue.

I did come across someone's suggestion to (1) Remove Brasero (2) Re-install it (3) Install gnomebake, but it did not seem to make any difference.

Anybody else having the same or similar experience?

---

### Post by conradin on 2010-10-28
Yep
I went back to an older kernel version on disk and it works fine 
The checksum seems to be taking foreva though.

---

### Post by ezsit on 2010-10-28
I gave up on Brasero. I installed Gnomebaker and all works fine there.

---

### Post by gustav.franzsen on 2010-10-29
I prefer to do my copying and burning with and from within the file manager, Nautilus I think?

Don't like using any dedicated cd-burner.

Is there a way I can tell Nautilus to use some other burn-option than Brasero then?

---

### Post by gustav.franzsen on 2010-10-29
@Conradin - Thnx! If I cannot find another way around it, will follow your route!

---

### Post by gustav.franzsen on 2010-11-01
> **ezsit said:**
> I gave up on Brasero. I installed Gnomebaker and all works fine there.

Thnx! That is the easiest work-around ... Gnomebaker ran without errors! :P

Gustav

---

### Post by kennedyjch on 2011-08-30
One solution that worked for me in this sort of case was to uninstall the (3) brasero packages (synaptic) and reinstall.

---

