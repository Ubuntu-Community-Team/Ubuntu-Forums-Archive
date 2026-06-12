---
title: "Ntfs resize errors"
date: 2010-07-10
forum: General Help
---

### Post by runrun395 on 2010-07-10
<snip> Let me list out to you the disasters which brought me here to you today.

1. Shut down my computer... WHILE PC DOCTOR WAS CHECKING MY HARD DRIVE
2. Kept getting <snip> errors at bootup
3. Used a live linux CD to save all of my files to one partition on our external hard drive
4. Started using the Ubuntu CD
4. Started cutting space from my mom's partition (I'm 15) to make room for the image that would be created by ntfsclone (my only smart move
5. Realized how to just transfer from my backup onto my computer w/o an image
6. Got impatient (here it comes)... and DECIDED TO CANCEL IN THE MIDDLE OF THE RESIZE
7. Started the ntfsclone (working for now)
8. Tried opening my mom's <snip> partition and got error messages

Now I'm thinking about how she's going to kill me and how maybe I should have listened when she asked me to bring in my computer to her work for fixing.

Lenovo ThinkPad T61
Windows 7 Ultimate x86
Core2 Duo T9300 @2.5GHz

---

### Post by garvinrick4 on 2010-07-10
I cannot stand the word retarded you are just impatient. As you grow older you will
gain patience. And face up to what you did wrong and tell Ma and take the heat. 
Oh yea and no need for **** up cursing is not something adults do, just kids. Good luck and take care runrun395.

---

### Post by Elfy on 2010-07-10
If you want help from people cut the language.

---

### Post by Megaptera on 2010-07-10
Hi,
What happens when you try to start up the ThinkPad? Can you get in to Windows? 
Was Ubuntu installed or were you using the live CD?

Can you post some of the error messages in case someone here can help you decipher them?

Richard

---

### Post by VeeDubb on 2010-07-10
All discussion of maturity and patience aside, I don't think that what you did is recoverable by "regular people."

At best, you'd be looking at booting up a live CD with modified permissions that would allow you to do things live CD's usually keep you from doing, imaging the entire drive to another drive, and running many many hours of diagnositcs and data recover programs on the image you created on another drive, and trying to recover as much as you can.  

In theory, that could be done without imaging to another drive, but then one mistake and any chance of recovery is gone.

I've gone through that hokey-pokey one time, and gotten 90% of my data back.  However, it was an ext3 volume that got messed up, and it was 'normal' data corruption, not an interrupted resize of and NTFS partition.  Basically, I'm saying that if it's possible to recover at all, it will be complicated, time consuming, and likely to fail.

---

