---
title: "Compiling for another OS"
date: 2009-10-17
forum: General Help
---

### Post by jfreak53 on 2009-10-17
Ok here's the biff.  I have ubuntu Jaunty.  Latest releases.

What I want to do is compile pdf2swf in my ubunutu for another linux Dis.  My web hosting server will not let me compile on my shared account.  So I have to upload the binary file ready compiled to be able to use it.  How do I do this short of installing the OS on my pc just to compile with?

They use CentOS release 4.8 (Final) i686 and the kernel version is 2.6.9-89.0.11.ELsmp.

Any ideas?

Thanks in advance.

---

### Post by beastrace91 on 2009-10-18
So long as your system is the same architecture (32bit) as the server you should be able to compile on it just fine and then shoot the compiled source over to your server (for example, run 'make' on your own system, then copy the folder contents to the server and run 'make install' there)

Worst case you could also always install CentOS via Virtual Box if this doesn't work :)

~Jeff

---

