---
title: "How do I create a wallpaper package?"
date: 2012-07-27
forum: General Help
---

### Post by linuxuser12345 on 2012-07-27
How do I create a wallpaper package as a .deb file that will make the wallpapers automatically appear on the Change Desktop Background's 'wallpaper' list?

---

### Post by Frogs Hair on 2012-07-27
I think there are wallpaper changer applications available , but have never attempted to write one. I only see Wally in the software center so far. Check here: [http://www.liberiangeek.net/2012/03/wallpaper-changer-wallch-updated-to-version-3-0install-it-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/03/wallpaper-changer-wallch-updated-to-version-3-0install-it-in-ubuntu-12-04-precise-pangolin/)

---

### Post by linuxuser12345 on 2012-07-27
> **Frogs Hair said:**
> I think there are wallpaper changer applications available , but have never attempted to write one. I only see Wally in the software center so far.
Great app, but no thanks :(
I want to create a wallpaper pack to mass-distribute on the Ubuntu Software Center, so it will have to be one that auto-configures itself in such a way that the computer "sees" them on the first 'Wallpapers' list on the stock wallpaper changer program in Ubuntu.

---

### Post by angry_johnnie on 2012-07-27
you'll need a directory called whatever you want to call your package.  inside that directory, another directory called DEBIAN, and another called usr.  inside usr, another directory called share.  inside share, another called backgrounds.  inside backgrounds, your wallpaper.

inside the DEBIAN directory, 2 files:  a text file called "control" and a "postinst" script.

this is an example of a control file:

```
Package: package name
Priority: optional
Section: misc
Maintainer: your name <your@email>
Architecture: all
Version: version number
Depends: whatever it depends on.
Description: a brief description of what your package includes or does.


```

notice the blank line at the end.  it's important.

the postinst script will just tell the system what to do with the included files.  here's an example:

```
#!/bin/bash

chmod a+r /usr/share/backgrounds/your-awesome-wallpaper

exit 0
```


once you have this, you'll need to change ownership of the directory.  suppose you have it on /home/you/wallpaper

you would:

```
sudo chown -R root.root /home/you/wallpaper
```

once ownership has been given to root, you just build the package.

```
sudo dpkg -b /home/you/wallpaer wallpaper.deb
```

and that's it.

it sounds and looks more complicated than it really is. :)

---

### Post by linuxuser12345 on 2012-07-27
Thanks :)
I'll probably need some more help, but if and when I do, I'll hit you up! Thanks :)

---

### Post by linuxuser12345 on 2012-07-27
What would I put for "depends"? "Section"?

---

### Post by angry_johnnie on 2012-07-27
well, if it's just a set of wallpapers, i guess you could leave it blank :)  it's just images, so it doesn't really need anything other tan a display.

---

### Post by linuxuser12345 on 2012-07-27
If I have multiple pictures, how would I design the Postinst file? The postinst file is confusing me :(

---

### Post by angry_johnnie on 2012-07-27
well, the postinst script just makes sure that everything is set up with the right permissions once installed.  you want to make sure the user has read permissions on all the images.

so, for example, if your wallpapers are called image1, image2, image3, and so on, you would have to do as follows:

```
#!/bin/bash

chmod a+r /usr/share/backgrounds/image1
chmod a+r /usr/share/backgrounds/image2
chmod a+r /usr/share/backgrounds/image3

exit 0
```

this way you'll ensure that all users have read permissions on the images.  otherwise they won't be able to see them, even if they're on the correct directory.

---

### Post by linuxuser12345 on 2012-07-27
Okay, now if there is a space in the file name, do I put a "_" (underscore) or just keep a space?

---

### Post by angry_johnnie on 2012-07-27
for the sake of simplicity i'd suggest you just rename it and put an underscore instead of a space. otherwise, it'll just complicate coding the rest of it.

---

### Post by linuxuser12345 on 2012-07-27
Thank you so much Angry_Johnnie! :)
My build is complete, but I have one more thing I need to figure out how to do... How do I compile it into an executable .deb format?

---

### Post by angry_johnnie on 2012-07-27
if you run 

```
sudo dpkg -b /your/directory package.deb
```

