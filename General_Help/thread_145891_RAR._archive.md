---
title: "RAR. archive"
date: 2006-03-17
forum: General Help
---

### Post by Darkness3477 on 2006-03-17
Hi, I have a few .RAR files (mostly ebooks and the likes), that I compressed on my other computer (it has XP on it), and now I want to read a few of them, but when I try to open it, I get a message telling me the archive type is not supported. Now, it wouldn't be much of a problem if I only had one or two files I wanted to open, but there is about 20 of them.  

Anyway, I am basically looking for a program that will let me open my .rar files. A program that is hopefully in the repositories, as I hate having to compile them myself, as things always seem to go wrong.

---

### Post by dermotti on 2006-03-17
EDIT
[B]
sudo apt-get unrar-free[/B]

try that.

theres also 

**sudo apt-get unrar-nonfree ** for rar 3.0 rar files.

---

### Post by Darkness3477 on 2006-03-17
Damnit! I actually have a book that I really want to read now.... Was going through checking which ones that were .rar's, and I found one which I only read a small section of, and now I want to read the rest...

Anyway, thanks for your help, but...Heh, didn't actually help, but thanks for trying!

---

### Post by dermotti on 2006-03-17
Lol i edited my post, see if those packages help

---

### Post by Darkness3477 on 2006-03-17
Thank you so much! The seond option (nonfree) worked! I can now scratch that learning itch with this ebook!

P.S. They need some sort of thanks and rep system here like they have on ITFreaks.

---

### Post by SerafeimG on 2007-12-07
Hallo!
I have installed the unrar package through Synaptic.
Now my desktop (Xubuntu) can recognize the rar files as a type of archive but i can't read and extract them correctly. Can you help??

---

### Post by mali2297 on 2007-12-07
> **SerafeimG said:**
> Hallo!
I have installed the unrar package through Synaptic.
Now my desktop (Xubuntu) can recognize the rar files as a type of archive but i can't read and extract them correctly. Can you help??

Try to extract them in **xarchiver**. 

If that doesn't work, try extracting from the terminal:
```

unrar e example.rar

```

---

### Post by Wolf78 on 2007-12-20
> **mali2297 said:**
> 
```

unrar e example.rar

```

So where did they go? I ran that command, got the message they were extracted but can't find them anywhere...tried locate and find commands, nothing shows

---

### Post by Wolf78 on 2007-12-20
Sorry I installed unrar-free, not unrar...but the question remains

---

### Post by mali2297 on 2007-12-20
> **Wolf78 said:**
> So where did they go? 

They should be extracted to the present working directory, run **pwd** to see what it is. I suggest that you open the file manager and look around.

---

### Post by Wolf78 on 2007-12-20
Thanx, I found them in the mean time...forgot to check the home dir :)

---

