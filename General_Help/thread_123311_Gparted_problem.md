---
title: "Gparted problem"
date: 2006-01-29
forum: General Help
---

### Post by Zalbor on 2006-01-29
This is more of a bug report than a question, I'm not sure if this is the right forum to post it.

I've noticed that when I set GNOME to the greek language, Gparted fails to starts. The window appears for just a moment before closing. This should probably be fixed for dapper, sorry if it's been reported before.

---

### Post by dcstar on 2006-01-29
[QUOTE=Zalbor]This is more of a bug report than a question, I'm not sure if this is the right forum to post it.

I've noticed that when I set GNOME to the greek language, Gparted fails to starts. The window appears for just a moment before closing. This should probably be fixed for dapper, sorry if it's been reported before.[/QUOTE]
Open a terminal and run it, then you will see the error message.

---

### Post by Zalbor on 2006-01-29
It's a segmentation fault. Why would it happen in one language and not in the other?

---

### Post by dcstar on 2006-01-29
[QUOTE=Zalbor]It's a segmentation fault. Why would it happen in one language and not in the other?[/QUOTE]
Don't know, could be any one of many, many reasons - missing language files, locales etc. etc.

---

### Post by plors on 2006-01-30
i guess this is a known problem which was related to a bug in libstdc++. This is solved in gparted-0.1 and above.

See also [this bug]("http://bugzilla.gnome.org/show_bug.cgi?id=157871")

Btw, you should consider filing bugs about such stuff instead of complaining about it on some public forum. As long as developers don't know about bugs they can't fix them.

To make OSS 'work', we need an active userbase :)

---

### Post by Zalbor on 2006-01-30
[QUOTE=plors]Btw, you should consider filing bugs about such stuff instead of complaining about it on some public forum. As long as developers don't know about bugs they can't fix them.[/QUOTE]
Well I know, but I don't know where to file it...

---

### Post by plors on 2006-01-30
hmmzz, that one is easy :)

-you go the the projects homepage (in this case [http://gparted.sf.net]("http://gparted.sf.net"))
-you go to a section called 'bugs'
-usually there's some info about how to file a new bug (in this case there's a step by step questiongame which lets you enter a bug in the most convenient way)

enjoy :D

---

### Post by Zalbor on 2006-01-30
Thanks! I thought it was an ubuntu thing, and was trying to find an "inform us for bugs" or something forum, I didn't think of checking the project itself...

---

