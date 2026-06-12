---
title: "ppt viewer"
date: 2010-02-11
forum: General Help
---

### Post by wlagaert on 2010-02-11
Hello,

While searching on google I found this: [http://http.us.debian.org/debian/pool/non-free/p/pptview/](http://http.us.debian.org/debian/pool/non-free/p/pptview/)

Now I have some questions:

1) Does it need Wine. I read somewhere about a powerpoint viewer that had to be running in Wine

2) Can you start a presentation directly from the command line (don't ask why, I just need to)? I had a sollution with openoffice impress (you can start a ppt with that program using a single command line. But I'm searching for a better solution)

3) If the answer is of 2 is yes, where can you find the commands I can use?

---

### Post by auh2o on 2010-02-11
My bad. It does indeed require Wine. Per Synaptic:

**Depends**: wine
**Suggests**: openoffice.org-impress

---

### Post by wlagaert on 2010-02-11
Nice, and does anyone know about the command-line? It just needs to start a presentation (in a loop)

---

### Post by scouser73 on 2010-02-11
> **wlagaert said:**
> Hello,

While searching on google I found this: [http://http.us.debian.org/debian/pool/non-free/p/pptview/](http://http.us.debian.org/debian/pool/non-free/p/pptview/)

Now I have some questions:

1) Does it need Wine. I read somewhere about a powerpoint viewer that had to be running in Wine

2) Can you start a presentation directly from the command line (don't ask why, I just need to)? I had a sollution with openoffice impress (you can start a ppt with that program using a single command line. But I'm searching for a better solution)

3) If the answer is of 2 is yes, where can you find the commands I can use?

It's Microsofts' own Power point viewer.

I installed this to see if it needed WINE and yes it does need WINE (which is installed when you download the .deb file) **pptview_8.0-6_i386.deb**

---

### Post by wlagaert on 2010-02-11
Damn.

I don't want to use wine. Is there any program that does the same thing but doesn't need wine?

---

### Post by SecretCode on 2010-02-11
99% sure your choices are pptview with wine, or OOo Impress.

---

### Post by wlagaert on 2010-02-12
Would be something like that be possible in another format (pdf, ...). And is there a way to convert ppt to that format using command line?

---

### Post by SecretCode on 2010-02-12
Google has lots of results for "convert ppt pdf linux command". I don't know which would work best for you.

---

