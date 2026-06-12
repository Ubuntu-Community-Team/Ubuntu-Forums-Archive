---
title: "How can you read files in your linux partition from windows?"
date: 2010-03-23
forum: General Help
---

### Post by Eoghanalbar on 2010-03-23
[Sorry if this is misplaced; I just couldn't think which category to put it under.]

So yeah, I'm almost exclusively using karmic (yay!:D), but I still have to use that vista install I have smushed in a corner of my HD from time to time.

Now, I installed karmic using the default, latest file system (ext4, I believe it is, right?).

Last I remember hearing, that presents a bit of a problem, doesn't it?

So what can I do?

---

### Post by akand074 on 2010-03-23
Windows/NTFS does not recognize EXT4 and earlier, JFS, XTF, ReiserFS, or any other filesystem most commonly seen in unix-based operating system. Though there are third party software that allows you to do so, as I've heard. Unfortunately I don't know of any off hand, I would google around for one in the mean time while perhaps someone else could give you an idea.

---

### Post by kenny2009 on 2010-03-23
Give [this]("http://www.howtoforge.com/access-linux-partitions-from-windows") a try. I haven't tested it so I can't say if it will work.. but I do not believe that it will cause any harm.


[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

---

### Post by Eoghanalbar on 2010-03-23
Ah yes, thanks Akand. The problem is that when you google for the words 'vista'/'windows' and 'ext4', you mostly get old pages telling how to access ext2/3, with notes or comments saying 'doesn't work with ext4'... hence why I thought it might be a good idea to ask in a new thread. Catch all the latest info floating by from intelligent humans who understand more than keyword matches. :P

And thanks Kenny, but that link seems to be one of those pages where the only place 'ext4' is mentioned is in the comments, saying it doesn't work with the method the page describes.

Here's another question, if I try one of these things and it doesn't work, how possible is it that the failure mode might involve messing up my whole file system (in either partition)?

---

### Post by Eoghanalbar on 2010-03-23
Oh actually, a better question:

Seeing as it's not really possible to access ext4 from windows, what're some good ways one might work AROUND this?

For example, thoughts on how best to create a separate partition to share between the two OS's.

I don't know about you, but I prefer to have all MY stuff (music, videos, pictures, and documents that I'm attached to) in a single super-folder to facilitate back-ups and moving between different computers.

---

### Post by ron999 on 2010-03-23
Yes you can create a new partition and format it ntfs.
Then you can access it from Windows or Linux.
Use gParted to do this, it's in Ubuntu's repository.

---