it should create an installable debian package

---

### Post by angry_johnnie on 2012-07-27
yep.  i just tested it.  i just build a debian package out of some old scripts and ran sudo dpkg -b.  i was able to install it afterwards with sudo dpkg -i mypackage.deb.

---

### Post by linuxuser12345 on 2012-07-27
> **angry_johnnie said:**
> if you run 

```
sudo dpkg -b /your/directory package.deb
```

it should create an installable debian package

What if it is located in my home directory?

---

### Post by angry_johnnie on 2012-07-27
just replace "/your/directory" with your actual directory.  if your directory is /home/yourname/package, you would run 

```
sudo dpkg -b /home/yourname/package package.deb
```

replace /home/yourname/package with the actual directory, and replace package.deb with the name you want to give it.  no spaces.  makes things easier. :)

---

### Post by linuxuser12345 on 2012-07-27
Okay... I'm stuck :(

```
jeb@AMD-Athlon-II-X3:~$ sudo dpkg -b ./mac-osx-wallpapers.deb
[sudo] password for jeb: 
dpkg-deb: error: failed to open package info file `./mac-osx-wallpapers.deb/DEBIAN/control' for reading: No such file or directory
jeb@AMD-Athlon-II-X3:~$ 


```

[IMG]http://ubuntuone.com/6Qc9w7L6AvyyR2OvDV0Mgo[/IMG]

---

### Post by angry_johnnie on 2012-07-27
if you actually have everything, all the files, in your home directory, you'll need to create a directory structure that the debian package system will understand.

remember that these directories should be like this:

/packagename/

/packagename/DEBIAN/
/packagename/DEBIAN/control
/packagename/DEBIAN/postinst

/packagename/usr/
/packagename/usr/share/
/packagename/usr/share/backgrounds/
/packagename/usr/share/backgrounds/image1
/packagename/usr/share/backgrounds/image2

---

### Post by angry_johnnie on 2012-07-27
[QUOTE=linuxuser12345;12134276]Okay... I'm stuck :(

```
jeb@AMD-Athlon-II-X3:~$ sudo dpkg -b ./mac-osx-wallpapers.deb
[sudo] password for jeb: 
dpkg-deb: error: failed to open package info file `./mac-osx-wallpapers.deb/DEBIAN/control' for reading: No such file or directory
jeb@AMD-Athlon-II-X3:~$ 


```


that was the dot.

instead of ./mac-osx....

you should cd into the directory where mac-osx-wallpapers is

then run ```
sudo dpkg -b mac-osx-wallpapers/ mac-osx-wallpapers.deb

```

also, notice you tell it where the files are, and then what the package name will be

---

### Post by linuxuser12345 on 2012-07-27
I did create a directory, but it doesn't seem to find the control file that is obviously there :(

---

### Post by linuxuser12345 on 2012-07-27
Aw I spent a lot of time coding using gedit... I hope I can get this to work without having to rewrite everything completely in a terminal :/

---

### Post by angry_johnnie on 2012-07-27
notice the dot you're placing at the beginning.

that's actually telling it to go somewhere else.

if the folder is called mac-osx-wallpapers and is located in your home directory, then it should be like this:

```
cd
sudo chown -R root.root mac-osx-wallpapers/
sudo dpkg -b mac-osx-wallpapers/ mac-osx-wallpapers.deb
```

also, make sure the DEBIAN folder is called DEBIAN with all capital letters, and make sure to leave a blank line at the end of the control file.

---

### Post by linuxuser12345 on 2012-07-27
> **angry_johnnie said:**
> 

you should cd into the directory where mac-osx-wallpapers is



How do I cd into the directory?

---

### Post by linuxuser12345 on 2012-07-27
Sorry, I'm still getting used to the terminal :)
Thanks for helping me

---

### Post by angry_johnnie on 2012-07-27
hey no worries.  we all learned little by little.  post 22 above should tell you exactly what to do, if your files are called what i think they're called :)

---

### Post by linuxuser12345 on 2012-07-27
[IMG]http://i49.tinypic.com/20rmjwg.png[/IMG]

---

