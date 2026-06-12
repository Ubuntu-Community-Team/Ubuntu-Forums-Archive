---
title: "HELP&gt;&gt;&gt;&gt;&gt; error: c compiler cannot create executables"
date: 2009-09-11
forum: General Help
---

### Post by Tclarkie on 2009-09-11
So im making a lfs OS right..
go througha all the config' stuff
try to compile the first package
it comes out with
"error: c compiler cannot create executables"
i try again
and on other packages

nothing


Can anyone help PLEASE



THANKS IN ADVANCE

(ps. they brought back the "SOLVED" prefix)

---

### Post by StuartN on 2009-09-11
> **Tclarkie said:**
> "error: c compiler cannot create executables"

Install the build-essentials package.

---

### Post by aesis05401 on 2009-09-11
What LFS book are you using?  I found that downloading the 6.3 stable livecd for my host environment, then using 6.4 instructions and packages was the best way to do this.  6.3 instructions left some things out and 6.4 corrects most of those points.  If your question is not answered in the docs please consider posting at an LFS mailing list or forum so the maintainers can take a look at whether they want to modify the instructions.  

Best of luck.

---

### Post by Tclarkie on 2009-09-11
6.5

---

### Post by Tclarkie on 2009-09-11
it didn't work

---

### Post by aesis05401 on 2009-09-11
Can you describe your host environment?  LFS in regular Ubuntu host environment runs into lots of issues and LFS maintainers recommended against building LFS in the regular Ubuntu environment as of LFS6.4 (I don't know about the latest version).  Have you tried a LFS-livecd environment inside VBox for your build?  

If you are not inside a sterile build environment you can run into all sorts of issues including accidentally linking to your host environment due to existing environment variables, not locating the correct packages due to scope/path issues, and all sorts of nasty stuff like that.

---

### Post by Tclarkie on 2009-09-12
thanks heaps, yeah ive stuffed up my system, will upgrading to 9.10 help

---

### Post by aesis05401 on 2009-09-13
Upgrading your Ubuntu box should not be the priority... You can set up a proper build environment for your LFS experiments by downloading VirtualBox from the repositories, downloading an LFS livecd, and then booting a VirtualBox virtual machine with the LFS livecd.  

Building your LFS system in this way will guarantee that you don't stuff up your LFS or host system.  Does this make sense?  Running your LFS build inside the VirtualBox VM will also allow you to take snapshots and save your 'Machine State' instead of shutting down the VM.  This is extremely helpful when building your first Linux system from scratch because you can close the VM whenever you want without losing all your environment variables/shell history etc.., and the snapshots let you roll back if you end up with a borked roll but don't want to start over.

Does this help?

---

### Post by Bachstelze on 2009-09-13
Not Ubuntu-related. Closed.

---

