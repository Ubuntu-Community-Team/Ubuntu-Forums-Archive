---
title: "&quot;An error occurred while extracting files.&quot;"
date: 2011-09-21
forum: General Help
---

### Post by The_Autonomist on 2011-09-21
For the longest time, i've been extracting my filed by dragging them into where i wanted them to be extracted. As of the last hour or so, i've trying to do the same thing with a few themes i've downloaded...to no avail. The error message:

> An error occurred while extracting files.

keeps popping up. 

At first, i thought it was because the downloaded file had been corrupted, but i tried it with a few other files already on my computer and i received the same message.

I can unpack the rar. or tar.gz file easily, by dragging the folder inside to whereever I want. But, once i attempt to extract whatever is in THAT folder, it won't let me do it. 

Does anyone know what is going on?

---

### Post by scarleo on 2011-09-21
Perhaps permissions problems. Are you the owner of the folder you are extracting to?

---

### Post by The_Autonomist on 2011-09-21
As far as i know, yes. I mean, i'm only trying to extract to a folder on my Desktop. 

But, how could i check if all of my permissions are in order?

---

### Post by The_Autonomist on 2011-09-21
I just checked my permissions under properties and I do indeed have full permissions...

---

### Post by The_Autonomist on 2011-09-21
It also won't let me even open the file or folder without giving me the same error message. Does anybody have any idea????????

---

### Post by .:Justus:. on 2013-02-10
I had this same problem.

This happened when I was trying to open a file within a folder in a zip archive.

For example I tried to open a file "document" in the folder "research papers" in the archive "College.zip".

However, since I hadn't extracted the zip yet I couldn't access it.

The problem was solved by simply extracting the whole "college.zip" folder and accessing the files within that way.

I hope this solves your problem!

Short version: Extract the biggest folder in the archive first and access the files within from the extracted folder.

---

### Post by elliotn on 2013-02-10
achieve could be corrupted

---

### Post by letsplayfootsy on 2013-02-10
open a terminal and enter
```

$ whoami
$ ls -ld ~/Desktop
$ cd ~/Desktop; ls -l

```

What is the output of these commands?

---

### Post by wildmanne39 on 2013-02-10
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