### Post by linuxuser12345 on 2012-07-27
```
jeb@AMD-Athlon-II-X3:~$ cd mac-osx-wallpapers
bash: cd: mac-osx-wallpapers: No such file or directory
jeb@AMD-Athlon-II-X3:~$ cd ./mac-osx.wallpapers
bash: cd: ./mac-osx.wallpapers: No such file or directory
jeb@AMD-Athlon-II-X3:~$ cd
jeb@AMD-Athlon-II-X3:~$ sudo chown -R root.root mac-osx-wallpapers/
[sudo] password for jeb: 
chown: cannot access `mac-osx-wallpapers/': No such file or directory
jeb@AMD-Athlon-II-X3:~$ 

```

---

### Post by angry_johnnie on 2012-07-27
:) well, in order to tell you what to do i'll need to know a few more details.

what is the name of the folder where you have the wallpapers?

where is this folder located?

---

### Post by linuxuser12345 on 2012-07-27
I gave the folder to Root and I am still getting the same error message that there is no control file :(

---

### Post by linuxuser12345 on 2012-07-27
The folder's name is "Mac-OSX-Wallpapers" and is in my Home folder.

---

### Post by linuxuser12345 on 2012-07-27
I'm not trying to install a deb file, I'm trying to *make* a deb file to mass-distribute.

---

### Post by angry_johnnie on 2012-07-27
good.

now, remember linux is case-sensitive, and things have to be typed in exactly.

in this case, you would run (one line at a time)

```
cd
sudo chmod -R root.root Mac-OSX-Wallpapers/
sudo dpkg -b Mac-OSX-Wallpapers/ Mac-OSX-Wallpapers.deb
```

if you were doing this before with all lower case letters, or with a different mix of lower case and upper case, it wouldn't work.  capital leters have to be typed in as capital letters, and lower case as lower case, otherwise it will go looking for a directory that doesn't exist.

the control file should be in the following directory:

/home/you/Mac-OSX-Wallpapers/DEBIAN/control

as long as it's there, the terminal should find it.  just be sure to be careful with capital letters.

---

### Post by linuxuser12345 on 2012-07-27
I did use caps... :/
It says root.root is an invalid mode.

---

### Post by linuxuser12345 on 2012-07-27
... and now this:

```
jeb@AMD-Athlon-II-X3:~$ sudo dpkg -B Mac-OSX-Wallpapers/ Mac-OSX-Wallpapers.deb
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
jeb@AMD-Athlon-II-X3:~$ 

```

---

### Post by angry_johnnie on 2012-07-27
:o the reason i mention it is because on previous posts, and on your screenshots, it shows only lower case letters, and a mixture of dots and dashes.

if it makes things easier, go ahead and create a compressed folder, like a zip file, or a rar file, with the whole folder, images, control file, and the rest.  upload it, and i'll be glad to make a debian package for you. :) got nothing else to do right now :)

---

### Post by angry_johnnie on 2012-07-27
> **linuxuser12345 said:**
> ... and now this:

```
jeb@AMD-Athlon-II-X3:~$ sudo dpkg -B Mac-OSX-Wallpapers/ Mac-OSX-Wallpapers.deb


```

that should be dpkg **-b**

-B is not a valid option.  remember it's case sensitive

---

### Post by linuxuser12345 on 2012-07-27
> **angry_johnnie said:**
> that should be dpkg **-b**

-B is not a valid option.  remember it's case sensitive


Okay, now it looks like I'm getting somewhere ;)
But...
```
jeb@AMD-Athlon-II-X3:~$ sudo dpkg -b Mac-OSX-Wallpapers/ Mac-OSX-Wallpapers.deb
[sudo] password for jeb: 
dpkg-deb: error: maintainer script `postinst' has bad permissions 664 (must be >=0555 and <=0775)
jeb@AMD-Athlon-II-X3:~$ 


```

---

### Post by angry_johnnie on 2012-07-27
hmmm
 that should be something like this (one line at a time):

```
cd
cd /Mac-OSX-Wallpapers/DEBIAN/
sudo chmod a+rwx postinst
cd
sudo chown -R root.root /Mac-OSX-Wallpapers/
sudo dpkg -b Mac-OSX-Wallpapers.deb
```

