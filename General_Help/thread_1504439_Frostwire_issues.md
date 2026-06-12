---
title: "Frostwire issues"
date: 2010-06-08
forum: General Help
---

### Post by KiraKarns on 2010-06-08
I'm trying to download frostwire and it always says Error: Dependency is not satisfiable: Sun-Java6-jre. I have no idea what this mean....

---

### Post by JoelOl75 on 2010-06-08
Open synaptic and make sure the universe is enabled.  Do a search for sun java and install the jre (runtime environment).  This will pull down some other files as well.  I believe it's version 1.6 in the repos and works fine with frostwire.

---

### Post by KiraKarns on 2010-06-08
I am so sorry but I don't know how to do any of the stuff you just told me would help. I'm completely retarded when it comes to computers

---

### Post by xjesse on 2010-06-08
You need java, sir.


sudo apt-get update

sudo apt-get install sun-java6-jdk

---

### Post by Soul-Sing on 2010-06-08
Download frostwire noarch, unpack it.run frostwire.sh from the folder. it runs fine with openjdk, no [COLOR="Red"]sun[/COLOR] java needed.
By default Ubuntu comes with openjdk.

---

### Post by KiraKarns on 2010-06-08
What's frostwire noarch? (Thanks, everyone, btw)

---

### Post by Soul-Sing on 2010-06-08
> **KiraKarns said:**
> What's frostwire noarch? (Thanks, everyone, btw)

thats a tar gz [COLOR="Red"]no[/COLOR]n [COLOR="Red"]arch[/COLOR]itecture
download from the frostwire site.
So not distro specific.

---

### Post by KiraKarns on 2010-06-08
Thank you so much!

---

