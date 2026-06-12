---
title: "Shell Scripts for Beginners"
date: 2012-02-12
forum: General Help
---

### Post by teh5abiking on 2012-02-12
i've seen so many threads on here, asking "how do i do x" or "where can i get y" or "what's z?" as a service to the ubuntu community, i've decided to create several scripts that in theory, should help out newbies get settled into ubuntu and hopefully get somewhat familiar with the command line. 

this thread is dedicated to creating scripts that help out not only noobs, but experienced users as well. all shell script requests are welcome, and contributions are greatly appreciated. 

anyway, let's get on with it! 

[B]WHAT IS A SHELL SCRIPT?
 - [/B]A set of commands in a text file that once executed, runs all the commands that have been specified in that file.

[B]HOW TO USE THE SHELL SCRIPTS PROVIDED: 
[/B]- First, download the script.
- Next, open up your file manager
- Go to your Downloads folder, and right-click on the script.
- Go to "Permissions" and click on "Allow executing file as program"
- Click on "Close" on the bottom right. 
- Open up a Terminal (CTRL+Alt+T) and execute the following:
```
cd ~/Downloads && ./<scriptname>
```
Replace <scriptname> with the actual name of the script. 
(If you downloaded the file to a different folder, replace ~/Downloads with the actual location of where the file is located.)

So long as you follow these steps, you should have no problem. 

_**SCRIPT LIST:**_

restricted-extras-installer: refreshes repositories and installs the ubuntu-restricted-extras package and the libdvdcss package on your system. these packages contain software that includes flash, java, audio codecs, video codecs, dvd playback, and much more. ubuntu cannot ship with this software by default due to legal encumbrances. 

script link: [http://www.mediafire.com/?0zy8f1r789zatpm](http://www.mediafire.com/?0zy8f1r789zatpm)

___

ubuntu updater: refreshes repositories and uses 'apt-get dist-upgrade' to fully upgrade the entire system. please note that if a new stable version of ubuntu is released, 'apt-get dist-upgrade' WILL upgrade your system to that version. if you don't like that, edit the script and replace 'sudo apt-get dist-upgrade' with 'sudo apt-get upgrade' instead. 

script link: [http://www.mediafire.com/?9uefdv2vo1a89oi](http://www.mediafire.com/?9uefdv2vo1a89oi)

___

acroread-installer: this script adds the ubuntu 10.04 lucid lynx partner repository to your software sources, refreshes your repositories, and installs the acroread package along with all of its required dependencies. acroread installs the adobe acrobat reader package, which provides the program itself and the plugin for firefox that allows you to view pdf files in the browser without having to download them.

script link: [http://www.mediafire.com/?xp0ulul2sour0jc](http://www.mediafire.com/?xp0ulul2sour0jc)  

___

[B]MORE TO COME SOON :D LEAVE SCRIPT REQUESTS DOWN BELOW IN THE COMMENTS :D
[/B]

---

### Post by teh5abiking on 2012-02-12
Reserved for Future Use

---

### Post by teh5abiking on 2012-02-12
Also Reserved

---

