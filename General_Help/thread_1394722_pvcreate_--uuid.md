---
title: "pvcreate --uuid"
date: 2010-01-30
forum: General Help
---

### Post by rpaskudniak on 2010-01-30
Greetings.

I have a 64-GB extended partition, part of a ~74GB EXT partition. IN my case, it is /dev/sdc5, a sub-partition of /dev/sdc3.  I wish to create/format it as a physical volume using the [FONT="Courier New"]**pvcreate**[/FONT] command, followed by creating logical volumes using the **[FONT="Courier New"]lvcreate[/FONT]** command.  (Never mind why; I am an Informix DBA with higher aspirations.:) )  It is not mounted and I will be using the raw character volumes for the server chunks.

Before I run pvcreate, I look at its man page.  It mentions the **[FONT="Courier New"]--uuid[/FONT]** command option but gived no example of a UUID in this command should look like.  The only clue I have is the UUID directives in the /etc/fstab file; they are [FONT="Impact"]UUUUUUGGGGLY!![/FONT] :-x For example, the one on the / (root) directory:
> [SIZE="2"][FONT="Courier New"]UUID=24c930e7-9639-4023-bac8-00053bd2d8e6  /  ext3  relatime,errors=remount-ro[/FONT] (rest omitted)[/SIZE]
What does that apparently meaningless string of hex digits actually stand for?  If I need to put together a meaningful uuid for the pvcreate command, what do I need to use for the --uuid option?

FWIW, I have attached a screenshot showing the relationship of sdc3 to sdc5.
 
Thanks for knowledgeable help here.

---

