---
title: "Extracting pax.gz"
date: 2010-04-21
forum: General Help
---

### Post by sarin_cv on 2010-04-21
I have some archives with the extension pax.gz. I think it is the mac archive format... is there anyway to extract the files in Ubuntu?

---

### Post by Portmanteaufu on 2010-04-21
Yup yup. You'll need 'gunzip' and 'pax', both of which you should be able to install from the repositories.

```

gunzip yourfile.pax.gz

```
will produce 'yourfile.pax'. You can then use the pax program to extract yourfile.

Here's the [usage information for pax.]("http://www.computerhope.com/unix/upax.htm")

Post again if you get stuck or are unfamiliar with installing from the repositories.

---

### Post by sarin_cv on 2010-04-21
k... i will try this when I reach home and let u know...

---

### Post by sarin_cv on 2010-04-22
gunzip worked and it generated the .pax file. But when doing a pax -r Archive.pax, it goes on idefenitely without any message.

---

### Post by Portmanteaufu on 2010-04-22
Hm -- if you just run 

```
pax archive.pax
```

does it print the table of contents properly?

I haven't used pax before, so I'm winging it here. How big is the archive file? Is it big enough that it might take a long time to extract?

---

### Post by Portmanteaufu on 2010-04-22
Oh, it looks as though you might have to use the '-f' flag to specify the input filename.

```
pax -r -f archive.pax
```

---

### Post by sarin_cv on 2010-04-22
it is a 2 GB file... it would not take 8 hours for extracting anyways..

---

### Post by sarin_cv on 2010-04-22
```
sarin@sarin-laptop:/media/Videos$ pax -r -f Archive.pax 
pax: Failed open to read on Archive.pax: Value too large for defined data type

ATTENTION! pax archive volume change required.
Ready for archive volume: 1
Input archive name or "." to quit pax.
Archive name >

```

---

### Post by Portmanteaufu on 2010-04-23
Unfortunately I'll have to join you in hoping for someone that's more knowledgeable regarding pax than I am.

I have heard, though, that 7zip can open old pax files. Maybe it'd be worth giving that a shot? I'm pretty sure it's in the repositories.

---

### Post by sarin_cv on 2010-10-19
digging out an old post... still got no solution for this...

---

