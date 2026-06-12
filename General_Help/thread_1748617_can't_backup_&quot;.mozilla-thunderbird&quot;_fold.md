---
title: "can't backup &quot;.mozilla-thunderbird&quot; folder"
date: 2011-05-03
forum: General Help
---

### Post by davek22 on 2011-05-03
I did a search and found a thread about how to backup one's Thunderbird emails and settings. Part of this process is to go into the Home folder and copy the ".mozilla-thunderbird" folder.

When I try to copy this folder to a thumb drive or burn to dvd, it gives me the _following error message_:

***"file system doesn't support symbolic links"***

Anyone know how to copy this folder?

Btw- I just recovered from an interrupted upgrade...but my wifi doesn't work. The natty live cd allows wifi to work so I want to copy this folder before upgrading. Wifi currently not working.

P.S. Not sure if relevant but this folder is the only one with a little curved arrow on the folder icon.

---

### Post by Vaphell on 2011-05-03
apparently it's not a real folder but a link pointing to some other physical folder.
```
ls -la ~
```
do you see **.mozilla-thunderbird -> some/stuff** there? some/stuff would be the real location of your thunderbird profile

---

