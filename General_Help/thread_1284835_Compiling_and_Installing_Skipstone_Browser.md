---
title: "Compiling and Installing Skipstone Browser"
date: 2009-10-07
forum: General Help
---

### Post by BoogieTrain on 2009-10-07
Hi. Im trying to install skipstone.

I am running ubuntu 9.4 i beleive. Netbook Remix. 

i downloaded the source tarball and extracted it using the GUI file manager. I then used the terminal to cd into the directory i extracted from the tarball. I tried a ./configure and got this:

phil@philmini9:~/Desktop/skipstone-1.0.1$ ./configure
configure: error: Cannot find mozilla includes - please use --with-mozilla-includes=path_to_mozilla_includes and specify a path

Earlier today i ran a system update through the built in package manager so everything should be up to date. I do have firefox, it was installed with NBR and it was updated when i ran the update.It is

 3.0.14 Firefox for Ubuntu 1.0

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.14) Gecko/2009090216 Ubuntu/9.04 (jaunty) Firefox/3.0.14

If anyone could help me get skipstone installed that would be great. Thanks all.

Here is skipstone: [http://www.muhri.net/skipstone/page.php3?node=home](http://www.muhri.net/skipstone/page.php3?node=home)

i see this on the webpage:

To compile it, you need the mozilla headers, if you dont have them, thats ok 
you can run the compiled binary, you will just have to export your 
environments if your mozilla installation is not in /usr/local/ or /usr like 
this:   export MOZILLA_FIVE_HOME=/usr/local/lib/mozilla 
  export LD_LIBRARY_PATH=/usr/local/lib/mozilla:$LD_LIBRARY_PATH  
 then run ./skipstone-bin from the same directory after you run make or make install, you can 
pass it a url for an argument at the command line also. If your Mozilla libs are in regular system directories, skipstone script will take care of it. 
 Enjoy. 



Now, i'd rather compile it myself (this is generally better right?) than use binaries. What do you gouys think? Should i just run those commands, or should I actaully compile this program myself?

---

### Post by BoogieTrain on 2009-10-07
okay i ran both import commands but still no dice.

phil@philmini9:~/Desktop$ cd skipstone-1.0.1/
phil@philmini9:~/Desktop/skipstone-1.0.1$ ls
acconfig.h    config.h      config.status  convert_bookmarks.pl  install-sh   pixmaps         skipstone.spec
AUTHORS       config.h.in   configure      COPYING               locale       plugins         skipstone.spec.in
ChangeLog     config.log    configure.in   icons                 Makefile     README          src
config.cache  config.mk.in  config.webkit  INSTALL               Makefile.in  README.copying  stamp-h.in
phil@philmini9:~/Desktop/skipstone-1.0.1$ make
(cd src && make)
make[1]: Entering directory `/home/phil/Desktop/skipstone-1.0.1/src'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/home/phil/Desktop/skipstone-1.0.1/src'
make: *** [all] Error 2
phil@philmini9:~/Desktop/skipstone-1.0.1$ make install
(cd src && make install)
make[1]: Entering directory `/home/phil/Desktop/skipstone-1.0.1/src'
make[1]: *** No rule to make target `install'.  Stop.
make[1]: Leaving directory `/home/phil/Desktop/skipstone-1.0.1/src'
make: *** [install] Error 2
phil@philmini9:~/Desktop/skipstone-1.0.1$ ./configure
configure: error: Cannot find mozilla includes - please use --with-mozilla-includes=path_to_mozilla_includes and specify a path
phil@philmini9:~/Desktop/skipstone-1.0.1$ 


Help!

---

