---
title: "How can I use a concurrent boot with Ubuntu 10.04??"
date: 2010-08-01
forum: General Help
---

### Post by csuarezmtz on 2010-08-01
Hi!!!
Thank you or reading this!

I have a dual core processor and would really like to take full advantage from it. I'm pretty sure that only one core is being used when booting and I would like ti know if this is true for the rest of the laptop usage.

Furthermore, I tried to follow a tutorial in order to edit 

/etc/init.d/rc
*****Tutorial indicated that one could get the concurrency by changing the value CONCURRENCY=none  to  CONCURRENCY=shell  however the file clearly says that "shell" is not a valid option, so I made no change.

Anyone knows how to solve this?? I've already googled it but found no solution.

Thx a lot!!!

---

### Post by dino99 on 2010-08-01
dont try to fix what is not broken ;)

on multi cores, each process is assigned to a core, and they work alternatively for temperature and charge reason, thats the way all OS works

---

### Post by csuarezmtz on 2010-08-01
I've just found some sort of solution, but I would really like the opinion of someone who knows how to work on Ubuntu (I don't). I post the link [http://portalubuntu.blogspot.com/2010/05/acelera-el-arranque-de-ubuntu-en.html](http://portalubuntu.blogspot.com/2010/05/acelera-el-arranque-de-ubuntu-en.html) (it's in Spanish, but google translate should make the difference).

They basically tell you to make use of "insser" and the use the next commands.

sudo update-bootsystem-insserv
sudo sed -i 's/CONCURRENCY=none/CONCURRENCY=startpar/g' /etc/init.d/rc
sudo sh -c "echo 'CONCURRENCY=startpar' >> /etc/default/rcS"

Is that okay?? or may this commands break things down??

Thx again!!!

---

### Post by jerenept on 2010-08-01
In booting, boot up speed is only really affected by hard drive speed; "Utilising both processors" will probably make zero difference.

EDIT: Ubuntu automatically takes full advantage of ALL processor cores!

Tinkering with system files is a BAD idea unless you know what you are doing!

---

### Post by dcstar on 2010-08-01
> **jerenept said:**
> In booting, boot up speed is only really affected by hard drive speed; "Utilising both processors" will probably make zero difference.

EDIT: Ubuntu automatically takes full advantage of ALL processor cores!

Tinkering with system files is a BAD idea unless you know what you are doing!

+1

Believing that booting is a CPU bound process is basically an admission that someone has no understanding whatsoever about what happens during the booting phase.

If you want fast booting then you get a fast boot device like a SSD (which I have, and Ubuntu boots in seconds).

---

