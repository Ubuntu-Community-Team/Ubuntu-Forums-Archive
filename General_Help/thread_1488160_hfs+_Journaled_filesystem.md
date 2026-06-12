---
title: "hfs+ Journaled filesystem"
date: 2010-05-19
forum: General Help
---

### Post by taunnt on 2010-05-19
Does 10.4 support writing to hfs+ journaled filesystems? If so how do I go about enabling write to a hfs+ partition?

Thanks

---

### Post by albesan on 2010-06-15
bumping it. same problem here

---

### Post by timbosity on 2010-07-05
[this]("http://brainstorm.ubuntu.com/idea/5878/") suggests that yes the support is there but I have not been able to successfully impart such skills to my own ubuntu system.

---

### Post by bumanie on 2010-07-05
There is a command line tool in ubuntu hfsutils. Also, I traced this through the puppy linux forum, a beta driver to allow read/write to hfs+ from linux - beware, it says to use at own risk as it is (or was) still in beta). Here's the [link]("http://www.ardistech.com/hfsplus/") if anyone wants to try it, I can't as I don't own an Apple. Would be prudent to backup important stuff first.

---

### Post by russo.mic on 2010-07-05
I've read / written to HFS+ before by mounting with the force option invoked on the command line.

mount -t hfsplus /dev/xxx /xxx/xxx -o force

The superuser will have privileges to write.

---

### Post by taunnt on 2010-07-05
In the original post the question asked was for hfs+ journaled. Keyword is journaled, I can write to hfs+, but not hfs+ journaled.

---

