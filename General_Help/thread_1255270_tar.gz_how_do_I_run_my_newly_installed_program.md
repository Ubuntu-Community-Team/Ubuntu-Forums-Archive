---
title: "tar.gz how do I run my newly installed program?"
date: 2009-09-01
forum: General Help
---

### Post by b3n0 on 2009-09-01
Hey all,

This is my first time playing around with tar.gz files, I'm learning heaps. I've followed 3 or 4 different tutorials. I mainly went by this though. [http://ubuntuforums.org/showthread.php?t=246092](http://ubuntuforums.org/showthread.php?t=246092)
I'm wanting to install Dvd::rip and Jahshaka. I haven't gotten to Jashaka yet.

Here are the steps I've taken.

1 Unzip.
```
tar -zxvf dvdrip.tar.gz
```

2 Navigate into the new folder
```
cd dvdrip/
```

3 Compile
```
./configure
```
```
make
```
```
sudo checkinstall
```
(note you must have checkinstall installed first sudo apt-get install checkinstall)

The it gives me...
> 
**********************************************************************

 Done. The new package has been installed and saved to

 /home/benjamin/dvdrip-0.98.10/dvdrip_0.98.10-1_amd64.deb

 You can remove it from your system anytime using: 

      dpkg -r dvdrip

**********************************************************************

Ok so I understand that a new compiled .deb has been created. But it says it has been installed _and_ saved. How do I run this newly installed app? Is there a GUI way? I've looked under all the menus. 

As you can tell I'm very use to the repos, however I am enjoying this lesson.

Cheers.

---

### Post by NoaHall on 2009-09-01
Is it a command line application? It won't appear in the menu if it is.

sudo dpkg --install /home/benjamin/dvdrip-0.98.10/dvdrip_0.98.10-1_amd64.deb

---

### Post by b3n0 on 2009-09-01
> **NoaHall said:**
> Is it a command line application? It won't appear in the menu if it is.

sudo dpkg --install /home/benjamin/dvdrip-0.98.10/dvdrip_0.98.10-1_amd64.deb

No it's supposed to have a GUI.
[http://www.exit1.org/dvdrip/](http://www.exit1.org/dvdrip/)

I ran your command, it hasn't changed anything. When I was doing my own trouble shooting I also tried installing the .deb package but through the GUI way. 
Just thinking out loud... Do tar.gz files even create menu short cuts automatic? Or do I need to create my own short cuts?

---

### Post by jacksaff on 2009-09-01
Run it by typing dvdrip at the command line.
If it works as desired you can easily make an entry for it in your menu. If it's not a gui program you can still make an entry to start a shell and run it.

By the way, dvdrip is in the repositories. You could have installed it with the command 

sudo apt-get install dvdrip

or by searching for it in a package manager such as synaptic.

---

### Post by b3n0 on 2009-09-01
> **jacksaff said:**
> 

By the way, dvdrip is in the repositories. You could have installed it with the command 

sudo apt-get install dvdrip

or by searching for it in a package manager such as synaptic.

Thanks for the advise, I was trying to learn .tar.gz compiling. But in this case I may opt for the easy way out.

This is what I get when I type dvdrip into the terminal.
> benjamin@B3n0:~$ dvdrip
Can't locate Locale/TextDomain.pm in @INC (@INC contains: lib /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/local/bin/dvdrip-splash line 8.
BEGIN failed--compilation aborted at /usr/local/bin/dvdrip-splash line 8.
Can't locate Locale/TextDomain.pm in @INC (@INC contains: lib /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/local/bin/dvdrip line 36.
BEGIN failed--compilation aborted at /usr/local/bin/dvdrip line 36.


I'm I missing some dependant files?

---

### Post by Topsiho on 2009-09-01
If you look in the map in which you did the install you'll probably find a file with the name dvdrip.

If necessary you'll have to make it executable with

chmod +x dvdrip

though often that is not necessary as it already is executable.

Then run it with ./dvdrip

and if all is OK then it runs :)

the ./dvdrip command says that it should look for the file dvdrip in the present directory. Otherwise it will probably not be found.

Installing from a .tar.gz file is an interesting exercise :)

