---
title: "Best search tool"
date: 2010-11-06
forum: General Help
---

### Post by rmcellig on 2010-11-06
I need to be able to search for files on all of my drives at the same time as well as text within the files. What is the best tool for me to use, that comes close (or even surpasses) to the Mac way of searching?

---

### Post by Barriehie on 2010-11-06
> **rmcellig said:**
> I need to be able to search for files on all of my drives at the same time as well as text within the files. What is the best tool for me to use, that comes close (or even surpasses) to the Mac way of searching?

I'm familiar with locate and find, I mostly use find; it has a much wider scope of selection than locate.  I just tested on my machine and by starting at root it will search all drives as it comes across them.  Grep is probably your best option for finding text within the files.

```

find <path> <options> | xargs grep <text_2_find>
```

My $HOME is about 1 gig and that just found all php files with 'forums' in them faster than I can blink.

HTH

---

### Post by I'mGeorge on 2010-11-06
> **rmcellig said:**
> I need to be able to search for files on all of my drives at the same time as well as text within the files. What is the best tool for me to use, that comes close (or even surpasses) to the Mac way of searching?

the locate command

---

### Post by rmcellig on 2010-11-06
I need a GUI solution. Is there anything out there that are front ends for Grep, Locate and Find commands?

---

### Post by Barriehie on 2010-11-06
> **rmcellig said:**
> I need a GUI solution. Is there anything out there that are front ends for Grep, Locate and Find commands?

oops, I'm predominately CLI...

---

### Post by Verbeck on 2010-11-06
what about the normal search? places>search for files
you can set the parameters for the search as 'contains the text' etc..

p.s. i dont know the mac way of searching

---

### Post by rmcellig on 2010-11-06
I can use that but I am not sure how to search all devices I have attached to my computer. Does this search tool have an index created alredy allowing for fast searches within files.

I remember older distros of Ubuntu had an idexing option that allowed the user to create a search index. I am using Ubuntu 10.10 and am not sure where to go to create the index, or was that removed from this latest version?

---

### Post by oldos2er on 2010-11-06
> **rmcellig said:**
> I need a GUI solution. Is there anything out there that are front ends for Grep, Locate and Find commands?

Catfish.

---

### Post by thehipho on 2010-11-06
Give SearchMonkey in the repos a try, it got lots of options. 
Or just use the Gnome Search Tool.

```

sudo apt-get install searchmonkey

```

---

