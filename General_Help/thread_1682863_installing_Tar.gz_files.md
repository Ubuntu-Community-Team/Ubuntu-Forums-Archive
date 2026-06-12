---
title: "installing Tar.gz files?"
date: 2011-02-06
forum: General Help
---

### Post by 4042966262 on 2011-02-06
ok, i have 2 programs i would like..
GoodWeather-White.tar.gz (1).crdownload
and
h3d-v-0.9.tar.gz
both are tar.gz files, currently in the ''downloads box''


folowing this tut, 
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
i got as far as
''qoute sudo chmod u+rwx /usr/local/src ''
when i copy (click and drag) my tar.gz file to /usr/local/src (which shows / on title bar)
i get an error.
an i doing this wrong? how do i compile the code?:confused:

---

### Post by jroa on 2011-02-06
You don't need to move it.  Just modify the command so that the path goes to where ever the file is located.  Where are the files located now?

---

### Post by 4042966262 on 2011-02-07
sitting in the downloads box.   
/home/kimball/Downloads

---

### Post by 4042966262 on 2011-02-07
i just tried qoute sudo chmod u+rwx/home/kimball/Downloads and got

kimball@kimball-desktop:~$ qoute sudo chmod u+rwx/home/kimball/Downloads
No command 'qoute' found, did you mean:
 Command 'route' from package 'net-tools' (main)
qoute: command not found
kimball@kimball-desktop:~$

---

### Post by wojox on 2011-02-07
Drop the "quote sudo" 

Their is no quote and you don't need sudo in your home directory.

---

### Post by lykeion on 2011-02-07
If you want the Good Weather desklet you can follow this graphical guide: [http://www.howtoforge.com/gnome_gdesklets](http://www.howtoforge.com/gnome_gdesklets)

---

### Post by 4042966262 on 2011-02-08
chmod u+rwx/home/kimball/Downloadskimball@kimball-desktop:~$ chmod u+rwx/home/kimball/Downloads
chmod: missing operand after `u+rwx/home/kimball/Downloads'
Try `chmod --help' for more information.
kimball@kimball-desktop:~$

---

### Post by 4042966262 on 2011-02-08
and thank you for the Gdesklets tip!!

---

### Post by dino99 on 2011-02-08
how to get a deb from tar.gz:

with synaptic, install gdebi & alien

sudo alien -k packagename.tar.gz

then right click on the generated deb to install it with gdebi

nothing else :)

---

### Post by jroa on 2011-02-09
> **4042966262 said:**
> chmod u+rwx/home/kimball/Downloadskimball@kimball-desktop:~$ chmod u+rwx/home/kimball/Downloads
chmod: missing operand after `u+rwx/home/kimball/Downloads'
Try `chmod --help' for more information.
kimball@kimball-desktop:~$

I believe you need a space between rwx and /.

---

### Post by 4042966262 on 2011-02-10
sudo alien -k packagename.h3d-v-0.9.tar.gz 
File "packagename.h3d-v-0.9.tar.gz" not found.

i downloaded Gdesklets, when i click icon nothing happens?

---

### Post by oldos2er on 2011-02-10
You're meant to replace "packagename" with whatever the actual file name is.

---

### Post by 4042966262 on 2011-02-10
kimball@kimball-desktop:~$ sudo alien -kh3d-v-0.9.tar.gz
Usage: alien [options] file [...]
  file [...]                Package file or files to convert.
  -d, --to-deb              Generate a Debian deb package (default).
     Enables these options:
       --patch=<patch>      Specify patch file to use instead of automatically
                            looking for patch in /var/lib/alien.
       --nopatch	    Do not use patches.
       --anypatch           Use even old version os patches.
       -s, --single         Like --generate, but do not create .orig
                            directory.
       --fixperms           Munge/fix permissions and owners.
       --test               Test generated packages with lintian.
  -r, --to-rpm              Generate a Red Hat rpm package.
      --to-slp              Generate a Stampede slp package.
  -l, --to-lsb              Generate a LSB package.
  -t, --to-tgz              Generate a Slackware tgz package.
     Enables these options:
       --description=<desc> Specify package description.
       --version=<version>  Specify package version.
  -p, --to-pkg              Generate a Solaris pkg package.
  -i, --install             Install generated package.
  -g, --generate            Generate build tree, but do not build package.
  -c, --scripts             Include scripts in package.
  -v, --verbose             Display each command alien runs.
      --veryverbose         Be verbose, and also display output of run commands.
  -k, --keep-version        Do not change version of generated package.
      --bump=number         Increment package version by this number.
  -h, --help                Display this help message.
  -V, --version		    Display alien's version number.
