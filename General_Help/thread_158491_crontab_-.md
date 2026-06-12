---
title: "crontab -"
date: 2006-04-11
forum: General Help
---

### Post by wiggy2k on 2006-04-11
Hi guys

I've just put 50 new machines in our call centre each with Ubuntu on
i'm wanting to add a crontab entry to shut them all down at 6pm

i've been doing this one at a time like this

export EDITOR=vi && sudo crontab -e

then adding 
00 18 * * * /sbin/halt

and this works fine but..... is there a way of doing this in a script?

maybe something like

echo 00 18 * * * /sbin/halt >> /path/to/some/file


Thanks
Scott

---

### Post by gnu2tux on 2006-04-11
$sudo crontab -e < file_with_crontab_entry

eg: the file with the crontab entry will look like this:

00 18 * * * /sbin/halt

Still have to type in password for each box, unless you change the authentication options, but that should work.

Let me know how you go.

Al.

---

### Post by justleen on 2006-04-11
[QUOTE=wiggy2k]Hi guys

I've just put 50 new machines in our call centre each with Ubuntu on
[/QUOTE]


keep it up!!  :cool:

---

