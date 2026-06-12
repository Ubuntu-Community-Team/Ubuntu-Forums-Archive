---
title: "Some RoadBlocks.. Pls help.."
date: 2006-05-25
forum: General Help
---

### Post by vinodis on 2006-05-25
I am migrating to Kubuntu from WinXP. Sofa so good.. But now facing some problems.. can someone help?

I have no internet connection at home. So cannot use apt-get . I download the source or .deb files from office n/w and take it home on USB drive. I wanted AutoMatix and downloaded the [Automatix Offline CD]("http://iso.mrbass.org/AutomatixCD-1.0rc1.zip") to install at home. One problem is sometimes .deb files are not available for things like koffice, kchm and some KDE themes. I am not able to compile from source. When I try to type CC or gcc on the Konsole, it says invalid command. But when I try 'whereis/locate cc' it shows it under /usr/..../X11 directory. So I assumed that I need to change the PATH variable to include that. But when I type $PATH it shows the same directory. I dont know why it is not picked up. How can I EDIT the environmment variables in Linux so that it is applied globally and not locally on a Konsole box. 

I tried installing Kompile to resolve the issue of manually compiling the source, but Kompile is not getting installed properly because of the dev-sources issues. 

Do I need to install any development/compiling oriented packages specially to compile from source. I thought it would have got installed from Automatix CD.
If I have to, where can I download the .deb files for that. Whenever I search in the package search of [Kubuntu site ]("http://packages.ubuntu.com/") I get a lot of dependent things, and most of the time its multiple files, so which ones to install first. 

Please help.
Thanks many in advance.
:)

---

### Post by [S|G] on 2006-05-25
Well, do you have gcc packages installed? If you don't, you have to install it. The package names are:

gcc-4.0
gcc-4.0-base
gcj-4.0-base
gcc-3.4 (its good to have 3.4 as a fallback alternative)
gcc-3.4-base
g++-4.0 (if you plan to compile C++ programs)
g77-3.4

Well, these are the packages I have here. Someone correct me if I'm wrong or missing something :P

---

### Post by nanotube on 2006-05-25
compilers and stuff are not installed by default in ubuntu. to get them installed, install the "build-essential" package.
since you have no internet, you will have to download all the dependencies of the build-essential package by hand, and then install them. you can see the dependencies if you go to packages.ubuntu.com and browse to the build-essential package.

---

### Post by nanotube on 2006-05-25
[QUOTE='[S|G]']Well, do you have gcc packages installed? If you don't, you have to install it. The package names are:

gcc-4.0
gcc-4.0-base
gcj-4.0-base
gcc-3.4 (its good to have 3.4 as a fallback alternative)
gcc-3.4-base
g++-4.0 (if you plan to compile C++ programs)
g77-3.4

Well, these are the packages I have here. Someone correct me if I'm wrong or missing something :P[/QUOTE]

he'll probably also need "make" and things, not just gcc, in order to build from source...

---

### Post by vinodis on 2006-05-25
I tried to download the build-essential.deb package. But its a mere 8kb file.
whats going wrong?!

---

### Post by nanotube on 2006-05-25
[QUOTE=vinodis]I tried to download the build-essential.deb package. But its a mere 8kb file.
whats going wrong?![/QUOTE]
build-essential is just a meta-package that pulls in a bunch of dependency package. that's why i said you should download the /dependencies/ of build-essential, rather than build-essential itself. :)

---

### Post by Jucato on 2006-05-25
I thought the build-essentials package is available on the install CD of Ubuntu/Kubuntu? I'm not sure about KOffice, though.

As for kchmviewer, I had to install it from source. Don't be too afraid of it. The hard part is getting the necessary files (like build-essentials) installed. after that, if all goes well (as it did with me), it's as easy as "./configure", "make", "sudo make install".

---

### Post by [S|G] on 2006-05-25
Take a look here:
[http://packages.ubuntulinux.org/dapper/devel/build-essential](http://packages.ubuntulinux.org/dapper/devel/build-essential)

You have to actually download the packages that it depends on

---

