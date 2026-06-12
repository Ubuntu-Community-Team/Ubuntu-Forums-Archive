---
title: "wary"
date: 2009-07-24
forum: General Help
---

### Post by david3743 on 2009-07-24
having spent the last 10 years making Microsoft a fortune, yesterday I loaded Ubuntu on an old Asus machine. It's really blown me away how easily the PC took to it (I've always had hassle with XP on it)
However as I have always used Microsoft before when surfing the net or doing research I have never gone to the internet without anti-viral software. I have installed Firestarter  which came with the ISO disc. So I then visited the Avast site to see about my hassle.
No problem they will download a free version for linux. But they offer 3 versions:-
Avast linux home edition (RPM package),  ditto (DEB package) and ditto (TAR GZX package). To you intelligent people this is probably simple, but I am known as techno turtle in the family!! So please tell me which one to use.
Cheers- and be kind I am frail!!!:confused:

---

### Post by wojox on 2009-07-24
.deb short for debian.

---

### Post by david3743 on 2009-07-24
Thanks Mate
 so by that I assume the others are short for something else, I will google them???:)

---

### Post by muteXe on 2009-07-24
I'm at work so i dont have my linux machine in front of me, but you could try looking in the synaptic package manager for avast.  I think AVG is there, as is clamAV.

It's fairly rare that you'd need to get a deb or tar from a website.

mute

---

### Post by wojox on 2009-07-24
Firestarter is no good. UFW is the default firewall and it's command line but you can download a gui gUFW.

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

RPM is Redhat and the other is Slackware I think.

---

### Post by muteXe on 2009-07-24
Yup slackware's package management uses tarballs.

---

### Post by fballem on 2009-07-24
> **david3743 said:**
> Thanks Mate
 so by that I assume the others are short for something else, I will google them???:)

There are two major packaging formats used in Linux - rpm and deb.

RPM packages are used in Red Hat-based systems, such as Fedora and OpenSUSE.

DEB packages are used in Debian-based systems, such as Debian and Ubuntu.

Since you're using ubuntu, you should almost always select the deb packages if available. As another poster suggested, however, you should always start with the Synaptic package manager (System > Administration > Synaptic Package Manager). You will rarely have to install a deb, since the repositories are pretty complete for most users.

The .tar.gz is a compressed archive (conceptually similar to a .zip file in Windows). This should be viewed as a last resort, and only when you get more comfortable with Linux. In some cases, the archive contains source files that need to be compiled. In other cases, the archive contains files that need to be placed in specific locations. Until you are really comfortable with Linux, I would suggest you avoid these.

By the way, it is up to you, but most Linux users do not use an Anti-Virus software. Many will use a Firewall. There are many posts in this forum that discuss this topic, but the very short answer is that Linux was designed from the ground up to be a secure, multi-user system with strict enforcement of privileges.

Unless you are running as the root user, the permissions necessary for a virus to work simply aren't there for a virus. In most other distributions, you are running as a 'normal' user, and you must take specific actions to run as root, such as typing 'sudo' before a command.

The only reason that people will run anti-virus software in Linux is to avoid passing an infected file to a Windows-based user.

Hope this helps,

---

### Post by 3rdalbum on 2009-07-24
Don't bother with the anti-virus software unless you want to check the disks of Windows users.

Note that you don't need to enable your firewall unless you have actually installed some software that is listening for incoming connections, and if you already have a firewall in your ADSL/cable router there's no need to enable a personal firewall. If you must use a firewall configuration program, use Gufw, not Firestarter.

---

### Post by david3743 on 2009-07-24
Thanks Guys I knew you would be clever!!

Now where's my bleeding coffee!!!:D

---

### Post by fballem on 2009-07-24
> **david3743 said:**
> Thanks Guys I knew you would be clever!!

Now where's my bleeding coffee!!!:D

Sounds like you might need something stronger than coffee!

---

