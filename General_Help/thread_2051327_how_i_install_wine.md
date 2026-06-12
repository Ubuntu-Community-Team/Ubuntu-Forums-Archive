---
title: "how i install wine?"
date: 2012-09-01
forum: General Help
---

### Post by Raihan004 on 2012-09-01
how i setup wine from wine-1.4.tar.bz2 format archive ?;) can you any one help me .
step by step process need coz am noob at linux .:guitar:
i wana learn and get enjoy .
 so ans me quick if know process :popcorn:

---

### Post by Lars Noodén on 2012-09-01
Wine 1.4 is in the software repository.  It would be best if you remove the files from the wine-1.4.tar.bz2 file and use the package manager instead.  You can get to [wine](apt://wine) via the Software Center or, if you have it, Synaptic.  From there it is one or two clicks and it is installed.  It will be updated that way too.

---

### Post by Raihan004 on 2012-09-01
> **Lars Noodén said:**
> Wine 1.4 is in the software repository.  It would be best if you remove the files from the wine-1.4.tar.bz2 file and use the package manager instead.  You can get to [wine]("apt://wine") via the Software Center or, if you have it, Synaptic.  From there it is one or two clicks and it is installed.  It will be updated that way too.

dude i wana to learn how i install wine from source code .
i can easily install it from soft manager or terminal :lolflag:
but i dont know how i install it form source code?:mad:

so if you know process instaing from source code,tell me:D

---

### Post by Tobeus on 2012-09-01
I would go to winehq to find out how to install their software from source.

[http://www.winehq.org/docs/wineusr-guide/installing-wine-source](http://www.winehq.org/docs/wineusr-guide/installing-wine-source)

This is where I found the instructions.

Hope that helps!

-Tobeus

---

### Post by Tobeus on 2012-09-01
Also, if you need to extract files from a tarball, you can use the tar command:

[http://infohost.nmt.edu/tcc/help/unix/tar_extract.html](http://infohost.nmt.edu/tcc/help/unix/tar_extract.html)

You can use the instructions from this site to help you learn how to extract a tarball.

This guy actually goes really well into the specifics with references on how to install wine from source.  I think it covers the details way better than the winehq instructions do.

[http://wiki.cockos.com/wiki/index.php/Installing_and_configuring_Wine](http://wiki.cockos.com/wiki/index.php/Installing_and_configuring_Wine)

That's about all I can help with.  Good luck!

-Tobeus

---

### Post by Lars Noodén on 2012-09-02
> **Raihan004 said:**
> dude i wana to learn how i install wine from source code .
i can easily install it from soft manager or terminal :lolflag:
but i dont know how i install it form source code?:mad:

so if you know process installing from source code,tell me:D

The wreckless way is to grab the tarball from the [Wine project's page](http://sourceforge.net/projects/wine/files/Source/) over at SourceForge.  Then extract the files and look at the file called README or INSTALL to find the instructions, in this case there is a file called README.  You will also have to fill any dependencies, the build process might need extras that the binary package does not.

However, the safe way to do it is to make your own Debian / Ubuntu package from the source and install that.  

[http://www.debian-administration.org/articles/336](http://www.debian-administration.org/articles/336)
[http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Debian-Binary-Package-Building-HOWTO.html](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Debian-Binary-Package-Building-HOWTO.html)

That will give you the best of both worlds.

---