---

### Post by linuxuser12345 on 2012-07-27
```
jeb@AMD-Athlon-II-X3:~$ cd
jeb@AMD-Athlon-II-X3:~$ cd /Mac-OSX-Wallpapers/DEBIAN/
bash: cd: /Mac-OSX-Wallpapers/DEBIAN/: No such file or directory

```

---

### Post by angry_johnnie on 2012-07-27
right!  my bad :p

i had to get rid of the "**/**" before the directory name.  try it like this.  it should work.

```
cd
cd Mac-OSX-Wallpapers/DEBIAN/
sudo chmod a+rwx postinst
cd
sudo chown -R root.root Mac-OSX-Wallpapers/
sudo dpkg -b Mac-OSX-Wallpapers/ Mac-OSX-Wallpapers.deb
```

---

### Post by linuxuser12345 on 2012-07-27
The whole folder is owned by root, too.
```
jeb@AMD-Athlon-II-X3:~$ sudo dpkg -b Mac-OSX-Wallpapers/ Mac-OSX-Wallpapers.deb
dpkg-deb: error: maintainer script `postinst' has bad permissions 777 (must be >=0555 and <=0775)
jeb@AMD-Athlon-II-X3:~$ 

```

Here are the permissions for the postinst file:
[IMG]http://i45.tinypic.com/2eaqpgx.png[/IMG]

---

### Post by angry_johnnie on 2012-07-27
yes, and that's the way it should be.  if it doesn't let you make any changes to it, i'd suggest you change permissions again.

judging from your screenshot, i gather your username is jeb.

so, it would be

```
cd
sudo chown -R jeb.jeb Mac-OSX-Wallpapers/
cd Mac-OSX-Wallpapers/DEBIAN/
sudo chmod 775 postinst
cd
sudo chown -R root.root Mac-OSX-Wallpapers/
sudo dpkg -b Mac-OSX-Wallpapers/ Mac-OSX-Wallpapers.deb
```

this is only difficult the first time :).  once you get the hang of it, you'll see it's really quite easy.


we'll try chmod 775 this time.

---

### Post by linuxuser12345 on 2012-07-27
just uploaded a pic for the permissions...

---

### Post by linuxuser12345 on 2012-07-27
Almost thereeeeeee!!!!!!!!!!! But.....
:(
```
jeb@AMD-Athlon-II-X3:~$ cd
jeb@AMD-Athlon-II-X3:~$ sudo chown -R jeb.jeb Mac-OSX-Wallpapers/
[sudo] password for jeb: 
jeb@AMD-Athlon-II-X3:~$ cd Mac-OSX-Wallpapers/DEBIAN/
jeb@AMD-Athlon-II-X3:~/Mac-OSX-Wallpapers/DEBIAN$ sudo chmod a+rwx postinst
jeb@AMD-Athlon-II-X3:~/Mac-OSX-Wallpapers/DEBIAN$ cd
jeb@AMD-Athlon-II-X3:~$ sudo chown -R root.root Mac-OSX-Wallpapers/
jeb@AMD-Athlon-II-X3:~$ sudo dpkg -b Mac-OSX-Wallpapers/ Mac-OSX-Wallpapers.deb
dpkg-deb: error: maintainer script `postinst' has bad permissions 777 (must be >=0555 and <=0775)
jeb@AMD-Athlon-II-X3:~$ 


```

How do I make the permissions of the postinst file >=0555 and <=0775?

---

### Post by angry_johnnie on 2012-07-27
> **linuxuser12345 said:**
> Almost thereeeeeee!!!!!!!!!!! But.....
:(


we're gettin there :)

try it again.  i just edited the code, so it's chmod 775 instead of chmod a+rwx.

---

### Post by linuxuser12345 on 2012-07-27
Maybe it has something to do with the fact that I made every single item in the folder owned by root?

---

### Post by angry_johnnie on 2012-07-27
> **linuxuser12345 said:**
> Maybe it has something to do with the fact that I made every single item in the folder owned by root?

it's alright.  chown -R jeb.jeb is recursive, and it will make every single file in the directory owned by you.  try the code with chmod 775.

---

### Post by linuxuser12345 on 2012-07-27
It's building! It's built! THANK YOU :)
I gave you special notice in the ownership files :)

