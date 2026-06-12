---
title: "Home folder isn't under my new installation"
date: 2009-11-15
forum: General Help
---

### Post by lu6cifer on 2009-11-15
So I installed Kubuntu, but then I got bored of it, and switched to Ubuntu 9.10.

I had created separate partitions for / and /home, and when it came to install Ubuntu, I did a manual installation and only installed /. 

But now, when I boot into Ubuntu, my home folder doesn't really exist..that is, the home folder for Ubuntu is located in the root partition space, and my home folder for Kubuntu is still intact, but is shown as a separate partition on the sidebar.

How do I fix this? How do I 'sync' the home and root partitions?

---

### Post by dcstar on 2009-11-15
> **lu6cifer said:**
> So I installed Kubuntu, but then I got bored of it, and switched to Ubuntu 9.10.

I had created separate partitions for / and /home, and when it came to install Ubuntu, I did a manual installation and only installed /. 

But now, when I boot into Ubuntu, my home folder doesn't really exist..that is, the home folder for Ubuntu is located in the root partition space, and my home folder for Kubuntu is still intact, but is shown as a separate partition on the sidebar.

How do I fix this? How do I 'sync' the home and root partitions?

You mount the /home partition. Either edit your /etc/fstab manually or use the **pysdm** package.

---

