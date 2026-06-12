---
title: "install tar.gz archives on ubuntu 10.10"
date: 2011-04-13
forum: General Help
---

### Post by rekharajct on 2011-04-13
I have downloaded a petri net tool petrify.tar.gz.Then extracted it using archive manager.But unable to install it.How could I install it?Is there any commands or instructions for installing it?

---

### Post by rekharajct on 2011-04-13
I  have downloaded a petri net tool petrify.tar.gz.Then extracted it using  archive manager.But unable to install it.How could I install it?Is  there any commands or instructions for installing it?

---

### Post by mendhak on 2011-04-13
Usually, there's either a readme file, or there's a bash script or there's a ready-executable in the extracted contents.

If you can't find any of those, can you show us where you got the .tar.gz from (assuming it's public)?  We could have a look too.

---

### Post by mcduck on 2011-04-13
A .tar.gz file is just an archive (like a .rar or a .zip file), and can contain anything inside it. It's impossible to say how to  install a specific .tar.gz if the package itself, or the site you downloaded it from, doesn't provide you with instructions.

Perhaps the package contains source code, and you'll have to compile it. Or it might contain a ready-made executable file that you just drop where you want it and run. Or something completely different.

---

### Post by howefield on 2011-04-13
Duplicate threads merged.

Please refrain from posting duplicate threads, it can make it difficult for anyone trying to help you.

---

### Post by rekharajct on 2011-04-18
I downloaded petrify.tar.gz from [www.lsi.upc.edu/~jordicf/petrify]("http://www.lsi.upc.edu/%7Ejordicf/petrify.The")
The archive that I downloaded contains an INSTALL file.But it do not have any instructions for installing.

---

### Post by thecamelcoder on 2011-04-18
> **rekharajct said:**
> I downloaded petrify.tar.gz from [www.lsi.upc.edu/~jordicf/petrify]("http://www.lsi.upc.edu/%7Ejordicf/petrify.The")
The archive that I downloaded contains an INSTALL file.But it do not have any instructions for installing.

Links dead mate. 

You may need to compile a this application for your local system, which will mean that there will be a config file in the root of the archive. 

Normally whats happens is that you go 
./configure which checks for dependecies on your system
make install which makes the installation file and then
install which installs the application. 

If you can find a live link for the package that you have i'll look into it further for you. 

):P

---

### Post by mcduck on 2011-04-18
> **rekharajct said:**
> I downloaded petrify.tar.gz from [www.lsi.upc.edu/~jordicf/petrify]("http://www.lsi.upc.edu/%7Ejordicf/petrify.The")
The archive that I downloaded contains an INSTALL file.But it do not have any instructions for installing.

The INSTALL file is pretty much all the installation instructions there are for that application. Based on it, it's an already-complied program which you can just extract where you want it and run from there.

---

### Post by rekharajct on 2011-04-18
I copied the archive to /usr/bin directory and extracted it there.But whenever I attempt to perform any operations on petrify or simply type petrify following error occurs
bash: /usr/bin/petrify: No such file or directory

---

### Post by luigi_mb on 2011-04-18
> **rekharajct said:**
> I copied the archive to /usr/bin directory and extracted it there.But whenever I attempt to perform any operations on petrify or simply type petrify following error occurs
bash: /usr/bin/petrify: No such file or directory

As macduck says, the package already contains the binaries. Do not copy the "archive" (unpacked or not) to /usr/bin/ . Assuming you have unpacked the archive in your home folder, just do

```

cd petrify
bin/petrify

```


/luigi

---

### Post by rekharajct on 2011-04-22
Thanks a lot .It worked.For the proper functioning of petrify tool , graphviz package is also required.Now everything works well.Once again thanks you very much.:)

---

