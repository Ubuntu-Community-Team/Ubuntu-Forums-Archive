---
title: "32 bit binaries on a 64 bit computer"
date: 2010-05-15
forum: General Help
---

### Post by Spreadsheet on 2010-05-15
Hello, I am running Ubuntu 64-bit and I downloaded a 32-bit binary. I tried to run it in the shell using ./file but zsh said that it did not exist. However it shows up in nautilus and ls. Is this supposed to happen?

---

### Post by gmargo on 2010-05-15
You will have to install one or more 32-bit compatibility libraries.  They are named 'lib32....", [http://packages.ubuntu.com/search?keywords=lib32&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=lib32&searchon=names&suite=lucid&section=all)

Try running "ldd" on the binary to find out what libraries it requires.

---

### Post by 3rdalbum on 2010-05-15
What happens if you drag it onto the terminal and then run the result?

And in order to run 32-bit programs you need the 'ia32libs' package. You might also need to use [Getlibs]("http://ubuntuforums.org/showthread.php?t=474790") to retrieve some more 32-bit libraries for your program.

---

