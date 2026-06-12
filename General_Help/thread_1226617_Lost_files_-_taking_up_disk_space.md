---
title: "Lost files - taking up disk space"
date: 2009-07-29
forum: General Help
---

### Post by fredtorrey on 2009-07-29
Hello,

I have run into a very starnge problem with my system where it thinks I'm using much more space than I actually am.  Let me explain.
I was helping my friend install ubuntu on his computer.  Before we did this, I created a shared folder on my computer, and allowed him to back up his files to my computer, so that he could retrieve them after deleting his partitions and installing ubuntu.
After he copied his files back to his computer, I wanted to delete them.  However, I did not have permission to delete them, they were read-only.  I messed around and thought that I changed the permissions.  I was able to delete the folder.  However, it appears the files did not actually delete - something is still taking up a large portion of my disk (his folder was several gigs in size).  I can't find the files anywhere. 
I have an 80GB hard drive.  When I check the properties of my filesystem, it says I am using 20 gigs.  When I go into my partion manager, it's showing that I have a 76 gig partion, of which I'm using about 70 gigs!
So what is going on here?  How can I clear up this space?
Please help!  Thanks

---

### Post by c0mput3r_n3rD on 2009-07-29
Did you remove it from the trash?

---

### Post by fredtorrey on 2009-07-29
> **c0mput3r_n3rD said:**
> Did you remove it from the trash?

Yes, that is the first thing I checked.  I've also deleted several other files and removed them from the trash successfully.  The trash is showing as empty.  I've rebooted the computer several times as well.

---

### Post by hyperAura on 2009-07-29
is it possible that u renamed the name of the folder and u placed a "." in front of it and its hidden? can u try searching for it through the terminal? just go to the directory and type ls -a and look for it.. thats wat i can think atm..

---

### Post by juanoleso on 2009-07-29
I've used baobab to figure out which folders are taking up the most space.

alt+f2 gksudo baobab
then scan from the root folder

---

### Post by DaithiF on 2009-07-30
> **fredtorrey said:**
> I have an 80GB hard drive.  When I check the properties of my filesystem, it says I am using 20 gigs.  When I go into my partion manager, it's showing that I have a 76 gig partion, of which I'm using about 70 gigs!


Hi
The 76gig vs 80gig drive is because 5% has been reserved by linux by default for system use.  5% of 80 = 4.  
As for where the 70gigs are being used, +1 for juanoleso's suggestion of baobab, also known as Disk Usage Analyser, in the menu at Applications -> Accessories -> Disk Usage Analyzer

---

### Post by fredtorrey on 2009-08-02
Thanks, that was the magic bullet.  Turns out the file was in my root folder, in the Trash.  So it wasn't being cleared out by me deleting my normal trash.  Opening the folder as root, I was able to delete the folder in question and get rid of it once and for all.
Thanks again.  Ubuntu community is great! :)

---

