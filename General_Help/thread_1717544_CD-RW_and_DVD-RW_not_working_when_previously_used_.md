---
title: "CD-RW and DVD-RW not working when previously used on Windows"
date: 2011-03-30
forum: General Help
---

### Post by Ghost_Mazal on 2011-03-30
Lo Guys , I have been struggling with this problem for a long time. I can't use cd-rw's or dvd-rw's that was previously burned in Windows. I have a lot of them that I still have from my Windows days and want to re-use them. But my Ubuntu can't delete the rw's so that I can use them again. I tried both Brasero and K3b. Both I just get "erase failed". It happens on both my desktop pc and my laptop. Is there a way or and app that will be able to erase these rw's that I can re-use them with Ubuntu ?

Thanx for any help.

---

### Post by Ghost_Mazal on 2011-03-30
bump

---

### Post by Sidewinder1 on 2011-04-03
I, also, would like to know the answer/s to the above question.
TIA,
Side

---

### Post by dandnsmith on 2011-04-03
I think some more info is needed to make an answer feasible.

1. release of ubuntu
2. any added bits to try to get brasero working
3. have there been successful writes to CDR etc?
4. can you mount the offending disks?

---

### Post by Ghost_Mazal on 2011-04-03
> **dandnsmith said:**
> I think some more info is needed to make an answer feasible.
 
1. release of ubuntu
2. any added bits to try to get brasero working
3. have there been successful writes to CDR etc?
4. can you mount the offending disks?
 
1. In my sig
 
2. None
 
3. Yes. CDR records without any problems
 
4. Yes. Offending discs mount normally and data currently on it can be accessed

---

### Post by Sidewinder1 on 2011-04-03
Think I got it...
Go to: Applications->Sound and Video->GnomeBaker, click on it.
When it opens, in Places, click on your CD drive (with disk to be erased in that drive) than go to Tools and click on Blank CD.
And, once it starts, even at 4X, it will say "One minute to complete". Don't believe it!!!
It took another 21 minutes from the "One Minute" message, but at least it worked.
Side

---

### Post by Ghost_Mazal on 2011-04-03
> **Sidewinder1 said:**
> Think I got it...
Go to: Applications->Sound and Video->GnomeBaker, click on it.
When it opens, in Places, click on your CD drive (with disk to be erased in that drive) than go to Tools and click on Blank CD.
And, once it starts, even at 4X, it will say "One minute to complete". Don't believe it!!!
It took another 21 minutes from the "One Minute" message, but at least it worked.
Side
 
Will give that a go thanx

---

### Post by Sidewinder1 on 2011-04-03
If that works to your satisfaction, please don't forget to mark your thread as "Solved".
 
As an aside, using GnomeBaker to then burn a copy of 10.04, live CD, (with all due respect to the developers), it doesn't have the wherewith-all to handle an ISO image. All it did was copy the raw ISO image to the CD; now I'm wasting another 21+ minutes blanking that CD. OTO, it may be my ignorance by not using the proper settings in GB.

Oh, well, back to the drawing board...

Side

---

### Post by dandnsmith on 2011-04-03
Brasero is set up to do ISO burns - I think I've used it in earnest (but memory is confused because of other things happening around that time.

---

### Post by Ghost_Mazal on 2011-04-03
I successfully erased a DVD-RW now also with gnomebaker. Seems gnomebaker for erase and Brasero or K3b for burning is the way to go.

---

### Post by Sidewinder1 on 2011-04-03
As a follow-up, I had to install Brasero (that's what I've had success with in the past), and it worked (burning ISO image for live CD), like a charm. :)

Side

---

