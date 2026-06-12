---
title: "deleting bookmarks on 11.10,12.04"
date: 2012-04-26
forum: General Help
---

### Post by hunterkasy on 2012-04-26
Just a question, why can't I delete a bookmark in FF running 11.10 or 12.04 just right click on the bookmark and select delete?

instead I have to go to bookmarks,show all bookmarks, then search for the bookmark.

When, I right click on a bookmark, it acts like a left click, goes to the bookmark I want to delete

Every Ubuntu machine I have done has this issue

---

### Post by Trapper on 2012-04-26
> **hunterkasy said:**
> Just a queston, why can't a person who wants to delete a bookmark in FF running 11.10 or 12.04 just right click on the bookmark and select delete?

instead you have to go to bookmakrs,show all bookmarks, then search for the bookmark.

I'm running 12.04 and have FF 11. I can right click and delete without having to go to All Bookmarks. Sorry but I don't know why you can't.

---

### Post by hunterkasy on 2012-04-27
am I the only one with this problem?

---

### Post by hunterkasy on 2012-04-30
?

---

### Post by Trapper on 2012-04-30
Sorry man. I really wish I could help with this but I've never experienced it or heard of it. I am up to FF 12 now on 12.04 and I can still delete from the bookmark menu with a right click and selecting delete. I can do this in FF 10, 11 & 12 on 10.04, 11.10, 12.04 and Xubuntu 12.04.

Can you add new bookmarks and do they stick after a restart of FF?

---

### Post by hunterkasy on 2012-04-30
> **Trapper said:**
> Sorry man. I really wish I could help with this but I've never experienced it or heard of it. I am up to FF 12 now on 12.04 and I can still delete from the bookmark menu with a right click and selecting delete. I can do this in FF 10, 11 & 12 on 10.04, 11.10, 12.04 and Xubuntu 12.04.

Can you add new bookmarks and do they stick after a restart of FF?

I can add bookmarks just fine, 

every Ubuntu machine I have put together has this problem, running 11.10 or 12.04

---

### Post by Trapper on 2012-04-30
> **hunterkasy said:**
> I can add bookmarks just fine, 

every Ubuntu machine I have put together has this problem, running 11.10 or 12.04


Are these cases of you using using your previous .mozzila or have you allowed FF to create a new one at first run? In other words, are you getting the same results using a previous .mozilla and a newly created one?

---

### Post by hunterkasy on 2012-04-30
> **Trapper said:**
> Are these cases of you using using your previous .mozzila or have you allowed FF to create a new one at first run? In other words, are you getting the same results using a previous .mozilla and a newly created one?

I tried renaming my .mozzila, and restarted FF, still have the same problem

---

### Post by Mathor on 2012-04-30
> **hunterkasy said:**
> I tried renaming my .mozzila, and restarted FF, still have the same problem

Upgrade your Firefox. On the new one, you just click on the star and unclick the star, just like in Chrome.

---

### Post by hunterkasy on 2012-04-30
> **Mathor said:**
> Upgrade your Firefox. On the new one, you just click on the star and unclick the star, just like in Chrome.

I am running FF 12

---

### Post by troysos on 2012-04-30
I've always had this problem as well on every Ubuntu computer since 10.10. Linux mint FF works fine for some reason but never Ubuntu. Chrome works fine but I like FF more.

---

### Post by Mathor on 2012-04-30
> **hunterkasy said:**
> I am running FF 12

So what happens when you click the star? Mozilla made it really easy on this release, a problem I had with past releases. I hated their bookmark management.

You should be able to click on the bookmark to take you to that page, and unclick the star, and press "remove bookmark"

---

### Post by hunterkasy on 2012-04-30
> **troysos said:**
> I've always had this problem as well on every Ubuntu computer since 10.10. Linux mint FF works fine for some reason but never Ubuntu. Chrome works fine but I like FF more.

I started to have this problem with 11.10 all earlier versions worked

---

### Post by hunterkasy on 2012-04-30
> **Mathor said:**
> So what happens when you click the star? Mozilla made it really easy on this release, a problem I had with past releases. I hated their bookmark management.

You should be able to click on the bookmark to take you to that page, and unclick the star, and press "remove bookmark"

the star thing does work, still a hassle,

---

### Post by coldjeanz on 2012-04-30
same problem for me, even on 11.10

---

### Post by Trapper on 2012-04-30
Strange. I have to change the user's permissions of my places.sqlite in my .mozilla profile folder to read only to NOT be able to delete with a right click. Even then it still shows the delete option in the drop down menu. It just won't actually delete the file if I click on it. FF11 or FF12 on the 3 different ubuntu releases, including 12.04.

---

### Post by hunterkasy on 2012-05-01
I would like to know how many other people are expirencing this

---

### Post by markyb73 on 2012-05-01
i have the problem as well, running ff12 on 12.04, had it for a few releases now.

---

### Post by manney on 2012-05-13
This also happen to me when I upgraded from Ubuntu 10.04 to 12.04.  I launched firefox in safe mode and found I could right click my bookmarks.  After five minutes of disabling ff extensions I found the culprit.  Disabling the Firefox extension Global Menu Bar Integration 3.2.3 gave  me back full functionality.  I can now right click and delete a bookmark.  Hope this helps someone else.

---

### Post by satish_j on 2012-05-28
> **Trapper said:**
> I'm running 12.04 and have FF 11. I can right click and delete without having to go to All Bookmarks. Sorry but I don't know why you can't.

how come you got FF 11 with 12.04..
My default install of 12.04 gave FF12.
Did you downgrade it?iam also expero\iencing similar issue as OP.

---

### Post by satish_j on 2012-05-28
> **manney said:**
> this also happen to me when i upgraded from ubuntu 10.04 to 12.04.  I launched firefox in safe mode and found i could right click my bookmarks.  After five minutes of disabling ff extensions i found the culprit.  Disabling the firefox extension global menu bar integration 3.2.3 gave  me back full functionality.  I can now right click and delete a bookmark.  Hope this helps someone else.

that helped me....:p
THANKS A LOT..

---

### Post by chocklet on 2012-05-28
> **manney said:**
> This also happen to me when I upgraded from Ubuntu 10.04 to 12.04.  I launched firefox in safe mode and found I could right click my bookmarks.  After five minutes of disabling ff extensions I found the culprit.  Disabling the Firefox extension Global Menu Bar Integration 3.2.3 gave  me back full functionality.  I can now right click and delete a bookmark.  Hope this helps someone else.

Manney!  You're the best!

---

### Post by colin.p on 2012-05-28
That worked. It also cleared up a few other weird issues in bookmarks. I found scrolling through a couple folders deep would make the list disappear before I could select one. Now it's back to the way it was in lucid and the bookmarks scroll properly and I can right click and delete.

---

### Post by keyshawn on 2013-02-26
Thanks for the tip. "Global Menu Bar Integration" was the culprit for me as well. 

Once I disabled it, I was able to right-click on bookmarks and delete them. 


Another reason that I'm not liking unity. :(

And... Here's the bug report for it. Filed 2 years ago - [https://bugs.launchpad.net/globalmenu-extension/+bug/748850](https://bugs.launchpad.net/globalmenu-extension/+bug/748850)

---

