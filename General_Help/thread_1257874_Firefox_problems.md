---
title: "Firefox problems"
date: 2009-09-04
forum: General Help
---

### Post by SISU1375 on 2009-09-04
Last night I lost all of my bookmarks, and Firefox won't let me bookmark any sites now to replace the ones I had.  Barnes & Noble opens, but it crashes immediately...Any ideas?

---

### Post by winotree on 2009-09-04
Try looking in /home/user/.mozilla/firefox/letternumber.default/bookmarkbackups then copy the last one back into your browser using Organize Bookmarks | Import and Backup | Restore

Firefox, by default always keeps five previous copies in the bookmarkbackups folder.  ;)

NOTE - letternumber.default folder is your uniquely named Firefox Profile -- it has an eight-digit alpha-numeric name followed by the .default designation...

EDIT - in the event this doesn't work or isn't what you need try a new profile -- if it works you can move your personal information over to it -- see if this helps [http://support.mozilla.com/en-US/kb/Profiles](http://support.mozilla.com/en-US/kb/Profiles)

---

### Post by lovinglinux on 2009-09-05
See **Solution** [*[COLOR="Red"]**FOT003**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT003).

---

