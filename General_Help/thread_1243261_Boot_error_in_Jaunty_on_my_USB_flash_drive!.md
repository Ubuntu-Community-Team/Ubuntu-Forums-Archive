---
title: "Boot error in Jaunty on my USB flash drive!"
date: 2009-08-18
forum: General Help
---

### Post by rogueleader12345 on 2009-08-18
Yesterday I was trying to get my Intrepid to recognize my Jaunty on my flash drive as a software source, so I moved the casper-rw file and the syslinux stuff off of it to make it just like the cd. It didn't work, so I put the files back on it. I come to boot into it today, I get the Live CD menu like normal, but then it just says "Boot error" and terminates. So, I have several questions.

1. Is it trashed, meaning, will I have to reload it?

2. If it is trashed, is there any way I can save my data that's on it? Like my packages, all my documents, etc.

3. If it's not trashed, how do I fix it?

Oh, this little tidbit might be helpful. I made it using the Create a USB Startup Disk in Ubuntu. Thanks!

---

### Post by kpkeerthi on 2009-08-18
No it is not trashed. You just can't move the files to your flash drive and try to boot off it. Use [unetbootin]("http://unetbootin.sourceforge.net/") to create a bootable 'Live' USB.

---

### Post by rogueleader12345 on 2009-08-18
I tried unetbootin before and it didn't work. Where is all the data stored? I think it's in the casper-rw file, but I'm not sure...

---

### Post by ptsubin on 2009-08-18
The USB Startup Disk Creator never worked for me, and it is always UnetBootin i have used. Are you syer you didn't make any mistake?

---

### Post by rogueleader12345 on 2009-08-18
I'm sure. When I loaded it up it flashed by and terminated. The thing with the one on Ubuntu is you have to clear all partitions and use an external iso, like one you downloaded, it won't work if you're trying to use one that's burned on a cd. Anyway, is it possible for me to reload it and just replace the casper-rw file with the one that has all my data? Or will it just cause the problem to reoccur?

---

### Post by rogueleader12345 on 2009-08-18
Or is the data somewhere else? Or might I be able to use a backup application to save all my data, reload Ubuntu, and then restore my data?

---

### Post by kpkeerthi on 2009-08-18
Are you trying to upgrade Intrepid to Jaunty?

---

### Post by rogueleader12345 on 2009-08-18
No. The flash drive had Jaunty on it, I'm just wondering if there's a way to save my data. My other computer has Intrepid.

---

### Post by rogueleader12345 on 2009-08-19
Is there anyone else who has any ideas?

---

### Post by kpkeerthi on 2009-08-20
It is not clear (atleast to me) what you are trying to ask/say. You may want to rephrase your query in simple terms.

---

### Post by rogueleader12345 on 2009-08-20
Ok. Sorry for any confusion. I know that I will have to reinstall Ubuntu, I would like to know if there is a way to save all my data, like my installed packages, my documents, my settings, etc. Hope that clears it up!

---

