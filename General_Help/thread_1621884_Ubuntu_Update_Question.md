---
title: "Ubuntu Update Question"
date: 2010-11-14
forum: General Help
---

### Post by TheMixtureMedia on 2010-11-14
Ok so here is what I am wanting to do. I have alot of new PPA's in Ubuntu Update. I am wanting to put them PPA's onto other computers. I am not sure what file it is I am looking for so I can put the file on other computers. Also the computer with all them PPA's are on a 64 bit computer could I put that file on a 32 bit computer and still get all them PPA's??

---

### Post by dcstar on 2010-11-15
> **TheMixtureMedia said:**
> Ok so here is what I am wanting to do. I have alot of new PPA's in Ubuntu Update. I am wanting to put them PPA's onto other computers. I am not sure what file it is I am looking for so I can put the file on other computers. Also the computer with all them PPA's are on a 64 bit computer could I put that file on a 32 bit computer and still get all them PPA's??

PPAs are irrelevant to 32 or 64-bit, the PPA repository will have separate trees for each architecture.

If the PPA maintainer does not provide packages for an architecture then that is just bad luck.

---

### Post by TheMixtureMedia on 2010-11-15
That's fine and all but is there a file that contains the files I need to trasnfer to another computer with out rewriting the ppa's over again.

---

### Post by plucky on 2010-11-15
> That's fine and all but is there a file that contains the files I need to trasnfer to another computer with out rewriting the ppa's over again. 


You should find all the PPA list files in **/etc/apt/sources.list.d** if you added them properly.

Good Luck

---

### Post by TheMixtureMedia on 2010-11-15
Thank you very much and could I put that file onto another computer so that computer would have them ppa's??

---

### Post by dino99 on 2010-11-15
as it is a text file, yes you can, only change the release if you need of course

---

### Post by TheMixtureMedia on 2010-11-15
Great thank you all for your help :-)

---

