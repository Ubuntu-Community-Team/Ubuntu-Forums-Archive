---
title: "Dependency after dependency after dependency..."
date: 2010-10-21
forum: General Help
---

### Post by rick astley on 2010-10-21
I've been trying to compile the linux kernel for hours now. I download the kernel source from kernel.org and I follow this guide:

[https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")

Im running a freshly installed and fully updated ubuntu 10.04. This is for hobby reasons so i'm following the guide from the section called "The Old Fashioned Debian Way." When I get to the 'make xconfig' part it doesn't finish. It tells me I have unmet dependencies.

Can anyone help me, or am I looking at the wrong type of guide?

rick.

---

### Post by nerdopolis on 2010-10-21
Hi.

I just tried this yesterday myself, and I installed libqt3-mt-dev, and make xconfig worked

You can install it by running
sudo apt-get install libqt3-mt-dev

hope this helps

---

