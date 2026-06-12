---
title: "Understanding what compiling is."
date: 2009-12-07
forum: General Help
---

### Post by mahela007 on 2009-12-07
What does compiling mean with respect to installing from a tar ball?

---

### Post by aviedw on 2009-12-07
No disrespect but this really seemed like a questions that could have been googled.

[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

[http://www.cyberciti.biz/faq/install-tarballs/](http://www.cyberciti.biz/faq/install-tarballs/)

---

### Post by lisati on 2009-12-07
A "tar ball" is similar in concept to a ZIP file in Windows, and commonly has an extension like ".tar" or ".tar.gz"

As with a ZIP file, you'll likely have to extract the files to a folder somewhere. If you're in luck, there'll be script files in the extracted folder to help with the compilation, e.g. configure, make, make install etc.

---

### Post by lloyd_b on 2009-12-08
> **mahela007 said:**
> What does compiling mean with respect to installing from a tar ball?

"Compiling" is a process that converts human-readable (well, *programmer-readable*) instructions to actual machine code.

When you download a tarball, you're downloading the "source" files of the project - these have to be converted into the binary executable(s) in order for it to run on your machine.

Lloyd B.

---

### Post by kjohri on 2009-12-08
A tar file is an archive of a software package. One has to install the tar archive into a directory for building the executable version of the software package. So the steps are,

un-tar the tar archive,
configure as per local environment,
compile the software package (make),
install the compiled software

[http://www.softprayog.in/tutorials/understanding-gnu-build-system.shtml]("http://www.softprayog.in/tutorials/understanding-gnu-build-system.shtml")

---

### Post by C-- on 2009-12-08
Different machines have different hardware instruction sets, architectures, and software environments, so you need to compile on a given machine before you can install it. Consider this analogy: computer A speaks Spanish, and computer B speaks French, while the programmer speaks English. The compiler translates the programmer's English into Spanish for computer A and French for computer B, otherwise nothing would make sense.

---

### Post by mahela007 on 2009-12-09
Thanks a lot!

---

