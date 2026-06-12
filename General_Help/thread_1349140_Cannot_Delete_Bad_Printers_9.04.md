---
title: "Cannot Delete Bad Printers 9.04"
date: 2009-12-07
forum: General Help
---

### Post by DantePasquale on 2009-12-07
Hi All,

I have a weird problem. I have 2 bad printers that show up in the System->Administration->Printing -- Printer Configuration Application. The problem is that I can't delete them! I really want them gone, but the Delete option is not available!!!

Here's some screen shots:

---

### Post by lidex on 2009-12-08
Looks like you need permission. Go to "system>administration>users and groups". Click "Unlock". Click "manage groups". Select "lpadmin" and click "properties". Make sure your username is checked. Click OK then close.

Back at the first window select your username on left and click properties on right. In next window select "user privileges" tab. Put a check in the box for "configure printers". Click OK then close.

---

### Post by DantePasquale on 2009-12-08
Bummer, that didn't work! Tried running 'gksu system-config-printer' and that didn't work either!

If I deselect "View->Show Discovered Printers" the 'bad' printers go away so at least they aren't confusing to my other users.

Checked the printcap and cups.conf files and I don't see these printers. Any CLI commands to clean this up? lpadmin doesn't look promising.

Oh, did I mention that I hate printers!

---

### Post by lidex on 2009-12-08
You use cups, right? Enter this uri in your browser address bar:
```
http://localhost:631/
```

See if you can delete from there.

---

### Post by DantePasquale on 2009-12-08
Good thought, but still can't delete. I think this is because the device uri is something like file:///dev/null -- not sure how that got set like that, but that's what it is!  (I may have an extra or missing slash)

---

### Post by lidex on 2009-12-08
Maybe because it's shared?
In "Server>Settings" are the first two boxes checked? Try unchecking them? OK, I'm reaching :-k

Maybe try unpublishing first then delete. (Cups interface - below).
Or modify printer and remove that bad uri. Maybe can't delete what it can't find. Finally, click documentation tab and read on...

---

### Post by lidex on 2009-12-08
Have a look at these links:
[http://www.linuxforums.org/forum/slackware-linux-help/156325-bad-device-uri-canon-ip1800.html]("http://www.linuxforums.org/forum/slackware-linux-help/156325-bad-device-uri-canon-ip1800.html")
[http://www.linuxquestions.org/questions/linux-software-2/cups-not-working-properly-doing-crazy-stuff.-769983/]("http://www.linuxquestions.org/questions/linux-software-2/cups-not-working-properly-doing-crazy-stuff.-769983/")
[http://lists.apple.com/archives/printing/2006/Jun/msg00010.html]("http://lists.apple.com/archives/printing/2006/Jun/msg00010.html")

---

