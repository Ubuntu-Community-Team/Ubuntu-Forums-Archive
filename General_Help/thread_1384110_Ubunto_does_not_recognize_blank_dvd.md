---
title: "Ubunto does not recognize blank dvd"
date: 2010-01-18
forum: General Help
---

### Post by Nphil on 2010-01-18
I can write to CD+R no problem but when I try to write to DVD it does not work.
When I put the DVD in the drive and go to computer and click open I get a message " unable to mount location, no media in drive." 
If I have a blank CD+R it says blank CD in drive but with the DVD I am having problems.
I have way to many family pictures and I'd like to put it on 2 DVDs instead of 12 CD+Rs. Does anyone know how to fix this problem?

---

### Post by warfacegod on 2010-01-18
Stupid question. Are you sure you have a DVD burner?

---

### Post by audiomick on 2010-01-18
Another stupid question: can the drive read a dvd? A DVD is a higher precision level than a CD. It way be that the drive can still deal with CDs, but not DVDs anymore.

Also, have you tried different brands of DVD? Doesn't sound logical, but in my experience, at least with CD blanks, it can indeed make a difference.

---

### Post by warfacegod on 2010-01-18
> **audiomick said:**
> Another stupid question: can the drive read a dvd? A DVD is a higher precision level than a CD. It way be that the drive can still deal with CDs, but not DVDs anymore.

Also, have you tried different brands of DVD? Doesn't sound logical, but in my experience, at least with CD blanks, it can indeed make a difference.

I agree. I had a Verbatim CD-RW drive that refused to read anything but Memorex discs and these cheap, no name brand discs that I got at the dollar store.

---

### Post by shreepads on 2010-01-18
Have a look at your disc drive specs, does it support burning to DVDs? 

Even within DVDs there are several different formats (DVD-R, DVD+R, DVD-R DL, DVD+R DL, DVD-RW, DVD+RW, etc) and unless the burner supports exactly the DVD format blank disc inserted it will not work. If the two match and it still doesn't work most likely explanation is that the blank media you have is faulty, try with a replacement.

IMHO the brand should not matter as long as the above requirements are satisfied.

---

### Post by 73ckn797 on 2010-01-18
If you determine the drive supports DVD then you will need to install "dvdauthor" from Synaptic. I was having the same problem in 9.10 using Brasero and other burning programs. It is not another burning program but will work in the background to allow burning a DVD.

---

### Post by shreepads on 2010-01-18
> **73ckn797 said:**
> If you determine the drive supports DVD then you will need to install "dvdauthor" from Synaptic. I was having the same problem in 9.10 using Brasero and other burning programs. It is not another burning program but will work in the background to allow burning a DVD.

The problem doesn't seem to be in the disc burning application (though Brasero works fine for me in Hardy on an LG burner) but in the disc/ drive based on the message:
    "unable to mount location, no media in drive."

---

### Post by 73ckn797 on 2010-01-18
> **shreepads said:**
> The problem doesn't seem to be in the disc burning application (though Brasero works fine for me in Hardy on an LG burner) but in the disc/ drive based on the message:
    "unable to mount location, no media in drive."
Exactly!

---

### Post by ProfBib on 2010-06-17
I have been having the same problem with my installation of 10.04 on a older Dell Dimension.  No luck burning with Brasero, burn (terminal app) or anything else from the gnome repositories.

What - it's about to get strange...

Back when I used KDE, I remember really liking K3B, so I went ahead and installed that and...it burned correctly using the exact same hardware on the very first try!

HMMMM:confused: but :p

---