---

### Post by angry_johnnie on 2012-07-27
yay!

glad to hear it's working.  it's one of those things that just gets easier every time you do it.

---

### Post by linuxuser12345 on 2012-07-27
I'm uploading it to my Google Drive now. I'll send you a copy when it uploads.
Feel free to edit and distribute the package contents as you like or need.

---

### Post by angry_johnnie on 2012-07-27
hey thanks.  if you post a link i'll be your first downloader :)

---

### Post by linuxuser12345 on 2012-07-27
Here it is! 
[https://docs.google.com/open?id=0B6ihhZN41GENby1tY0lZcVQtTjg](https://docs.google.com/open?id=0B6ihhZN41GENby1tY0lZcVQtTjg)

Please, if you find any errors, feel free to fix them and contact me asap :)

---

### Post by linuxuser12345 on 2012-07-27
ERRRRRR! Not... installing! :(
I need your help again, sorry lol

---

### Post by linuxuser12345 on 2012-07-27
I keep getting this error message:
```
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 254072 files and directories currently installed.)
Unpacking mac-osx-wallpapers (from .../jeb/Mac-OSX-Wallpapers.deb) ...
dpkg: error processing /home/jeb/Mac-OSX-Wallpapers.deb (--install):
 trying to overwrite '/usr/share/backgrounds/Frog.jpg', which is also in package ubuntu-wallpapers-karmic 0.34.1
dpkg-deb (subprocess): data: internal gzip write error: Broken pipe
dpkg-deb (subprocess): failed in write on buffer copy for failed to write to pipe in copy: Broken pipe
dpkg-deb: error: subprocess <decompress> returned error exit status 2

```


What do I do?

---

### Post by angry_johnnie on 2012-07-27
hey there.

what happens is that there's already a wallpaper called Frog, in another package.  i had to go and rename it to frog, with a lower case f.  also, in the postinst script, some o the file names with spaces have underscores, but in /usr/share/backgrounds, the same files have the spaces, not underscores, so i went and renamed the files to match the underscores in the postinst script.  i'm currently uploading the modified debian package and files.  as soon as the  upload completes i'll give you the link

---

### Post by angry_johnnie on 2012-07-27
and, actually, since these are pretty large files, and it'll take quite a long time to upload, it may really be a lot quicker if you go and do the same.


in a terminal, type:

```
cd
sudo chown -R jeb.jeb Mac-OSX-Wallpapers/ && sudo chmod a+rw Mac-OSX-Wallpapers/DEBIAN/postinst

```
go to your wallpapers/DEBIAN folder and edit the postinst script.  replace chmod a+r /usr/share/backgrounds/Frog.jpg with /usr/share/backgrounds/frog.jpg.  

in your Mac-OSX-Wallpapers/usr/share/backgrounds folder, change Frog.jpg to frog.jpg.  also, for all the wallpapers whose filenames have spaces, replace the spaces with underscores.  some filenames have dashes instead of spaces.  these are ok.  only change the ones with spaces.  after that is done, go back to the terminal and do

```
cd
sudo chown -R root.root Mac-OSX-Wallpapers/
cd Mac-OSX-Wallpapers/
sudo chmod -R 775 DEBIAN/
cd
sudo dpkg -b Mac-OSX-Wallpapers/ Mac-OSX-Wallpapers.deb
```

it should work after that.  that was exactly what i did, and it worked, with no errors.  i did get the same error you got the first time, but not after this.

try it.  i'm sure it will be quicker than waiting for my upload :P

---

### Post by oldos2er on 2012-07-27
> **linuxuser12345 said:**
> I'm not trying to install a deb file, I'm trying to *make* a deb file to mass-distribute.

See [http://developer.ubuntu.com/packaging/html/](http://developer.ubuntu.com/packaging/html/)

---

### Post by linuxuser12345 on 2012-07-28
Can you please upload it to Google Drive? I found out that Google Drive doesn't tend to freeze up as much as Ubuntu One does, and I will look at the changes you made and learn from them, anyways :)

---

### Post by angry_johnnie on 2012-07-28
will do.  i have bad weather and lousy speed, so i guess i'll just leave it uploading all night.  i tried to upload it to dropbox a couple of times and it died.  i tried ubuntu one and it also failed.  i'll upload it to google docs then.  will take a long time :)  hopefully it'll be there by tomorrow morning :)

---

### Post by linuxuser12345 on 2012-07-28
> **angry_johnnie said:**
> will do.  i have bad weather and lousy speed, so i guess i'll just leave it uploading all night.  i tried to upload it to dropbox a couple of times and it died.  i tried ubuntu one and it also failed.  i'll upload it to google docs then.  will take a long time :)  hopefully it'll be there by tomorrow morning :)

