---
title: "Concerning the manual installation of Firefox plugins."
date: 2006-02-22
forum: General Help
---

### Post by DonQuixote on 2006-02-22
Alright, please don't say "Automatix". :-D

There are times when Firefox can not install a plugin automatically, and give you the option of "Manual Installation".

So, with that in mind, I am interested in knowing how to manually install plugins, without the use of Automatix, primarily because I have an innate curiosity of how things work under the hood.

If I download Firefox, and unzip it to /opt/firefox, how would I go about installing the plugins, and pointing Firefox to them?

Can anyone point me in the right direction? (I have searched for threads about this, but my search has, by and large, been a lot of reading, "Use Automatix").

Thanks!

---

### Post by dcstar on 2006-02-23
[QUOTE=DonQuixote]Alright, please don't say "Automatix". :-D

There are times when Firefox can not install a plugin automatically, and give you the option of "Manual Installation".

So, with that in mind, I am interested in knowing how to manually install plugins, without the use of Automatix, primarily because I have an innate curiosity of how things work under the hood.

If I download Firefox, and unzip it to /opt/firefox, how would I go about installing the plugins, and pointing Firefox to them?

Can anyone point me in the right direction? (I have searched for threads about this, but my search has, by and large, been a lot of reading, "Use Automatix").

Thanks![/QUOTE]
Your Firefox directory will have a "plugins" directory, the .so and .xpt files (or links) go in there (or just a link for the Java plugin).

Firefox will see them on next start-up, do "about: plugins" (remove the space) to look at them.

---

