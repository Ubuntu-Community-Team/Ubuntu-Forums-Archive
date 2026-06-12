---
title: "Deleting the Windows partition"
date: 2012-04-10
forum: General Help
---

### Post by TheNessus on 2012-04-10
Hi all,

I have a windows partition, which is about 200gb. It is where I store all my music, photos, etc. I don't have an external HD, and my /home is only about 30GB. 

I realized I don't use my W7 at all, and all my dealings with MS Office are done in virtualbox anyway.

So I decided that I will just delete all the content on my windows partition, except for my personal data such as music and photos.

But, forgive me for my noobishness - it's not as effective as backing up my stuff, formatting the partition, and putting my stuff back up there, right? what are the disadvantages here with deleting compared with formatting?

---

### Post by Basher101 on 2012-04-10
deleting = you get rid of selected files (but maybe not all)
formatting = deletes EVERYTHING.

---

### Post by TheNessus on 2012-04-10
> **Basher101 said:**
> deleting = you get rid of selected files (but maybe not all)
formatting = deletes EVERYTHING.

Yea, exactly. There's residue and stuff that will still be there no matter what?

---

### Post by bedpotato on 2012-04-10
Well I am no expert at all but it seems rather daft to me to have a second OS being used solely for the purpose of data storage. USB drives are really cheap these days if you don't want to buy an actual HD.

Whatever you decide, back up your photos and music if they're important to you! Data is so easily lost or stolen. :(

---

### Post by Basher101 on 2012-04-10
the only thing that comes to my mind to reduce "residue" is to run Defragmentation 1-2 times before normally deleting the unneeded files

---

### Post by jwbrase on 2012-04-10
> **TheNessus said:**
> Hi all,

I have a windows partition, which is about 200gb. It is where I store all my music, photos, etc. I don't have an external HD, and my /home is only about 30GB. 

I realized I don't use my W7 at all, and all my dealings with MS Office are done in virtualbox anyway.

So I decided that I will just delete all the content on my windows partition, except for my personal data such as music and photos.

But, forgive me for my noobishness - it's not as effective as backing up my stuff, formatting the partition, and putting my stuff back up there, right? what are the disadvantages here with deleting compared with formatting?

Well, as long as you continue to not have any backup medium (external HD or something of the sort), deleting unnecessary files instead of reformatting is probably the better solution. There's a risk of data loss any time you repartition your drive, so it's risky to do without doing a back up. Even if you did have a backup medium, Linux's NTFS support is good enough that reformatting the partition to ext3/ext4 probably wouldn't be worth the trouble (actually, what I'd probably do, depending on the exact existing partitioning scheme, would be to totally get rid of the NTFS partition and grow your home partition over it, but it still probably wouldn't be worth the trouble).

---

### Post by TheNessus on 2012-04-10
> **jwbrase said:**
> Well, as long as you continue to not have any backup medium (external HD or something of the sort), deleting unnecessary files instead of reformatting is probably the better solution. There's a risk of data loss any time you repartition your drive, so it's risky to do without doing a back up. Even if you did have a backup medium, Linux's NTFS support is good enough that reformatting the partition to ext3/ext4 probably wouldn't be worth the trouble (actually, what I'd probably do, depending on the exact existing partitioning scheme, would be to totally get rid of the NTFS partition and grow your home partition over it, but it still probably wouldn't be worth the trouble).
Yeah, I have that external HD loaned somewhere by a person I haven't seen for over a year. Hmm. Expanding /home is exactly what I wanna do in the end. Right now it's all fragmented, this is there, that is here, meh. so annoying.

---

