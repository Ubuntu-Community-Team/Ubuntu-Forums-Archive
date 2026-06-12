---
title: "Installing Tar.gz files??"
date: 2006-04-27
forum: General Help
---

### Post by morbid_bean on 2006-04-27
How do I install a tar.gz file in the terminal???

---

### Post by Qrk on 2006-04-27
tar.gz is an archive. The way to install a tar.gz depends on what is in the archive, much like .zip on windows.

The syntax is this:
```

tar -xvvzf filename.tar.gz
```

Which will extract it to the current directory.

Once you've extracted it, there should be a readme (if the devolopers were nice) telling you which scripts is the install script. Usually, but not always, nicely named install.sh

```
./install.sh
```

Will install it 9 times out of ten.

---

### Post by Sef on 2006-04-27
Here's a tutorial on installing software on Ubuntu.  Scroll towards the bottom for installing from source.

[http://www.psychocats.net/ubuntu/installingsoftware.php]("http://www.psychocats.net/ubuntu/installingsoftware.php")

Also to compile, build-essential needs to be installed.

sudo apt-get update

sudo apt-get install build-essential

---

### Post by trenta91 on 2007-12-10
> **Qrk said:**
> tar.gz is an archive. The way to install a tar.gz depends on what is in the archive, much like .zip on windows.

The syntax is this:
```

tar -xvvzf filename.tar.gz
```

Which will extract it to the current directory.

Once you've extracted it, there should be a readme (if the devolopers were nice) telling you which scripts is the install script. Usually, but not always, nicely named install.sh

```
./install.sh
```

Will install it 9 times out of ten.

well, i am very new to ubuntu 7.10, i intsalled it just yesterday.
so i searched google all day today, and only found stuff like this with the codes and stuff....
but nothing says where to type the codes and i have been very frustrated.:mad:
if someone could tell me what program i should use for thse codes and where to find it, it would be such a help, thanks

---

### Post by amugofcoffee on 2007-12-10
If this is source code, then you need to extract it into a suitable directory and compile it. Make sure you have build-essential installed.

What you then do is enter the directory via Terminal, e.g. if the folder is in /home/foo/foobar-1.0/, then enter in terminal: **cd /home/foo/foobar-1.0/**.

What you then might need to do is chmod the configure file a+x, so enter in: **chmod a+x configure**.

Then, you run: **./configure**.

Then, as super user, run **make** then **make install**.

And it should be done :D

---

