---
title: "Creating a partition from a particular sector"
date: 2009-12-27
forum: General Help
---

### Post by kilee on 2009-12-27
Hi friends.
I'm trying to make a partition from sector "a" to sector "b". Let me explain.
I'm recovering my files from a 200 gb hdd. I spent 2 full days making it, and it was working like a charm. I recovered about 70% of the disk. BUT I had to terminate the program for reasons of no interest at all.

Now I do not want to start over. I haven't found any way to make photorec start searching for files from sector "a", and go on from there. 
So I believe It is possible to create a partition from this point to the end of the disk. Then I'd ask photorec to look for files within that partition.

Is there a wonderfull command or tool to do this?

Thanks in advance and happy holydays!

---

### Post by john newbuntu on 2009-12-28
You can use the "dd" command specifying the skip option and probably other options like notrunc and noerror to copy portions of the disk to a file.  You could then mount the file as a loopback device.

---

### Post by kilee on 2009-12-28
Thanks John!

I'll try. If succeed I'l post the results.

---

