---
title: "trying to install from a tarball, and ./configure doesn't work"
date: 2010-11-27
forum: General Help
---

### Post by ninjaaron on 2010-11-27
The thread title says it all. I've extracted the tar.gz, gone into the folder in a terminal, typed "./configure", and it just says "bash: ./configure: No such file or directory"

So that sucks.

I really wanted to try the LibreOffice beta.

---

### Post by nothingspecial on 2010-11-27
Is there a configure script?

Is there a README file?

---

### Post by ninjaaron on 2010-11-27
uh... i don't see a configure script (which, I guess makes sense). There is a readme, which I have read. It doesn't have any details about how to install.

[edit] dammit. ok, I just found the tarball with the debian package. I'll give that a try instead.

---

### Post by ninjaaron on 2010-11-27
well, that went swimmingly.

---

### Post by mikewhatever on 2010-11-27
Try unpacking the tarball instead of installing it. Depending on what's inside you may be able to use it for installation. If that is source code, ./configure is usually the way to start.

---

### Post by oldos2er on 2010-11-27
They have *deb files available. 32-bit: [http://download.documentfoundation.org/libreoffice/testing/3.3.0-beta3/deb/x86/LibO_3.3.0_Linux_x86_install-deb_en-US.tar.gz](http://download.documentfoundation.org/libreoffice/testing/3.3.0-beta3/deb/x86/LibO_3.3.0_Linux_x86_install-deb_en-US.tar.gz)

or 64-bit: [http://download.documentfoundation.org/libreoffice/testing/3.3.0-beta3/deb/x86_64/LibO_3.3.0_Linux_x86-64_install-deb_en-US.tar.gz](http://download.documentfoundation.org/libreoffice/testing/3.3.0-beta3/deb/x86_64/LibO_3.3.0_Linux_x86-64_install-deb_en-US.tar.gz)

---

### Post by SeijiSensei on 2010-11-27
Quick checklist for building from source:

1)  sudo apt-get install build-essential
    Run this to get compilers and other needed software installed first.

2)  Unpack the tarball into your home directory

Usually the tarball will contain a directory of its own which will be created as $HOME/source-code-directory, but it's always good to check first like this:

```
tar tzvf /path/to/tarball.tgz
```

Use "z" if it's a tgz (uses gzip compression).  Replace "z" with "j" if it's compressed with bzip2 (tarball usually ends in .bz2).

If you see a directory then you're set.  Otherwise create a directory under your home and move the tarball there.  Then, in either case, rerun the command above replacing "t" in the options with "x" to extract.

3)  Go into the directory where the source files are installed; type "./configure; make".  If everything goes okay, type "sudo make install" to install the program.  Programs compiled from source will usually be installed under /usr/local.  

4)  If you see a statement at the end about needing to run "ldconfig" type "sudo ldconfig" after installation.

---