THANK YOU EVER SO MUCH :)
Please be sure to add yourself to the authors list.

---

### Post by angry_johnnie on 2012-07-28
there you go.  this morning i woke up with good weather, and it uploaded in just a few minutes, thank goodnes :)

here's the two links.  one is the debian package.  the other one is a .tar.gz with the files.  double checked everything and made sure it installed.  seems to be working :P

[https://docs.google.com/open?id=0B6H329ep1BznMkYyTWlxTTFFTkE](https://docs.google.com/open?id=0B6H329ep1BznMkYyTWlxTTFFTkE)
[https://docs.google.com/open?id=0B6H329ep1BznemFvWGRMUFhwR2s](https://docs.google.com/open?id=0B6H329ep1BznemFvWGRMUFhwR2s)

---

### Post by linuxuser12345 on 2012-07-28
> **angry_johnnie said:**
> there you go.  this morning i woke up with good weather, and it uploaded in just a few minutes, thank goodnes :)

here's the two links.  one is the debian package.  the other one is a .tar.gz with the files.  double checked everything and made sure it installed.  seems to be working :P

[https://docs.google.com/open?id=0B6H329ep1BznMkYyTWlxTTFFTkE](https://docs.google.com/open?id=0B6H329ep1BznMkYyTWlxTTFFTkE)
[https://docs.google.com/open?id=0B6H329ep1BznemFvWGRMUFhwR2s](https://docs.google.com/open?id=0B6H329ep1BznemFvWGRMUFhwR2s)

```
Not Found

Error 404
```

You need to publish the files on your Google Drive to the General Public. By default, Google Drive only lets you share to yourself. Please edit the permissions, thanks :)
I'm already getting responses back from the Ubuntu App Developer team :) Excited!!!!

---

### Post by angry_johnnie on 2012-07-29
yikes! sorry :P

just changed that.

here's the new links:

[https://docs.google.com/open?id=0B6H329ep1BznMkYyTWlxTTFFTkE](https://docs.google.com/open?id=0B6H329ep1BznMkYyTWlxTTFFTkE)
[https://docs.google.com/open?id=0B6H329ep1BznemFvWGRMUFhwR2s](https://docs.google.com/open?id=0B6H329ep1BznemFvWGRMUFhwR2s)

i changed to "anyne with the linke can view"  hope that's enough :)

---

### Post by linuxuser12345 on 2012-07-29
Thanks, man! The Ubuntu App Development Team has been contacting me looking for a new .deb. Thank you thank you thank you :)

---

### Post by linuxuser12345 on 2012-07-29
I'm trying to make a PPA, and I need help with that, too! lol
```
jeb@AMD-Athlon-II-X3:~$ dput ppa:jebeld17/macosx-wallpapers <Mac-OSX-Wallpapers.deb>
bash: syntax error near unexpected token `newline'
jeb@AMD-Athlon-II-X3:~$ 


```
```
jeb@AMD-Athlon-II-X3:~$ dput ppa:jebeld17/macosx-wallpapers <source.changes> 
bash: syntax error near unexpected token `newline'
jeb@AMD-Athlon-II-X3:~$ sudo dput ppa:jebeld17/macosx-wallpapers <source.changes> 
bash: syntax error near unexpected token `newline'
jeb@AMD-Athlon-II-X3:~$ 


```

I have absolutely no idea whatsoever on how to upload to my PPA... What am I doing wrong?

---

