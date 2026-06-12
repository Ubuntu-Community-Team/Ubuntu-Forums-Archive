---
title: "Question Regarding Installing Software"
date: 2006-02-08
forum: General Help
---

### Post by NuNn DaDdY on 2006-02-08
When I download a compressed file my archive manager comes up and I extract it to a specified location to be installed.  But when i go to the folder where I extracted it to all the contents of the file are there but I'm unable to install the software to run the program.  I was wondering is there a command that I have to issue in order to install the software or am I going about this completly the wrong way and should just be using the command prompt to extract and install the software.  Thanks.  :-D

---

### Post by GeneralZod on 2006-02-08
Here's a good beginner's guide to installing software, written by current Beanie of the Month, aysiu.  Basically, if you try to install software under Linux like you would under Windows, you'll have a very difficult time ;)

[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by MartinG on 2006-02-08
First, the best way to install software is to get it from the repositories, using synaptic or apt-get.  Are you sure the program you want isn't available that way?

If you do have to work from a tar file, you need to install "build-essential" (via synaptic) and I'd also recommend "checkinstall".  Once you have these, open a terminal in the folder where you've extracted the files, and run the following three commands, one after the other:```
./configure
make
sudo checkinstall
```Be prepared for a long wait at each step!  This process will ultimately build a deb package and install it.  If you don't use checkinstall, the last line should be "sudo make install", and in this case there won't be a deb package built but the program will be installed directly -- which can cause problems later over uninstalling or updating.

Doing it this way can have you chasing all over the place trying to meet dependencies, which is another very good reason for using the repositories if at all possible.

---

### Post by lamego on 2006-02-08
Usually .tar.gz compressed software comes with a nice INSTALL or README files that you should read ;)

---

