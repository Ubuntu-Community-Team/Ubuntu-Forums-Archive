---
title: "Problems with java"
date: 2010-03-28
forum: General Help
---

### Post by rahulponna on 2010-03-28
Hi,

 I am running a mentor graphics tool which used java-jre. Every time I try to invoke the tool I get the following error message
Exception in thread "main" java.lang.UnsatisfiedLinkError: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so: /home/rahulp/mentor/eldo/devenv_tools/i686/2.4.9-e.12/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/jvm/java-6-openjdk/jre/lib/i386/libfontmanager.so)

From the error message I thought gcc_4.2.0 is not installed in my system. I went to synaptic package manager and installed gcc_4.2, but I still get this error.

I really frustrated with the above error. Any kind of help will be appreciated.



Thanks
Rahul

---

### Post by darolu on 2010-03-28
> **rahulponna said:**
> /usr/lib/jvm/java-6-openjdk/jre/lib/i386/**libfontmanager.so**: 

/home/rahulp/mentor/eldo/devenv_tools/i686/2.4.9-e.12/lib/**libgcc_s.so**.1

If GCC is installed, you probably have the .so files it's requesting but are installed somewhere else.

Run a 'find' search to see if you have this files and then symlink to them in these directories, so your tool can run.
```
sudo find / -name libfontmanager.so

sudo find / -name libgcc_s.so
```

---

### Post by rahulponna on 2010-03-28
Thanks darolu, You were right, I had to pick up the right files from the right directories.
The tool I was running had it's own "lib" directory and it was using **libgcc_s.so**.1 file from that directory which was a older version. I removed that file and placed libgcc_s.so.1 from gcc 4.2.0 directory.

---

