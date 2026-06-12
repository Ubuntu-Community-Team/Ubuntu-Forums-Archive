---
title: "ext3 to ext4"
date: 2009-09-04
forum: General Help
---

### Post by rahilm on 2009-09-04
hello..
i am thinking of switching from ext3 to ext4. Is it worth it?
and how do i do it without destroying my current settings and installed applications?

---

### Post by defacto on 2009-09-04
Some say that it's running just fine, however, I've had issues with it's stability. 
To upgrade from ext3, follow the guide @ [http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto) ( scroll down to the last section ).

---

### Post by rahilm on 2009-09-04
what kind of issues??

---

### Post by P4man on 2009-09-04
If it aint broken, dont fix it. there is very little to be gained from going to Ext4, especially when you dont do a fresh install, because then the performance benefits, however humble, aren't there.

If you do a fresh install one day, you could consider it. I think it shaved a few seconds from my boot time, but nothing i would notice without a stop watch.

---

### Post by QIII on 2009-09-04
I think the big concern initially with ext4 was with the manipulation of large files if there is system crash mid-copy.  Don't know if that is resolved.

Karmic uses ext4 by default, so consider that if you do a clean install when it comes out. 

I haven't run into any problems yet, but I haven't expressly tested the large file issue.

(BTW, Karmic Alpha 5 seems to portend well for the final release...)

Edit:  Just checked.  There are some patches regarding the ext4 write issues in the generic 2.6.30 kernel, which comes with Karmic.  Ubuntu added the patches to the 2.6.28 kernel in Jaunty.

---

### Post by sasho_zl on 2009-09-04
A month ago because of a system crash caused by a known ext4 bug I lost all my documents and photos. It still has a lot of bug fixing to go through before it is safe. I would recommend that you wait until the official Karmic release and then migrate to that FS.

---

### Post by rahilm on 2009-09-05
thanx. i'll wait till KK releases

---

