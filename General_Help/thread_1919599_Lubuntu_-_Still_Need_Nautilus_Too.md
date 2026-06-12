---
title: "Lubuntu - Still Need Nautilus Too?"
date: 2012-02-03
forum: General Help
---

### Post by 2CV67 on 2012-02-03
As a fresh convert to Lubuntu after disappointment with Unity & Classic, I am still feeling my way around, not helped by the relatively sparse documentation.

I like the snappy & simple File Manager (PCManFM 0.9.9 in my case) - at least for most of the time.

But I still have to resort to Nautilus for some tasks.
Not a problem, as I have an icon for that on top panel, but I am posting to find out if I can/could manage without Nautilus.

Jobs I have needed Nautilus for:
1. Searching - I also found Catfish which works well, but is there a search function in PCMan?
2. Seeing Network - I found if I added Network as a bookmark in Nautilus, then it appeared as a bookmark OK in PCManFM too, so my problem is fixed, but was there another way for somebody without Nautilus?
Ah - while writing this I just found I can do Go > Network Drives, but I don't know if that is a result of my new bookmark or if it was always there & I hadn't seen it...
3. Open as Administrator - haven't found how to do that.
4. Nautilus Actions (launch scripts by right-click). Is there an equivalent?
5. Root Nautilus?

Please note: 
I am not complaining about PCManFM - it pleases me most of the time.
I am not suggesting adding extra bloat - that's what Lubuntu is all about, after all.
I am just asking if some of this stuff is already there & I just haven't found it yet!

One good recent improvement in Nautilus has been that it now lists hidden files below normal files, which I find much more convenient.
Any way to do that in PCManFM?

Thanks!

---

### Post by Rodney9 on 2012-02-03
1. No, good find on Catfish
2. Always there
3. Go to PCManFM Tools / Open Current Folder As Root
4. No, but you can open the current folder in terminal and run scripts there.
5. Not sure, I don't use Nautilus, but maybe in the terminal 'sudo nautilus'

For Lots Of Documentation, How-To's, Information and Screen-Casts on Lubuntu go to the

Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by 2CV67 on 2012-02-03
> **Rodney9 said:**
> For Lots Of Documentation, How-To's, Information and Screen-Casts on Lubuntu go to the

Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney
Been there - Done that!
I actually read the whole thread & a lot of the links...
Congratulations for that effort!

Thanks for the short, sharp answers on the other points.
I count 1 & 2 & 3 as [SOLVED] 
Can't think how I didn't find "Open as Root"... :redface:

Thanks again!

---

### Post by 2CV67 on 2012-02-18
One other thing I find myself still using Nautilus for, is picking deleted items from the trash can.

Nautilus lets me sort items by deletion date, which is often the most relevant method, but I haven't found how to do that with PCmanFM.

---

### Post by Rodney9 on 2012-02-18
> **2CV67 said:**
> One other thing I find myself still using Nautilus for, is picking deleted items from the trash can.

Nautilus lets me sort items by deletion date, which is often the most relevant method, but I haven't found how to do that with PCmanFM.

In PCmanFM select Trash then View - Sort Files

Rodney

---

### Post by 2CV67 on 2012-02-19
> **Rodney9 said:**
> In PCmanFM select Trash then View - Sort Files

Yes, but that only allows sorting by modification time, not deletion time.
Some files I deleted yesterday have last modification dates in 2009.

---

### Post by MG&amp;TL on 2012-02-19
Searching-you can add the lubuntu-desktop PPA and install the experimental lxfind, which is quite cool.

Anything graphical as root should be (for instance):

```
gksu nautilus
```

---

### Post by 2CV67 on 2012-02-19
> **MG&TL said:**
> Searching-you can add the lubuntu-desktop PPA and install the experimental lxfind, which is quite cool.

I seem to already have that one, but had not previously noticed it!

Actually, I prefer Catfish, quite the best & fastest search tool I ever tried.

---

