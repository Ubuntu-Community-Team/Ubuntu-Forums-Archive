---
title: "If the security-testing packages are in Ubuntu repositiories, why install BackTrack?"
date: 2012-06-24
forum: General Help
---

### Post by bananaboatcoat on 2012-06-24
Hello,
Assume that a person has installed and uses Ubuntu Linux. Ubuntu is his main distro for personal and work use. 
On very rare occasions, the user wants to use security-testing packages, the sort of packages that Backtrack Linux would have in their own repository.

If the security-testing/pen-testing packages are found in Ubuntu repositories, is there still any good reason to install BackTrack Linux?



[http://www.backtrack-linux.org/wiki/index.php/FAQ#Why_cant_I_just_add_the_Backtrack_repositories_to_my_Ubuntu_install_or_the_Ubuntu_repositories_to_my_Backtrack_install_.3F](http://www.backtrack-linux.org/wiki/index.php/FAQ#Why_cant_I_just_add_the_Backtrack_repositories_to_my_Ubuntu_install_or_the_Ubuntu_repositories_to_my_Backtrack_install_.3F) gives a FAQ that, though related to my question, does not answer it:
> 
Why cant I just add the Backtrack repositories to my Ubuntu install or the Ubuntu repositories to my Backtrack install ?

We highly recommend against this action because Backtrack tools are built with many custom features, libraries and kernel. We have no way of knowing how they will perform on a non Backtrack distribution, plus you will very quickly break your install.
Also if you chose to add the ubuntu repositories to your Backtrack install, you will most certainly break your entire Backtrack install very quickly.
We do a lot of testing to ensure that all packages in our repo will work together without causing problems.
If you decide on this course of action you do so entirely at your own risk and the backtrack team will not offer any support in any way.

---

### Post by zombifier25 on 2012-06-24
Same reason why there are Kubuntu, Xubuntu, Lubuntu, etc. If you're looking for a security-testing distro from the very start, then installing BackTrack is more convenient than installing Ubuntu, and then manually add the packages.

---

### Post by bananaboatcoat on 2012-06-24
> **zombifier25 said:**
> Same reason why there are Kubuntu, Xubuntu, Lubuntu, etc. If you're looking for a security-testing distro from the very start, then installing BackTrack is more convenient than installing Ubuntu, and then manually add the packages.

But:
-- if one is not looking for a security-testing distro from the start, and
-- if one is interested in installing only a few security-testing packages, and 
-- if one finds setting up a new distro (BackTrack) on their hard drive much more inconvenient than installing the few security-testing packages on Ubuntu

why install Backtrack?

---

### Post by zombifier25 on 2012-06-24
> **bananaboatcoat said:**
> But:
-- if one is not looking for a security-testing distro from the start, and
-- if one is interested in installing only a few security-testing packages, and 
-- if one finds setting up a new distro (BackTrack) on their hard drive much more inconvenient than installing the few security-testing packages on Ubuntu

why install Backtrack?

Then they wouldn't be installing BackTrack. Like what I said, only sysadmins, penetrating testers, security experts, etc. who would like to test the security of their servers would use BackTrack.

---

