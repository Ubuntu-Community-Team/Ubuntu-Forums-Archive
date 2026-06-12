---
title: "Compiling troubles..."
date: 2006-03-29
forum: General Help
---

### Post by Piggah on 2006-03-29
Hi,

I'm having a bit of trouble compiling gaim2.0beta3. I've never had this issue before, but I am now for some reason. The problem is that it's unable to find a makefile. I think that has something to do with an error I get while running ./configure, which stops the ./configure too btw.

```
checking for XML::Parser... configure: error: XML::Parser perl module is require d for intltool

```

I assume I need to install some package for that, but I have no idea what. 

Here also is what I get when I attempt to run 'make'.
```
make: *** No targets specified and no makefile found.  Stop.
```

I'm lost with this, so any help is really appreciated. :) 

Thanks in advance :)

---

### Post by hw-tph on 2006-03-29
```
hakan@devon:~$ apt-cache search xml-parser | grep -i perl
libdbix-xml-rdb-perl - perl module for creating XML from a DBI datasource
libxml-parser-perl - Perl module for parsing XML files
hakan@devon:~$ sudo apt-get install libxml-parser-perl
```

That should take care of that. You can use apt-cache (or aptitude) to quickly search the available packages - these tools are very useful. Read apt-cache(8) for more information, or **man -k apt** to look for man pages that relate to apt.


Håkan

---

