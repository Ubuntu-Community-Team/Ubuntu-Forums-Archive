---
title: "Unable to locate package update"
date: 2012-02-08
forum: General Help
---

### Post by rahelinux on 2012-02-08
after typing this command "apt-get install update" , I got this message :
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package update
, plz I need your help, why I cannot update?

---

### Post by rahelinux on 2012-02-08
> **rahelinux said:**
> after typing this command "apt-get install update" , I got this message :
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package update:p
, plz I need your help, why I cannot update?
df

---

### Post by polki@mac.com on 2012-02-08
Try:

sudo apt-get update

instead.

---

### Post by muggle_born_prince on 2012-02-09
You cannot do sudo apt-get install update. It should be <b>sudo apt-get update</b>.

No package means, there is no package called update in the list of archives.

---

### Post by rahelinux on 2012-02-13
Thanks a lot for your replies.

---