um.......???

---

### Post by psycho5 on 2011-02-10
Right click the tar.gz file in your downloads folder and "extract here..." for both.

Go into terminal and enter the extracted folder for the program.

eg:

cd /home/kimball/Downloads/program1/

then just type

./configure [enter]
./make [enter]
./sudo make install [enter]

it should install it.

---

### Post by oldos2er on 2011-02-10
> **4042966262 said:**
> kimball@kimball-desktop:~$ sudo alien -kh3d-v-0.9.tar.gz

um.......???

Space bar is your friend: sudo alien -k h3d-v-0.9.tar.gz
Computers are pretty dumb in that way, they can't distinguish a typo from what you actually intended.

---

### Post by 4042966262 on 2011-02-10
kimball@kimball-desktop:~$ sudo alien -k h3d-v-0.9.tar.gz
File "h3d-v-0.9.tar.gz" not found.
kimball@kimball-desktop:~$ 

i clearly see it on desktop!!

---

### Post by 4042966262 on 2011-02-10
kimball@kimball-desktop:~$ cd /home/kimball/Desktop
kimball@kimball-desktop:~/Desktop$ 

now what?

---

### Post by jroa on 2011-02-10
While you are there, type:

```
ls
```

---

### Post by lykeion on 2011-02-11
I wonder if above posters trying to help 4042966262 actually tries out their solutions before providing them. 

