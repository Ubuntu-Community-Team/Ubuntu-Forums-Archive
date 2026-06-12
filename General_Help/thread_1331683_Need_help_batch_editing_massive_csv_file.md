---
title: "Need help batch editing massive csv file"
date: 2009-11-19
forum: General Help
---

### Post by purduepilot on 2009-11-19
I was going to go flying this morning, but the freezing levels are at like 3000 so we canceled. With nothing else to do at the moment, I've been screwing around with this for the past few hours and have hit a snag.

I have a Garmin Nuvi 255W with a road database. I am trying to add some aviation "points of interest" to it (airports, navaids, intersections, etc.) so that I can use it while flying. I found a nice little site [http://navaid.com/GPSPilot/?clear=yes](http://navaid.com/GPSPilot/?clear=yes) that generates aviation POI files for Palm devices, and have used a program that I found on one of the Ubuntu repositories (gpsbabel) to convert it into a csv file as an intermediate step file which I can run through the Garmin utility to add to my GPS. The snag I'm running into, though, is that when I convert it into a csv file it does not put quotes around the waypoint name, and the Garmin utility seems to require that text have quotes.

Summary: I need a way to put quotes around the cells in one column of a csv file. The quotes cannot be around the lat/lon entries.

Here's part of the airport POI file:

39.94302, -91.19446, KUIN
39.98539, -90.80414, I63
39.63886, -90.77843, KPPQ
41.24865, -90.73708, C00
40.52008, -90.65239, KMQB
40.92970, -90.63111, C66
40.11755, -90.59041, 5K4

I need it to be formatted like this:

39.94302, -91.19446, "KUIN"
39.98539, -90.80414, "I63"
39.63886, -90.77843, "KPPQ"
41.24865, -90.73708, "C00"

But I'd really prefer not to do that manually for all 10000ish entries. Anybody have any ideas?

---

### Post by hwttdz on 2009-11-19
cat input.csv |awk '{print $1 $2 "\""$3"\""}'>outputfile.csv

---

### Post by undecim on 2009-11-19
Open a terminal (Applications -> Accessories -> Terminal) and type (copy/paste) this: ```
awk -F ", " -v q='"' '{print $1 FS $2 FS q$3q}' oldfile > newfile
```where "oldfile" is the original file, and "newfile" is a new filename where you want the new, correct csv file to be placed. (Note: if you have any spaces in the filenames, you will need to put the filenames in quotes)

EDIT:
> **hwttdz said:**
> cat input.csv |awk '{print $1 $2 "\""$3"\""}'>outputfile.csv
Or that, assuming that spaces don't make a difference.

---

### Post by hwttdz on 2009-11-19
Who's going to break out the "perl -i -pe "s/ome_crazy/perl_nonsense/"" for the win? (and I'm kind of curious and messed it up on my first try).

---

### Post by purduepilot on 2009-11-19
Excellent!  Thanks so much!

---

