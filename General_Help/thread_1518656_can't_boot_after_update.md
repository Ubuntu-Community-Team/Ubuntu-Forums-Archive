---
title: "can't boot after update"
date: 2010-06-26
forum: General Help
---

### Post by dave_man137 on 2010-06-26
ok so can't boot after updating x this has happened before but not like this. Grub works just fine but nothing after what I can't do 

1 10.04 = black screen
2 recovery mode=black screen
3 ctrl+alt+f1 = nothing

Please help


ps it's a ati card and yes I think they suck

---

### Post by dave_man137 on 2010-06-26
bump

---

### Post by dave_man137 on 2010-06-27
Nobody has a idea how this can be fixed?

---

### Post by warfacegod on 2010-06-27
Can you boot boot properly with an older kernel?

---

### Post by Rubi1200 on 2010-06-27
Hi,
can you run a LiveCD?
If so, see here and follow the instructions before posting back:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by dragos240 on 2010-06-27
Agreed, looks like a kernel issue if you can't get into recovery mode, if not, it's something deeper.

---

### Post by dave_man137 on 2010-06-27
> **dragos240 said:**
> Agreed, looks like a kernel issue if you can't get into recovery mode, if not, it's something deeper.

I removed the last kernel aweek ago the update was for xorg or something to do with x

---

### Post by dragos240 on 2010-06-27
> **dave_man137 said:**
> I removed the last kernel aweek ago the update was for xorg or something to do with x

No old kernels work? That's peculiar, can you still boot off of a live cd? If you can do that, we can go from there.

---

### Post by dave_man137 on 2010-06-27
> **Rubi1200 said:**
> Hi,
can you run a LiveCD?
If so, see here and follow the instructions before posting back:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)


this is not working i'm in the live cd I get this bash [path/to/the/download_folder]/boot_info_script*.sh
bash: [path/to/the/download_folder]/boot_info_script*.sh: No such file or directory

---

### Post by dave_man137 on 2010-06-27
Fixed. Booted a live CD went into my ubuntu partition.  Found the X11 config.  Edit to vista driver (default) -> Hit 'save'.  This was done with gedit.  Saved.  Re-booted in recovery mode.  Then re-installed ATI driver then re-booted again and all is well. 

Thanks for everyone for all their help.  There may have been a better way to do this but this is the only way I could figure it out.  Once again, I hate ATI graphics cards.

---

