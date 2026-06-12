---
title: "PHP doesn't support MySQL?"
date: 2004-10-20
forum: General Help
---

### Post by kuam on 2004-10-20
I'm trying to install phpBB2 v2.0.10 and this is what I get:

"The PHP configuration on your server doesn't support the database type that you chose"

Did I miss a package somewhere?  :(

---

### Post by natefish on 2004-10-20
I had the same problem, you need to download the package

"PHP4-MYSQL" from the "universe" it will run after that.

---

### Post by kuam on 2004-10-20
Thank you so much...  :D

---

### Post by tedbundyjr on 2004-10-22
what do you means by > "PHP4-MYSQL" from the "universe"

---

### Post by tedbundyjr on 2004-10-22
ok got it

from /etc/apt/sources.list
> 
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe


---

