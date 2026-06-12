---
title: "Share altered packages from Canon back to the community?"
date: 2010-11-09
forum: General Help
---

### Post by JorisSpekreijse on 2010-11-09
Hello,

After some struggling with installing a printer (Canon Pixma 620) I have some knowledge and two packages "left". The feedback is send to the author of mp610's blog at blogspot. But I had to alter two packages in order to install the drivers for the printer correctly.

It is a small trick. I had to alter the dependency for libcupsys2 to libcups2. But looking on the internet, I see that a lot of people have this problem installing these drivers. So I think these packages must be shared. Letting people work with dpkg-deb is for advanced users, not for the normal endusers Ubuntu want to reach.

There are two options.

I could send it to the maintainer in Japan. But then they have to alter a lot of packages, and I doubt if they will do that. After all they used this very obselete libcupsys2.

Second option is to host these packages somewhere. Problem is that I am not the maintainer of these packages nor the owner of intellectual property. And when I will do that, what must I do to the construct file in the package? I already altered description and gave it a new version number xxx-2.i386 i.o. xxx-1.i386.deb Or should I gave them a new name like xxx-1_<name>.i386.deb?

Anyhow, I want to share but I am very insecure how to do it properly.

---

