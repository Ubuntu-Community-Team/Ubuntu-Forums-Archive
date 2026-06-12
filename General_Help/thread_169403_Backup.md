---
title: "Backup"
date: 2006-05-02
forum: General Help
---

### Post by 33125416 on 2006-05-02
I need some software to backup WindowsXP before I install Ubuntu.  Can any of you suggest some programs to do this?

---

### Post by el3ktro on 2006-05-02
I don't know of any free (as in beer) tools to do that, but you might look at Norton Ghost for example.

Tom

---

### Post by 33125416 on 2006-05-02
Thanks.  Is it really neccesary to backup before installing linux?

---

### Post by 33125416 on 2006-05-02
And, my computer has two hard drives, one where windows is installed and another for everything else.  Seeing as I'm keeping windows, should I install it on the hard drive with windows or the other one?

---

### Post by el3ktro on 2006-05-02
Hello,
well it depends. I suppose you want to have Windows & Linux installed side-by-side. In this case, you have to re-partition your harddisk, to make some room free to install Linux. In 99,9% of all cases this works just fine, but it is kind of a dangerous operation to do, so it's always a good idea to have a backup. Ths has nothing to do with Linux though, it's just that re-partitioning a harddrive may cause harm, but don't worry this is very unlikely.

If you install Linux on your 1. or 2. harddisk really depends. What sizes are your harddisks and how many/how large partitions do you have on them?

Tom

---

### Post by 33125416 on 2006-05-02
The hardrive with windows on it is only 4 gigs, and the other one is 80.  I haven't made any partitions yet because the site I looked at for installing said I didn't need to make any.  I guess cause linux makes it's own?

---

### Post by 33125416 on 2006-05-04
Ok, I got through all those other problems.  Now I need help making a partition, :p .  I was trying to make one through the ubuntu installer but it's really confusing, can anyone help me?

---

### Post by brotakul on 2006-07-27
first, you have to choose a manually partitioning. otherwise ubuntu can format your whole harddrive!
so, you need 2 partitions for linux. one for the os[about 10GB should be enough] and one for swap[512MB-you have to check it as swap].
you can format the system partition [the 10GB one] with ext3. then check it as root ["/"]. 
then apply the changes and you're done. if something's wrong, the installer will let you know.
good luck.

---

