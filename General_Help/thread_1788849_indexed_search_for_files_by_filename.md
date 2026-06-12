---
title: "indexed search for files by filename"
date: 2011-06-23
forum: General Help
---

### Post by Didge on 2011-06-23
Is there really no way of having with a GUI an indexed file search by filename (not contents etc) which gives a detailed list? Great big icons as a "result" is no good to me, I want "details" that I can then click on to either open or copy etc. I tried the totally useless "Tracker" and Zeitgeist in my 11.04 is no better. 

There is a fantastic product in the win environment called everything.exe which does exactly what I want. I cannot be alone in this type of requirement. It has to have a GUI.

I have TB's of data on both ext4 and NTFS partitions.

---

### Post by dino99 on 2011-06-23
are you not satisfied with nautilus+xapian ?

---

### Post by vanadium on 2011-06-23
In the dash, type "search" to lauch "Search for files". This will likely do what you are looking for.

---

### Post by Didge on 2011-06-23
Thank you Dino99, I haven't had a look at that yet! 

The file search in Nautilus is not indexed as far as I can see. When you say +xapian, what do you mean?

---

### Post by Didge on 2011-06-28
Referring to my own original post:
"an indexed file search by filename"

Any ideas anybody? 

Nautilus search is not indexed. Leastways, mine isn't.

---

### Post by vanadium on 2011-06-29
Referring to my original post, yes, it is indexed as it uses locate behind the scenes. Or I might not understand your question well.

---

### Post by rg4w on 2011-06-29
> **Didge said:**
> There is a fantastic product in the win environment called everything.exe which does exactly what I want. I cannot be alone in this type of requirement. It has to have a GUI.
I was tempted to write one, but I can't believe there isn't such a gadget already.

I suspect there is; haven't spent much time looking into it myself (I don't actually need one, I just find indexing an interesting exercise).

Watching this thread with interest....

---

### Post by vanadium on 2011-06-30
Curious. It is like I am the only one seeing my posts. In asfar as I can tell, gnome-search-tool provides a graphical interface and uses among other utilities "locate" as backend. Taking a test, I see a lot of files thrown out very fast - likely what is provided by locate, after which the utility continues using find.

I do not want to nag, but I would like to know if I completely misunderstood the question, or why otherwise the gnome-search-tool would not satisfy the request.

Needles to say, I am not familiar with the everything.exe utility in Windows.

[Edit]I found it here [http://www.voidtools.com/](http://www.voidtools.com/). The interface looks deceptively like gnome-search-tool. However, unlike gnome-search-tool, the utility shows up everything when launched, and filters the results as you type.

---

### Post by Didge on 2011-07-05
Whilst the search in Nautilus does sort of work I just want to search for filenames, not content. I have TB's of files and a search for "notes" would bring up 1000's of files instead of maybe 100.

I think you get the drift of the voidtools product where there is a db of filenames and locations and you filter the result. It is, to all intents and purposes, instantaneous.

If Nautilus is using locate then can I stop it searching for content? Maybe that is my solution.

---

### Post by Didge on 2011-07-21
Bump.

---

### Post by SeijiSensei on 2011-07-21
Locate only indexes file names.  It ignores the files' contents entirely.

---

### Post by Didge on 2011-07-25
I am dreading the thought of having to go back to Windows 7 but not having a straightforward gui that gives me a list of filenames quickly is going to be the cause.

I Do Not want every file containg "txt" to be listed but only files that have "txt" in the filename. There just has to be something out there. The cli is great for getting a list using locate but then I can't "manage" those files.

Surely you understand? No?

---

### Post by Didge on 2011-07-26
Here is as close as I could get in case it helps anybody.

Locate indexes filenames and locations. Let's use it.

By default the /media path is excluded from the Locate indexer updatedb. That means my NTFS drives were not being indexed so I mounted them elsewhere, in /mnt/ using fstab. We do not want temporary drives indexed which is why this needs to be done.

I installed Catfish and changed the options so it uses locate as the default method and filesystem as the base directory for the search. Nobody here mentioned Catfish. Is there something better?

It is a start.

---

### Post by vanadium on 2011-07-26
I have already mentioned the default gnome search tool, which provides a list of files in a gui that you can manage. It uses locate and find in the background. At first, files appear quick as they are provided by locate. then the tool continues searching the drive with find.

---

### Post by Didge on 2011-07-27
Yes, you did Vanadium. Thanks. It is, now that I realise the limitations of the locate /media mounted volumes index working like the coffee solution. Still not quite what I am after but hey ho!

---

