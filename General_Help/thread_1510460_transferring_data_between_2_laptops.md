---
title: "transferring data between 2 laptops"
date: 2010-06-15
forum: General Help
---

### Post by pr0t3g3 on 2010-06-15
I would like to transfer a massive amount of data between my laptops simultaneously.  Is there a way to attach a cable via one flash port on one laptop to another and transfer like that?  I don't really even know whether or not I'm asking the right question, or if I'm even in the right forum, but this was the best I could do.  Any suggestions or advice for a transfer such as that?

---

### Post by cariboo on 2010-06-15
Use a crossover network cable between the to laptops. Make sure the ip addresses are in the same netblock ie: 192.168.0.1 - 192.168.0.254. 

One way to transfer the data is to install openssh-server on the laptop with all the data that needs to be transfered, then use something like Filezilla, or even nautilus to transfer the files, using sftp to download the files.

---

### Post by pr0t3g3 on 2010-06-15
Why can't I just plug in a 2 way flash-drive-like cable?  is it because it wouldn't know what to do?  What I mean to say is:  Is there a way to do* that* and have a space appear between those drives where I can put files that are seen by both laptops in their respected port folder locations?

---

### Post by pr0t3g3 on 2010-06-20
kay..  the above comment must have sounded noobish.. but I don't have time to search for the answer that cariboo gave me.  Can someone either dum what he said down or direct me to a place where I can look at leisurely?  Cross-over network cable?  netblock?  open ssh server?  Forgive me but I've never heard of some of those names before, and I don't have time to hunt down the defs!

---

### Post by spcwingo on 2010-06-20
You can do it with one of these:

[http://www.belkin.com/iwcatproductpage.process?product_id=275561]("http://www.belkin.com/iwcatproductpage.process?product_id=275561")

---

