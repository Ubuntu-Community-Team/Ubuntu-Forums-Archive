---
title: "Installing programs"
date: 2006-04-16
forum: General Help
---

### Post by agentx606 on 2006-04-16
I am new to Linux, I have Unbuntu Linux installed on my computer now. I have noticed that if you go to add new program there is a list that you can choose from and you check them and it will install them for you. but I was wondering how you install programs that you download on your own, for example, I downloaded Clamav and I just can't figure out how to install it. ](*,) 

any help would be greatly appreciated such as some good tips for new users and help with what I have already stated. thank you.

---

### Post by xXx 0wn3d xXx on 2006-04-16
[QUOTE=agentx606]I am new to Linux, I have Unbuntu Linux installed on my computer now. I have noticed that if you go to add new program there is a list that you can choose from and you check them and it will install them for you. but I was wondering how you install programs that you download on your own, for example, I downloaded Clamav and I just can't figure out how to install it. ](*,) 

any help would be greatly appreciated such as some good tips for new users and help with what I have already stated. thank you.[/QUOTE]

If it is a .deb file, in terminal type:

> sudo dpkg -i nameoffile
-----------------------------------------
If it is a .tar.gz/bz

1. Put it in your home directory

2. Right click it and select "Extract Here."

3. In terminal type:

> cd name-of-directory

4. Type
> ./configure

5. Then 
> make

6. Then
> sudo make install

6a. If you want a .deb file, install check install:
> 
sudo apt-get install checkinstall

Then instead of "sudo make install, type:

> sudo checkinstall
---------------------------
If that doesn't work read the README file from the extracted directory.

---

### Post by croak77 on 2006-04-16
Just apt-get install clamav. It's in the repo's.

---

### Post by xXx 0wn3d xXx on 2006-04-16
[QUOTE=croak77]Just apt-get install clamav. It's in the repo's.[/QUOTE]
Yeah, but it is most likely not the newest one.

---

### Post by Ensnared on 2006-04-16
This usually varies between the different programs. The best bet for any Ubuntu-user is to download a deb-package of the program, but these aren't always available. It's then a matter of preference if you want to either download the source and compile it yourself, or download another package (like rpm, which is often available) and convert that to a deb using alien.

If you've downloaded a deb-package, you install it like this:
```
sudo dpkg -i filename.deb
```

If you've downloaded an rpm-package, you can convert it like this:
```
sudo alien filename.rpm
```

You may need to install alien before that will work, in which case you do this:
```
sudo apt-get install alien
```

You can then install the resulting deb-file like any other deb-file.

If you've downloaded the source archive of the program, you'll have to compile it and then install it. This usually requires additional packages installed on your system, and it may sometimes fail due to lack of specific developement-files that the program needs. But provided all of this is installed on your system, the way to do it is normally like this:
```
tar fzx filename.tar.gz
cd created_folder
./configure
make
sudo make install
```

This will compile the program and install it, but in some cases the process is slightly different, so _always_ consult the accompanying README and/or INSTALL files located in the directory created when untar'ing the archive.

A good replacement for "sudo make install" is using "sudo checkinstall" (requires checkinstall to be installed - "sudo apt-get install checkinstall"), which will generate a deb-file and install that instead of simply copying the files into the directories. This makes it a lot easier to remove or upgrade the program at a later date, as you can just remove it using "dpkg -r package" (or "dpkg --purge package" to remove all configuration-files and such as well as the main program files/libraries/documentation/etc).

In most cases, the installation instructions are also available at the website for the application, especially where compiling from source is the only method. They will also list any required libraries and such for compiling it.i

In any event, if you're going to compile anything on an Ubuntu system, you will probably want to simply install the "build-essential" meta-package. You do this like so:
```
sudo apt-get install build-essential
```

---

