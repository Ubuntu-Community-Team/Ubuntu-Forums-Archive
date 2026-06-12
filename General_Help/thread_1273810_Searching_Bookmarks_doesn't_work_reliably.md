---
title: "Searching Bookmarks doesn't work reliably"
date: 2009-09-23
forum: General Help
---

### Post by narnie on 2009-09-23
I'm have a problem with firefox 3.0 AND 3.5 not working correctly on searching bookmarks. I can be in a directory in the library and SEE the link I'm trying to find. When I type a word from the title, It doesn't see it and there is nothing but white screen in the links area. This behavior is not present in every folder, but enough as to cause alarm.

I have a quite large bookmark set and need searching to work reliably. It bothers me that TWO versions of firefox have this issue.

I have exported the bookmark listing as HTML and it seems fine to me. No errors or strange gobble-dee-gook. I have even deleted the old bookmark and imported in the HTML that I originally exported. This did not seem to "wake up" the search.

Any ideas?

Thanks,
Narnie

---

### Post by narnie on 2009-09-26
Nobody responded to this, but I found the solution.

I was trying to figure out how bookmarks are stored in Firefox. I renamed my .mozilla folder and started from scratch. By a few trials, I discovered that aside from the bookmarkbackup folder, they are normally stored in:

.mozilla/places.sqlite

and possibly also (as is mine):

.mozilla/places.sqlite-journal

I have xmarks installed and this may be required to make this work automatically.

I just closed firefox and renamed places.sqlite to places.sqlite.bak and the same with places.sqlite-journal.

I then restarted firefox and it rebuilt them from the backups (I think) and the searching worked correctly.

If you don't use xmarks (which I highly recommend), then I would first export the bookmarks to HTML via the menu Bookmarks->Organize Bookmarks then Import and Backup from the new window. Close firefox.

Then rename the above file(s) and restart firefox. Then import the bookmark similarly to the way the exported it (but just import this time) and I'll bet it will work.

I'm so glad to have searching bookmarks work well again!

Narnie

---

