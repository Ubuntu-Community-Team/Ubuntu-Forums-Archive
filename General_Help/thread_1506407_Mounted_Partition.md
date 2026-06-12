---
title: "Mounted Partition"
date: 2010-06-10
forum: General Help
---

### Post by novatax on 2010-06-10
I have /storage as second partition of harddisk to store all my files mounted on /media/storage. Is it means that even I store my files in /storage, it will fill the filesystem partition to?

---

### Post by ersi on 2010-06-10
See the partition as an own harddrive. If you fill /media/storage and there's no space left on that partition, you can't put in new files. But your regular system partition will continue working. 

Please describe more what you wanted to know, if I missunderstood you

---

### Post by novatax on 2010-06-10
Sorry, I'm a bit confused.
I only have 2 partitions, filesystem (/) and storage (/media/storage). Just like drive C and D (documents) in windows.
I find that all my files I stored in storage partition were also in filesystem /media/storage to.
So, is it means that all my files in storage partition also "real" in filesystem partition? Because I'm affraid that would reduce the filesystem partition size..

---

### Post by ersi on 2010-06-10
If you fill the 'storage' partition, only that will be filled. It won't flow over to your / partition and make that smaller. You could see /media/storage as "D:". If you'd fill it up, you will be unable to save more files to anywhere beneth /media/storage/ but all other locations are still on your /-partition, so you'll still be able to save files there. 

It's a bit complicated to form into a nice sentense or two. There is a lot of reading material online about how the Linux filesystems/layouts work. I've searched up two articles that may be nice reading. I'm not totally sure, since I havn't verfied it fully. These might give you some more insight:
[http://www.linuxpronews.com/linuxpronews-55-20080610OnaLinuxSystemEverythingisaFile.html](http://www.linuxpronews.com/linuxpronews-55-20080610OnaLinuxSystemEverythingisaFile.html)
[http://www.linux.org/lessons/beginner/l4/lesson4e.html](http://www.linux.org/lessons/beginner/l4/lesson4e.html)

---

### Post by novatax on 2010-06-10
So it means that my storage files in filesystem was just like link?

---

### Post by cbecker78 on 2010-06-10
I think you may just be confused.  It sounds to me like you have a partition called storage, and it is being mounted as /media/storage.

Edit: didn't see the last two posts at time of writing the above.  I think the answer to your question is yes, but I'll let ersi confirm that as he seems to have a better idea of what you are describing.

---

### Post by novatax on 2010-06-10
I see now.
Just realize when I open /media/storage, the partition highlights on side pane of nautilus moves from filesystem to storage..:tongue:
Thanks guys, sorry for the troubles..

---

