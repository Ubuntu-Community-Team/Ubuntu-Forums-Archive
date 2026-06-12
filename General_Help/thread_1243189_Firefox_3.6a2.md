---
title: "Firefox 3.6a2"
date: 2009-08-18
forum: General Help
---

### Post by Nater43 on 2009-08-18
How would I go about installing firefox 3.6a2 in Ubuntu? I have the file I need, but I'm not sure on how to get it to install. Probably an easy question, but I'm new with Ubuntu.

Thanks.

---

### Post by HiImTye on 2009-08-18
[How to install ANYTHING in Ubuntu!]("http://amitech.50webs.com/installing/index.php.html")

---

### Post by Nater43 on 2009-08-18
> **HiImTye said:**
> [How to install ANYTHING in Ubuntu!]("http://amitech.50webs.com/installing/index.php.html")

I'm getting a page load error.....

---

### Post by HiImTye on 2009-08-18
weird, works for me

what kind of file is it?

---

### Post by Nater43 on 2009-08-18
Its .tar.bz2.

---

### Post by HiImTye on 2009-08-18
here's from that page :)
> Source Package (.tar, .tar.gz, .tgz, .tar.bz, ...)     ***Note:** not all files with an extension named .tar, .tar.gz, and so on are archives with source code in them - they might be precompiled! If the archive is precompiled, there should be an installer or a binary executable inside it.*     
    
 Sometimes all you've got is a package full of uncompiled source code. Luckily, you don't need to be a programmer to know how to compile and install a package with source code. Back in the old days, this was the only way to install software on Linux and there *is* a standard way of installing these files. It will not work in every case, but it will in most (if you have the right dependencies installed). To compile a package you must first extract it somewhere. This is easily done, simply right-click on the package and select *Extract Here*.                [[IMG]http://amitech.50webs.com/installing/Extract.png[/IMG]]("http://amitech.50webs.com/installing/Extract.png")       
       [[IMG]http://amitech.50webs.com/icons/tango_video.png[/IMG] See a screencast of package contents being extracted]("http://i168.photobucket.com/albums/u178/anurag_panda/Extract_here.gif")
       To proceed you must have the compiler tools installed. They all come with the package *build-essential*, available in Synaptic. When you're sure you have the compiler tools installed, you fire up the terminal and change directory to the one you've just extracted (if you're not sure how to do that see: *[Navigating the terminal]("http://amitech.50webs.com/installing/index.php.html#navigating_the_terminal")*.       
      
      When you're in the correct directory you execute a configure script: ./configure. The purpose of the configure script is usually to check for dependencies and then create the makefile. If the script fails for some reason and tells you to install certain packages, look up the names in Synaptic (**Important!** If you find packages in Synaptic named almost the same but with a *-dev* extension, remember to install those as well! They're development packages and are needed for compiling). Don't worry if it complains that there is no configure script - many packages don't come with one! Then you compile it with make and after it's been compiled you can install it. There are two ways:       
      
      **Normal install:** If you want to install it the normal "primitive" way, type sudo make install. To remove the temporary files you run make clean. To uninstall the program you run sudo make uninstall. These two clean-up commands don't always work, though, the programmer needs to have enabled them.       
      
      **Package manager install:** If you want to install it in a way that means it can be easily removed from inside the package manager, first install the package *checkinstall*. To install the package type sudo checkinstall. This will take slightly longer than a normal install and quite possibly you'll have to supply a description of the application yourself (and edit the other information slightly). If the need arises, this will be easy to take care of from inside the checkinstall program.

---

### Post by kpkeerthi on 2009-08-18
Just extract the archive and run the **firefox** file contained within. No need to compile or anything.

---

### Post by Nater43 on 2009-08-18
> **kpkeerthi said:**
> Just extract the archive and run the **firefox** file contained within. No need to compile or anything.

I did, and it boots up Firefox fine, but I would like it to overwrite the firefox that came installed on Ubuntu, so I only have one.

---

### Post by kpkeerthi on 2009-08-20
> **Nater43 said:**
> I did, and it boots up Firefox fine, but I would like it to overwrite the firefox that came installed on Ubuntu, so I only have one.

There is no clean way. If you remove the firefox package that comes with Ubuntu, it takes away some important stuffs that is required. 

You could symlink /usr/bin/firefox to the beta you downloaded or create a separate launcher for it.

---

