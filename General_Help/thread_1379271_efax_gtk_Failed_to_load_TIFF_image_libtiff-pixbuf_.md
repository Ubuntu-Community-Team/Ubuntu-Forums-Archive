---
title: "efax gtk Failed to load TIFF image: libtiff-pixbuf: Bad value 0 for &quot;RowsPerStrip&quot;"
date: 2010-01-12
forum: General Help
---

### Post by Fitch on 2010-01-12
This is a bit wierd in that e-fax seems to be working, and in the home directory, I can actually see a couple of faxes with a PS on the end, is that PostScript?

But e-fax itself seems to be putting the "faxes" in a /home/faxin/<yeardatetimesecond> directory and is subsequently unable to read the tiff image in that directory.  

When I call up the received fax list and click on a fax, nothing happens.
If I try to open the file with Nautilus, I get:
Failed to load TIFF image: libtiff-pixbuf: Bad value 0 for "RowsPerStrip"

Any ideas?

---

### Post by kwstas on 2010-03-01
it seems that you can see your received fax only by clicking on the "view" icon!
i have the same problem about the tiff message and i have noticed that some times the "document viewer" open the tiff! i think it's while the received faxes list is opened or something...

---

### Post by Fitch on 2010-03-01
Whatever I do, it's unreadable.
Is there anything that can actually read an image with "0 per strip"?

---

### Post by doubledice on 2011-10-03
Hello, anyone knows of a solution to this problem, im in search too!

---

### Post by Fitch on 2011-10-03
This is what put me completely off Linux.
I am now back on Windows as no-one was interested. (you might have guessed that as my last post is now a year and a half old)
The original creator of TKUSR stopped developing it about 1996 and now doesn't even have a fax anymore.
USR changed their raw data output so it is unrecognisable by Linux -You must go through their own software, and of course, they don't support Linux.
The people who maintain libtiff libraries could not make head or tail of the fax output, and that was that.
 
I own a business, and get quite a few bookings by fax every week. I tried getting someone interested and asked questions for about a year, and then wiped Linux and put XP back on as the cheapest and quickest alternative.
 
Sorry! but through experience, no-one is interested.
 
Linux is not downwardly compatible: every time there's an upgrade, the first thing the update does is remove everything that has become obsolete, and lo and behold, stuff doesn't work anymore.
 
USR (HP now) are partly to blame as the message modem has no Linux support (except the flash ROM upgrade - whoopey do!).
They have now got version D of the message modem, so are still selling it, but you have to use Windows.

---

### Post by RogerDavis on 2012-05-15
1) UNTRUE on the modem, USR does make internal modems (and external) that are compatible.

2) TRUE on the software - No one seems to give a damn.

---

