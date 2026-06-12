---
title: "foxit 64 bit help"
date: 2009-08-05
forum: General Help
---

### Post by Strongman332 on 2009-08-05
i am trying to install foxit on my 64 bit machine but it is a 32 bit deb i dont know what to do here

---

### Post by kimo9909 on 2009-08-09
After you download it from [http://www.foxitsoftware.com/pdf/desklinux/](http://www.foxitsoftware.com/pdf/desklinux/) you need to extract the files to run the application.  below you will find the instruction to setup as I did in Ubuntu 64 bit.

[LIST=1]
[*]Download the tarball
[*]Create a folder called "bin" in your HOME directory (which is folder with the same name as you login)
[*]***NOTE: I use the "bin" directory for all of my downloaded applications that are not "installed"
[*]Create a folder named "Foxit_Reader"
[*]Extract the contents of the tarball to that folder
[*]Run click/dbl click the "Foxit" executable (also add it to the menu if you like)
[/LIST]

After that you are done.  Keep in mind that the "bin" directory is just a directory like any other.  I use it for Foxit Reader, Eclipse, etc.  I hope this helps!  :cool:

---

### Post by kimo9909 on 2009-08-09
Alternatively you can follow the instructions below to install using the package they provide [[COLOR="Blue"]here[/COLOR]]("http://mirrors.foxitsoftware.com/pub/foxit/reader/desktop/linux/1.x/1.0/enu/FoxitReader_1.0-1_i386.deb").

Use the root account (SUDO will do) on terminal to execute the below command for installation.
(sudo) dpkg -i FoxitReader_1.0-1_i386.deb

Use the root account on terminal to execute the below command for uninstallation.
(sudo) dpkg -r FoxitReader

---

### Post by beadrifle on 2010-04-04
sudo dpkg -i --force architecture Foxitreader... works

---

### Post by vickoxy on 2010-08-09
> **kimo9909 said:**
> Alternatively you can follow the instructions below to install using the package they provide [[COLOR="Blue"]here[/COLOR]]("http://mirrors.foxitsoftware.com/pub/foxit/reader/desktop/linux/1.x/1.0/enu/FoxitReader_1.0-1_i386.deb").

Use the root account (SUDO will do) on terminal to execute the below command for installation.
(sudo) dpkg -i FoxitReader_1.0-1_i386.deb

Use the root account on terminal to execute the below command for uninstallation.
(sudo) dpkg -r FoxitReader

Thanks! :popcorn:

The best PDF REader for now on my 64bit Ubuntu...

---

### Post by nothingspecial on 2011-09-13
Thread closed

---

