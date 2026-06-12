---
title: "Debian Ubuntu package handling"
date: 2010-11-23
forum: General Help
---

### Post by yc2 on 2010-11-23
Hello,

I am writing an introduction to Ubuntu in the Swedish language.
[http://e-dog.info/t/63/doc/Ubuntu_installation.php](http://e-dog.info/t/63/doc/Ubuntu_installation.php)

I try to write a little about the background and _I am unclear about how Debian is transformed into Ubuntu_. I know that a snapshot of Debian unstable (sid) is made evey six months and that this is the basis for making Ubuntu.

However, I do not understand the following:

1. What are the main steps in making Ubuntu out of Debian. I do not think packages are changed, so I assume new packages are introduced? (As I understand there is no other software in Ubuntu apart form the packages.)

2. How does package maintenance work. I know some packages are tested in the Ubuntu test-version. (We are now running Natty test parallel to Maverick) Bugs are found and reported in launchpad. How do the corrected packages port back to Debian? 

I think a certain package is exactly the same thing in Debian and Ubuntu. There is no special Debian or Ubuntu version. but in this case it also seems strange to have two package maintenance systems, one for Debian and one for Ubuntu. If a bug in a package was corrected in Ubuntu/LP, this correction would be "overwritten" when the snapshot of Debian was made for the next version of Ubuntu?

Sorry for not quite clear question. Can anyone please describe the relation between Debian and Ubuntu when it comes to creating new versions of Ubuntu and how package upgrades are related in thet two distros?

Thanks.

---

### Post by dcstar on 2010-11-23
> **yc2 said:**
> 
.........
**I think a certain package is exactly the same thing in Debian and Ubuntu. **There is no special Debian or Ubuntu version. but in this case it also seems strange to have two package maintenance systems, one for Debian and one for Ubuntu. If a bug in a package was corrected in Ubuntu/LP, this correction would be "overwritten" when the snapshot of Debian was made for the next version of Ubuntu?

Sorry for not quite clear question. Can anyone please describe the relation between Debian and Ubuntu when it comes to creating new versions of Ubuntu and how package upgrades are related in thet two distros?

Thanks.

[LIST=1]
[*]**No**. Ubuntu is Debian based but is different from Debian - you should not mix packages.
[*]Do a web search for detailed explanations of the difference, I believe many already exist.
[/LIST]

---

