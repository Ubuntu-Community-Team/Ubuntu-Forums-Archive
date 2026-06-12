---
title: "Firefox gone haywire"
date: 2010-08-15
forum: General Help
---

### Post by damnated on 2010-08-15
I'm using version 3.6.8, and this is the list of the errors:

- Tab, Home, End, Pg Up, Pg Down, Arrow Keys not working (when it comes to navigation on the page and when it's about writing, editing text)
- I use del.ici.ous bookmarks, and in the past this replaced my Firefox bookmarks menu. Now the original Firefox bookmarks menu is back (in del.ici.ous the settings are to hide it!); when I click on the del.ici.ous bookmarks button, I get an empty side panel. I'm logged in, and if I go to the del.ici.ous site, I can see that my bookmarks are there, so they weren't deleted or anything. They just don't show up in the side panel.
- I can't bookmark to delicious. When I push the TAG button or Right Click on the page and select Bookmark this to Delicious, nothing happens.

I do not have Caret Browsing on, I have activated it and deactivated it however, but it didn't fix my problem. Every button I mentioned works everywhere else.
It is something definitely Firefox related, and I don't know what is going on, please advise!

---

### Post by afrodeity on 2010-08-15
```

sudo apt-get install --reinstall firefox

```

---

### Post by damnated on 2010-08-15
> **afrodeity said:**
> ```

sudo apt-get install --reinstall firefox

```
Didn't work.

---

### Post by Karl1982 on 2010-08-15
Might try purging firefox to include its config and all user data, then reinstall from scratch.  Check your home folder for any leftovers before reinstalling.  If Firefox is the problem, it seems like that should fix it...

---

### Post by lovinglinux on 2010-08-15
Looks like is del.ici.ous extension that gone haywire. This is the second post I read today about del.ici.ous problems. So disable it.

---

### Post by damnated on 2010-08-15
> **lovinglinux said:**
> Looks like is del.ici.ous extension that gone haywire. This is the second post I read today about del.ici.ous problems. So disable it.

And circle takes the squire. Thank you!

EDIT: After doing some googleing, it turns out that the newest del.ici.ous update is to blame. It is particularly bad on linux systems, but other platforms had their fair share of errors with it as well. [http://support.delicious.com/forum/comments.php?DiscussionID=5042](http://support.delicious.com/forum/comments.php?DiscussionID=5042)

If anyone else came across this issue, I can confirm that installing an older version of del.ici.ous fixes everything. Link here: [https://addons.mozilla.org/en-US/firefox/addon/3615/eula/67323](https://addons.mozilla.org/en-US/firefox/addon/3615/eula/67323)

---

