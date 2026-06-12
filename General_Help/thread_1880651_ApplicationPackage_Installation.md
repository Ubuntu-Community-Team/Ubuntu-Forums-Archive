---
title: "Application/Package Installation?"
date: 2011-11-14
forum: General Help
---

### Post by histamineblkr on 2011-11-14
My question is:

What is the correct path to install applications and programs in ubuntu 10.04?

Say I download Netbeans from Netbeans.org and then I go to install it using there install.sh script. It just decides where to install itself on my machine. The same with VirtualBox or with Thunderbird, etc. However can I and should I be specifying where it installs itself? I don't care to always use the USC since it doesn't have the latest nor does it necessarily have even the application I want.

If there is a post/thread that already covers this or some ubuntu documentation that I can read just link me to it or if it's an easy answer just reply.

Thank you.

---

### Post by mlentink on 2011-11-14
Applications usually go to /usr/bin, but you can check where they have been installed by 
```
which applicationname
```
You don't ordinarily worry about where apps go.

---

### Post by oldos2er on 2011-11-14
Installing programs manually (i.e. not using APT), you have a few choices. If you're install compiled source code with **sudo make install**, it usually goes to /usr/local/*

From the Linux File System Hierarchy Standard: "The /usr/local hierarchy is for use by the system administrator when installing software locally. It needs to be safe from being overwritten when the system software is updated. It may be used for programs and data that are shareable amongst a group of hosts, but not found in /usr."

There's also /opt. 

Some apps like Thunderbird and Firefox will run quite happily from within your home folder.

If you have a specific question about Netbeans, I'd use their forums/mailing lists.

---

### Post by histamineblkr on 2011-11-16
> **oldos2er said:**
> Installing programs manually (i.e. not using APT), you have a few choices. If you're install compiled source code with **sudo make install**, it usually goes to /usr/local/*

From the Linux File System Hierarchy Standard: "The /usr/local hierarchy is for use by the system administrator when installing software locally. It needs to be safe from being overwritten when the system software is updated. It may be used for programs and data that are shareable amongst a group of hosts, but not found in /usr."

There's also /opt. 

Some apps like Thunderbird and Firefox will run quite happily from within your home folder.

If you have a specific question about Netbeans, I'd use their forums/mailing lists.

Thank you. It's more of an overall question of how to manage packages myself if I chose to download newer versions and install them myself, not specifically Netbeans.

---

