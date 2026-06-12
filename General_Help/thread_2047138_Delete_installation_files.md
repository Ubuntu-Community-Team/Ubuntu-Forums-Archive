---
title: "Delete installation files"
date: 2012-08-24
forum: General Help
---

### Post by dagring on 2012-08-24
When you untar a tar ball and install the program, is it natural to delete the untared files? In Windows when one unpack program files and run the install file, all the necessary files are put in the program folder. The rest can be delted. Is it the same in Linux?

Dag R

---

### Post by drmrgd on 2012-08-24
If you mean the original tarball from which you've extracted files and installed, then sure.  If you don't need a copy around for any reason, then you can delete it.  The program won't use any files that haven't been unpacked into the program directory.

---

### Post by qamelian on 2012-08-24
Just be aware that, if this a a program you compiled from source, the uninstall script will usually be in the same folder as the extracted files. If you decide to remove the program for any reason, it will get messy and difficult without this script.

---

### Post by dagring on 2012-08-24
I mean the files which are unrared. I'm a little confused about where  the untared files should be placed, and if they are the real program. In windows it's only: path, yes, yes, and the installation is finished. Linux have another model.

Dag R

---

### Post by qamelian on 2012-08-24
> **dagring said:**
> I mean the files which are unrared. I'm a little confused about where  the untared files should be placed, and if they are the real program. In windows it's only: path, yes, yes, and the installation is finished. Linux have another model.

Dag RThe only way to know for sure is to read the README and possibly other docs included in the archive.

---

### Post by nerdux on 2012-08-24
> **dagring said:**
> I mean the files which are unrared. I'm a little confused about where  the untared files should be placed, and if they are the real program. In windows it's only: path, yes, yes, and the installation is finished. Linux have another model.

Dag R

Linux's installation model is easier than window's, provided the program you need is in the repositories, which happens 90% of the time (are we talking Ubuntu here?). Just sudo apt-get install it, and it will be downloaded/installed. You could also use synaptic from a graphic terminal. And getting all your software automagically arranged by functionality in your menu at installation time is quite a bonus!.

---

### Post by drmrgd on 2012-08-24
> **dagring said:**
> I mean the files which are unrared. I'm a little confused about where  the untared files should be placed, and if they are the real program. In windows it's only: path, yes, yes, and the installation is finished. Linux have another model.

Dag R

Well, you're welcome to store those where you like.  In Windows, you'll have a Program Files directory with all of the local program content, and occasionally some satellite portions of the programs in Users directories.  Windows, since it uses a registry, is a little more particular about where things are stored with regard to programs.  

However, Linux is more flexible in this regard, and uses the a few system variables to find where libraries are located and other helpers.  Also, launching programs can be done from anywhere, assuming that the executable (in Linux these are called binaries) files are located somewhere you have access.  

One of the big things that depends on how you do things is whether you have a multiuser server (or home computer for that matter), or just a single user home computer.  Classically (although this is not at all a rule!), program files could be stored in the /opt directory, which I believe was intended as the place to store add-on packages similar to Windows' Program Files.  Here's a little more info:

[http://www.linuxtopia.org/online_books/linux_beginner_books/linux_filesystem/opt.html](http://www.linuxtopia.org/online_books/linux_beginner_books/linux_filesystem/opt.html)

In order to actually launch that package from the command line, though, you'd have to navigate to the package binary and launch it from there, which as you might imagine is a pain.  Therefore the idea of the $PATH enviroment variable was implemented to tell the system to look there for routine paths to binaries.  This is why in the terminal, you don't have to run:

```
/bin/ls ~/Documents
```

You can leave off the '/bin/' part because the system is going to look in your $PATH variable of which /bin/ is a part.  To see what's in your $PATH, you can run:

```
echo $PATH
```

That will tell you all the places the system will look for binaries by default.  However, you'll notice that /opt/ is not part of the $PATH, which is normal.  In order to keep things cleaner, the system puts things in a series of /bin folders.  I get a little confused over the exact purpose of all of these, and I'm too new to Linux / Unix to appreciate it, I'm sure!  There is an absolute wealth of info on the web in terms of the exact use for each folder, although again, things are flexible - especially on a home system.  You can run:

```
man hier
```

to get a quick snapshot on the each directory of a typical system and its purpose.  

At any rate, we need to have the binary for the program accessible to some place in your $PATH.  To do that, we'll make a symbolic link (the Linux equivalent of a Windows shortcut) to the binary in a directory that is part of your $PATH using the 'ln -s' command. Since we're making a system change, we'll need admin privileges to do it (again, I'm assuming a single-user system - there is a way to do this on a server by creating a /bin directory inside of your /home folder, which is automatically part of your $PATH).  So:

```
sudo ln -s /opt/my_program_directory/myprogram /usr/bin/myprogram
```

After that, you can just type 'myprogram' from anywhere, and the system will launch it just like it'll launch any other commands (like ls) from anywhere.  

As one final example, and a real case study, here's how Google-Chrome is setup on my computer:

```
/opt/google/chrome $ ls
chrome                          locales                product_logo_256.png
chrome.pak                      nacl_helper            product_logo_32.png
chrome-sandbox                  nacl_helper_bootstrap  product_logo_32.xpm
default-app-block               nacl_irt_x86_32.nexe   product_logo_48.png
default_apps                    nacl_irt_x86_64.nexe   product_logo_64.png
google-chrome                   PepperFlash            resources.pak
google-chrome.desktop           product_logo_128.png   theme_resources_standard.pak
libffmpegsumo.so                product_logo_16.png    ui_resources_standard.pak
libpdf.so                       product_logo_22.png    xdg-mime
libppGoogleNaClPluginChrome.so  product_logo_24.png    xdg-settings
/opt/google/chrome $ which google-chrome 
/usr/bin/google-chrome
ls -l /usr/bin/google-chrome 
lrwxrwxrwx 1 root root 32 Aug 16 19:42 /usr/bin/google-chrome -> /opt/google/chrome/google-chrome
```

You can see that I have Google Chrome installed in /opt/google/chrome/, which is where the binary is located.  In order to not have to type /opt/google/chrome/google-chrome each time I want to launch it from the terminal, I have a symbolic link to that binary in /usr/bin, which is part of my $PATH.  So, all I have to do now, is type 'google-chrome' from anywhere and it'll launch.

I hope that makes sense.  Post back if you still have questions.

---

### Post by dagring on 2012-08-28
Thanx very much "drmrgd" for your tutorial. I have read and tested the things you wrote. I feel I now understand more of the details concerning paths, folders and the installation process.

Dag R

---

