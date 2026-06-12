---
title: "Accidentally overwrite /opt/lib/ directory"
date: 2012-02-10
forum: General Help
---

### Post by power39 on 2012-02-10
Hello,

I am using Ubuntu 11.10. I was following an erroneous C programming tutorial and accidentally overwrote my /opt/lib directory with:
sudo mv mylibrary.so.1.0 /opt/lib

What's the best way to undo the damage done?

Thanks.

---

### Post by llamabr on 2012-02-10
there's nothing in mine.  What was in yours? (short answer -- whatever you deleted is gone).

---

### Post by power39 on 2012-02-10
I have no idea what was in it. <feels dumb>

---

### Post by painejake on 2012-02-11
As far as I'm aware /opt is where 3rd party packages and add-on application packages go.

Maybe something you installed for a .sh or .bin? Or compile yourself with /opt prefix?

Hope this helps

---

### Post by The Cog on 2012-02-11
This command:
> sudo mv mylibrary.so.1.0 /opt/lib
will move the file so that it becomes /opt/lib (overwriting any per-existing /opt/lib file). But it there was already existing /opt/lib directory, then it would simply have moved the library file into the /opt/lib directory.

Ubuntu does not normally have a /opt/lib file or directory (/opt is normally empty), so I think there has been no damage done. These commands should make the directory and put the library file in there with its proper name:
> sudo mv /opt/lib /opt/mylibrary.so.1.0
sudo mkdir /opt/lib
sudo mv /opt/mylibrary.so.1.0 /opt/lib

---

