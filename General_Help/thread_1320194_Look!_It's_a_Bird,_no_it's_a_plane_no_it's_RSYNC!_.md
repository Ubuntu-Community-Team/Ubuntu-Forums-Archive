---
title: "Look! It's a Bird, no it's a plane no it's RSYNC! Can't solve rsync"
date: 2009-11-09
forum: General Help
---

### Post by rlb.contact on 2009-11-09
Hello,
I'm in a bit of a pickle. Here's the breakdown:

1) My hardrive was acting weird. I knew that she was going down for the count soon.
2) The hdd was only 40GB, and it was not big enough to store everything I had.
3) Over time, I had stored more and more extraneous info onto an external usb hdd.
4) I made my final copy and wham! the hdd died.
5) New hdd, 120GB is plenty big.

What I have done:
As a precaution I duplicated all files/directories from usb onto new hdd. So there are copies at this point. Many of the directories and files are duplicates with small changes.

What the current situation looks like:
I may have three main directories that have roughly the same files. There may be additional files. Parts of each main directory might have extra folders.


/GenHome/
Academic Stuff    Financial                        My Music     video
BookStored        Financial Aid and Student Loans  My Pictures  Volunteer
Business Letters  Glasgow MPH Laptop Docs          Pictures     Work
DocTransfer2      Legal                            Rnd Stuff
Document          Medical  

/sink/
Desktop    Downloads  Library Media  Pictures  Templates
Documents  kdenlive   Music          Public    Videos


What I need to do:
1) I want to condense all of the files into a unified structure. GenHome has the most information. sink needs to be brought into the larger structure of GenHome. However, there is a lot of duplication and extra folders that need to be incorporated into the new uber directory
2) I want to eliminate duplicate files, keeping the newest file only.
3) I really don't want to have to do this by hand :-)

So...I imagine that there is a shell script with rsync that might work for this. However I am not even closely able to do this on my own.


BTW, good job on Karmic Koala! Smoothest yet...

---

