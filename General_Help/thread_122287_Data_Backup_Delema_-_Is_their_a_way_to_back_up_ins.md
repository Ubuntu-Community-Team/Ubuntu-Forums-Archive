---
title: "Data Backup Delema - Is their a way to back up installed programs, and settings"
date: 2006-01-27
forum: General Help
---

### Post by Shin Natsume on 2006-01-27
im getting a pc upgrade tommorow, and thus will probably need to wipe my hard disc and do a re install

i used one the automatix script to get a bunch of programs etc, and that was while i was on a high speed conection, but now im nack on 56k, and i dont really want to have to download everything again on such a slow connection, and from wat i remember reading about it, it deletes all the install files after installing, so i can simply back those up

so is their a way to back up those programs i installed etc onto dvd or something, and then restore them once ive reinstalled ubuntu?

thanks in advance :)

ciao

---

### Post by GeneralZod on 2006-01-27
All programs you installed should be cached in /var/cache/apt/archives.  Back them up onto DVD, and once you've installed your new system, copy them back from DVD into the same folder (will require root priviledges).

Personal settings are stored in your /home/<username> folder.

System-wide settings are trickier, but people very rarely change this in my experience.

---

### Post by Shin Natsume on 2006-01-27
thanks for the reply, i shall have a look tommorow/later today and hopefully they are their :D

will this also recreate the menu items for them, or will i have to recreate those myself?

thanks again

ciao

---

### Post by GeneralZod on 2006-01-27
[QUOTE=Shin Natsume]
will this also recreate the menu items for them, or will i have to recreate those myself?

thanks again

ciao[/QUOTE]

It's basically just the same as storing all of your Window's setup.exe; if the .deb file provides a menu entry, then this will be correctly installed.  If some of your programs were naughty and didn't come with a menu entry and you had to manually add it, then it's *possible* you'll have to add it again this time around, although if you copy your /home over your newly installed system, this might not be the case.

---

