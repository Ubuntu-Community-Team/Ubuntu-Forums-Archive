---
title: "stddef.h"
date: 2010-10-13
forum: General Help
---

### Post by Spyros_Gre on 2010-10-13
Hello! I am building a program in C and I must include stddef.h.
Netbeans (with c/c++ support) says that the particular header is missing.
I have installed and reinstalled several times gcc 4.4, build-essentials etc to no avail.. 
Searching through forums and articles, I stumbled upon some of them stating that stddef.h is not included in ubuntu 10.10. Is that true? Are there any workarounds for this? Is this a bug? Thank you!:)

---

### Post by luigi_mb on 2010-10-13
```

locate stddef.h

```

The file should be in /usr/include/linux and elsewhere. You may have to edit your makefile. 

/luigi

---

### Post by gmargo on 2010-10-13
Install the **linux-libc-dev** package to get stddef.h.

[http://packages.ubuntu.com/lucid/linux-libc-dev](http://packages.ubuntu.com/lucid/linux-libc-dev)

For future reference, on the package page at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) in the "search the contents of packages" section, you can search for specific files.

---

### Post by Spyros_Gre on 2010-10-14
> **luigi_mb said:**
> ```

locate stddef.h

```

The file should be in /usr/include/linux and elsewhere. You may have to edit your makefile. 

/luigi

Hello! Thank you. I had actually tried that and it did work. My main concern is about portability and the fact that something has changed in ubuntu 10.10. Maybe a different path or failure to include it. I don't know.

> **gmargo said:**
> Install the **linux-libc-dev** package to get stddef.h.

[http://packages.ubuntu.com/lucid/linux-libc-dev](http://packages.ubuntu.com/lucid/linux-libc-dev)

For future reference, on the package page at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) in the "search the contents of packages" section, you can search for specific files.

Thank you I've done that and nothing changed. If I just copy the stddef.h file in my include dir, won't that be ok?

---

### Post by jespdj on 2010-10-14
> **Spyros_Gre said:**
> If I just copy the stddef.h file in my include dir, won't that be ok?
That's not a good idea. It probably refers to other system header files and if you just copy stddef.h and not those other files it won't work. But besides that, you don't want to include such a system header files with your own sources. People who compile your source code for their system should use the stddef.h that's specific for their system, and not the one that you provided.

After installing linux-libc-dev, you should make your project reference the file that's in the system include directory. Probably somewhere in your project settings (or your makefile) you should make sure that the compiler looks at the system include directory.

---

### Post by gmargo on 2010-10-14
Maybe you're actually looking for the stddef.h provided by the compiler itself:
```

$ dpkg -L gcc-4.4 | grep stddef
/usr/lib/gcc/x86_64-linux-gnu/4.4/include/stddef.h

```What other options are you giving the compiler?  Are you telling it to ignore it's own standard directories?

---

### Post by Spyros_Gre on 2010-10-14
My Include directories were:
/usr/local/include
/usr/lib/gcc/i686-linux-gnu/4.4.5/include
/usr/lib/gcc/i686-linux-gnu/4.4.5/include-fixed
/usr/include

I tried pretty much reinstalling everything relative to gcc. Nothing happened.
I then did a dpkg -L gcc as suggested and I realized that I could choose 4.4.4 instead of 4.4.5. I gave it a try changing the include directories of netbeans and voila! SUCCESS! 
Thank you all!

---

### Post by ryanfx on 2010-11-08
> **Spyros_Gre said:**
> My Include directories were:
/usr/local/include
/usr/lib/gcc/i686-linux-gnu/4.4.5/include
/usr/lib/gcc/i686-linux-gnu/4.4.5/include-fixed
/usr/include

I tried pretty much reinstalling everything relative to gcc. Nothing happened.
I then did a dpkg -L gcc as suggested and I realized that I could choose 4.4.4 instead of 4.4.5. I gave it a try changing the include directories of netbeans and voila! SUCCESS! 
Thank you all!

If you go to tools -> options -> C/c++ Compiler -> code assistance and then hit "Reset Settings" at the bottom of the page, it resolves the broken paths (and you won't have to continually include the correct directories for every project).   This broke on my upgrade as well.  Hope this helps.

---

