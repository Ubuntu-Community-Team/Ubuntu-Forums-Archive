---
title: "What it means to have an encrypted drive?"
date: 2011-04-06
forum: General Help
---

### Post by X10A on 2011-04-06
In disk usage analyser, I see that under home, I have my user folder which is about 50 GB. But for some reason, there is another equally big folder called "ecryptfs". When I installed ubuntu, I selected the encrypt hard drive option. How is this encryption when it seems like the space is just being replicated? And if I want to free up the 50 GB of space taken up by "ecryptfs", how do I do it?

---

### Post by 3Miro on 2011-04-06
In encryption you have one large file, which is all the encrypted data. That file is then mounted as the regular folder. Basically the two things are two instances of the same, one encrypted one unlocked. Only encrypted data is written on the HDD, the unencrypted one is in RAM only (and only part of it).

---

### Post by techunit on 2011-04-06
If you set your home directory as being encrypted during the install your home directory can only be unlocked by your password at log-in. So running the disc usage analyzer will likely report an inacurate file size. This is normal and to be expected. With out having it unlocked your home directory will appear to be filled with static.

---

### Post by X10A on 2011-04-07
Thanks.   So it means that if someone took apart my HD without me knowing, it'll be harder for them to pry into my data?

---

