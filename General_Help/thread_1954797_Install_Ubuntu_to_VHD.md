---
title: "Install Ubuntu to VHD"
date: 2012-04-08
forum: General Help
---

### Post by ChaosChris2009 on 2012-04-08
Is it possible to install Ubuntu to a VHD?

I'm currently on Windows 7

---

### Post by Cheesemill on 2012-04-08
For what purpose?

You could use either Hyper-V or Virtualbox to install a Ubuntu VM into a VHD file, but this would only make any sense if you want to run it as a virtual machine.

---

### Post by ChaosChris2009 on 2012-04-08
> **Cheesemill said:**
> For what purpose?

You could use either Hyper-V or Virtualbox to install a Ubuntu VM into a VHD file, but this would only make any sense if you want to run it as a virtual machine.

I want to dual boot it without having to partition.

---

### Post by Cheesemill on 2012-04-08
In that case you are probably better of using Wubi:
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

---

