---
title: "Packaging for Hardy"
date: 2011-04-17
forum: General Help
---

### Post by Sam1994 on 2011-04-17
Hello,

Having to build a package myself because it is deprecated on Hardy. I tried checkinstall but obviously its not the way to go about it due to dependencies. Unfortunately, I have unresolvable dependencies that must be built from source as 8.0.4 is such a deprecated platform. So what is the best method of packaging everything? dpkg -b? The dependencies give me errors when I try checkinstall as a packaging method.

So if I host my own apt-repo, I upload the dependency packages, as well as the actual software package and then if I list them as dependencies apt will pull them down right. Now here's the bit I'm a little confused on. When listing the dependencies, should I give them the same name as the current dependency name (e.g. curl), or should I remove the dependency curl from the current list I have in a text file of dependencies and call it curl-fixed etc. If I still call it curl, apt will fetch the wrong package perhaps, unless I list my repo above official Ubuntu ones??

Thanks, apt packaging is in no way my forte.

---