Just to make things clear, problem is compiling a program called h3d.
Homepage: [http://h3d.sourceforge.net/](http://h3d.sourceforge.net/)

Solution: extract .tar.gz and compile with configure, make, make install
Results: actually you need to run autogen.sh first, but it complains about a missing gnomeConf.sh. This won't compile in newer versions of Ubuntu, see  [THIS]("http://ubuntuforums.org/showthread.php?t=1292807") post.

Solution: convert sources using alien command
Results: Converts ok and a .deb file is created. However installing the .deb file results in a h3d-v-0.9 directory in the root (!) and there is no executable to launch the program. The only executable found is a symlink (h3d) which links to itself (!). Here's how it looks in the terminal if you don't believe me:
```
root@desktop:~# ls -gGh /h3d-v-0.9
total 412K
-rw------- 1  12K 2002-02-04 06:16 ABOUT-NLS
-rw-r----- 1  195 2002-01-27 17:39 acconfig.h
-rw-r----- 1  39K 2002-02-04 06:16 aclocal.m4
-rw-r----- 1   22 2002-04-13 08:11 AUTHORS
-rwxr-x--x 1  324 2002-01-27 17:39 autogen.sh
-rw-r----- 1    0 2002-01-27 17:39 ChangeLog
-rw-r----- 1 4.5K 2002-01-27 17:48 config.cache
-rw------- 1 3.7K 2002-04-13 08:26 config.h
-rw-r----- 1 3.4K 2002-01-27 17:47 config.h.in
-rw-r----- 1 3.9K 2002-04-13 08:26 config.log
-rwx------ 1  19K 2002-04-13 08:26 config.status
-rwxr----- 1 139K 2002-02-04 06:16 configure
-rw-r----- 1  860 2002-01-27 17:39 configure.in
lrwxrwxrwx 1   27 2011-02-11 10:53 COPYING -> /usr/share/automake/COPYING
-rw-r----- 1  18K 2002-02-02 18:05 door.gif
-rw-r----- 1 5.0K 2002-02-03 06:54 door.jpg
drwxr----- 2 4.0K 2011-02-11 10:53 gh3d
-rw-r----- 1  13K 2002-02-02 18:21 grass.jpg
lrwxrwxrwx 1    4 2011-02-11 10:53 h3d -> gh3d
-rw------- 1  21K 2002-02-14 06:07 h3d.glade
lrwxrwxrwx 1   27 2011-02-11 10:53 INSTALL -> /usr/share/automake/INSTALL
lrwxrwxrwx 1   30 2011-02-11 10:53 install-sh -> /usr/share/automake/install-sh
drwx------ 2 4.0K 2011-02-11 10:53 intl
drwxr-x--x 2 4.0K 2011-02-11 10:53 macros
-rw------- 1  14K 2002-04-13 08:26 Makefile
-rw-r----- 1  595 2002-01-27 17:39 Makefile.am
-rw-r----- 1  13K 2002-02-04 06:16 Makefile.in
lrwxrwxrwx 1   27 2011-02-11 10:53 missing -> /usr/share/automake/missing
lrwxrwxrwx 1   33 2011-02-11 10:53 mkinstalldirs -> /usr/share/automake/mkinstalldirs
-rw-r----- 1    0 2002-01-27 17:39 NEWS
drwxr-x--x 2 4.0K 2011-02-11 10:53 pixmaps
drwxr-x--x 2 4.0K 2011-02-11 10:53 po
-rw-r----- 1  490 2002-04-13 08:21 README
drwx------ 2 4.0K 2011-02-11 10:53 samples
drwxr-x--x 3 4.0K 2011-02-11 10:53 src
-rw-r----- 1   10 2002-04-13 08:26 stamp-h
-rw-r----- 1   10 2002-02-04 06:16 stamp-h.in
-rw-r----- 1 6.4K 2002-02-02 17:47 window.jpg
-rw-r----- 1  12K 2002-02-02 17:35 wood.jpg

root@desktop:~# ls -gGh /h3d-v-0.9/gh3d/
total 120K
-rw-r----- 1 7.7K 2002-02-06 19:05 box.xpm
-rw-r----- 1  27K 2002-02-03 08:15 csalogo.png
-rw-r----- 1  249 2002-02-03 07:44 Delete24.gif
-rw-r----- 1  829 2002-02-03 07:51 delete.xpm
-rw-r----- 1 7.3K 2002-01-27 17:50 door.xpm
lrwxrwxrwx 1    3 2011-02-11 10:53 h3d -> h3d
-rw-r----- 1  778 2002-02-03 07:44 New24.gif
-rw-r----- 1 3.2K 2002-02-03 07:50 new.xpm
-rw-r----- 1  462 2002-02-03 07:44 Open24.gif
-rw-r----- 1 1.6K 2002-02-03 07:50 open.xpm
-rw-r----- 1  266 2002-02-03 07:45 Save24.gif
-rw-r----- 1  812 2002-02-03 07:51 save.xpm
-rw-r----- 1 5.4K 2002-02-06 19:02 tree.xpm
-rw-r----- 1  239 2002-02-03 07:44 Undo24.gif
-rw-r----- 1 8.6K 2002-01-27 17:50 wall.xpm
-rw-r----- 1  485 2002-02-03 07:44 Zoom24.gif
-rw-r----- 1  484 2002-02-03 07:44 ZoomIn24.gif
-rw-r----- 1 1.5K 2002-02-03 07:48 zoomin.xpm
-rw-r----- 1  477 2002-02-03 07:44 ZoomOut24.gif
-rw-r----- 1 1.5K 2002-02-03 07:48 zoomout.xpm
```

My solution: h3d is 8 years old, don't waste energy on this, find another program that works, preferrably something developed after Ubuntu 4.10 was launched.

---

