---
title: "installing app using a tar.gz file"
date: 2011-03-21
forum: General Help
---

### Post by retrodans on 2011-03-21
Hello, in the past, all my installation have been done using synaptic package manager, but I have come across a situation where I would like to install an application which only has a tar.gz file not a .deb file.

How should I go about installing it, do I just unpack to root, or is there a method of installation I should run through.

The application I would like to install is:
[http://www.charlesproxy.com/download/](http://www.charlesproxy.com/download/)

Thankyou for your help,
Dan

---

### Post by TeoBigusGeekus on 2011-03-21
[https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

---

### Post by SeijiSensei on 2011-03-21
Looks like you can just unpack the tar.gz archive into your home directory, then run the charles.sh script like this:

```

cd ~
tar xzvf /path/to/charles.tar.gz
charles/bin/charles.sh

```

You'll have to have Java installed as well.

---

### Post by retrodans on 2011-03-21
Thankyou for your wift response, I had also missed something else, I had to go to the *.sh file, right click, and set the permissions to allow execution, as it wasn't letting me through GUI or through terminal.

Thanks again,
Dan

---

### Post by jerome1232 on 2011-03-21
I just wanted to add generally anything that comes as a tar.gz is either a precompiled binary, the program itself ready to go, or the source code. In all cases the author of the software *should* provide decent documentation in the archive or on the site. Always remember to have a look in the archive for a readme file of some sort.

---