Topsiho

---

### Post by NoaHall on 2009-09-01
Try using "sudo ldconfig" and then do it again. After, if that fails, install perl.

---

### Post by b3n0 on 2009-09-01
Genius guys! It's working well!
Thanks heaps for your help.

One more .tar.gz related question. I'm trying to install Jahshaka now. I'm noticing that it's a step up from DVD::rip. When I run the configure script this is what I get.
> benjamin@B3n0:~/jahshaka$ ./configure 
>>Configuring build type for jahshaka

./configure: 57: qmake: not found
---------------------------------------
Jahshaka Configure Script User Commands
---------------------------------------

SYNOPSIS

     ./configure [ switches ]
     ./configure [ switches ] jahshaka
     ./configure [ switches ] jahplayer

DESCRIPTION

     Configures the jahshaka build process to build either jahshaka
     or jahplayer

     By default running configure with no arguments will activate the
     build for jahshaka

     You need to follow the configure command with the make command
     in order to actually build the software!

SWITCHES

     --prefix=path
          sets the path for the installation (default: /usr/local)

     --disable-debug
          sets debug mode off

     --disable-plugins
          disables the plugin build and install

     --enable-static
          disables the dynamic loading of various open libraries


Now this seems to make a  bit of sense. I'm only struggling stringing together what the new command would be.
I came up with this 
```
./configure --prefix=path jahshaka
```
it did not work. Where am I going wrong?

Cheers, again.

---

### Post by Topsiho on 2009-09-01
Glad it works now :)

Considering your next question: if it needs qmake this means that the application was written using Qt4, or maybe Qt3? If you use KDE then it is already installed (KDE4 -> Qt4 and KDE3 -> Qt3 (I think)).

Maybe there is a README included wherein you can find useful directions.

An application written in Qtx is compiled like so:

qmake -project
You'll have a file called applicationname.pro after this

qmake
You'll have a Makefile after this. In this file are instructions on how to compile the application, based on what is in your computer, for:

make (or: sudo make)
You'll have a file applicationname, which is the executable.

Looksee what you have already and continue from there. If you have Qtx installed, of course.
Hope this helps.

For applicationname you must substitute the name of the application :)

Topsiho

---

### Post by b3n0 on 2009-09-02
Ok now I'm a little confused.

> benjamin@B3n0:~/jahshaka$ ls
AUTHORS                jahshaka.spec
config.pro             jahshaka_vc71.sln
configure              jahshaka_vc71_static.sln
configure.bat          jahshaka_vc71_static.vcproj
COPYING                jahshaka_vc71.vcproj
database               jahshaka_vc8_static.sln
docs                   jahshaka_vc8_static.vcproj
fonts                  jahshaka.xcode
INSTALL                jahuserinstall
installer              media
jahinstall_data.pro    openlibraries-win32-installer
jahinstall_proc.pro    Pixmaps
jahplayer.pro          plugins
jahplayerSettings.pro  process_dynamic_settings.pro
jahplayer.spec         README
jahplayer_vc71.sln     release_notes.htm
jahplayer_vc71.vcproj  scenes
JahshakaCommunity.url  Settings.pro
jahshaka.kdevelop      source
jahshaka.pro           TODO
JahShaka.rc            utils
jahshakaSettings.pro
benjamin@B3n0:~/jahshaka$ 


Inside the INSTALL file this is what I have
> The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes a while.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Type `make install' to install the programs and any data files and
     documentation.

  4. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  

Thanks for the tips Topsiho.

I tried the following...
```
benjamin@B3n0:~/jahshaka$ qmake -jahshaka.pro

```
I get this error
> benjamin@B3n0:~/jahshaka$ qmake -jahshaka.pro
The program 'qmake' can be found in the following packages:
 * qt3-dev-tools
 * qt4-qmake
Try: sudo apt-get install <selected package>
bash: qmake: command not found
benjamin@B3n0:~/jahshaka$ 

I also tried installing 'Qmake' with the apt-get funtion.
No go sorry, any other ideas?

---

### Post by P4man on 2009-09-02
You have to install qmake first:

```
sudo apt-get install qt4-qmake 
```

---

