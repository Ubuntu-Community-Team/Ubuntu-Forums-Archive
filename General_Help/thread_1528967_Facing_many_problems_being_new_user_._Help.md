---
title: "Facing many problems being new user . Help"
date: 2010-07-11
forum: General Help
---

### Post by asifnaz on 2010-07-11
Startted using ubuntu 7 days ago
1) I hear no start up sound doeas it mean my sound card is not installed .I can see that speaker icon on to right by the way .
   
  2)cant go online but its not ubuntu's fault i am using dial up modem . I will hopefully get DSL soon (ubuntu does not install my modem so i go online with xp)
   
  3)I want to download from getdeb dot net but it has only install button not download button (i cant install as i am online using xp ) 
   
  4)I installed VLC.deb right click on a song click open with vlc player but nothing happend . I did same on my Friend's pc with same result .
   
  If i installed an application .deb how can i view/open/use it given it was installed successfully .
   
  give me some links where i could download (using xp) .deb media players as default music player plays nothing and asks for add ins and i cant go online with ubuntu.
  Please help me as I have passed my ubuntu CD to many of other friends and all are facing same problem.
  regards

---

### Post by mike555 on 2010-07-11
for dialup You should download Gnome-ppp and it's dependencies ... [http://packages.ubuntu.com/sl/lucid/gnome-ppp](http://packages.ubuntu.com/sl/lucid/gnome-ppp)    .... you will also need a compatible modem like this one ... [http://www.newegg.com/Product/Product.aspx?Item=N82E16825134002](http://www.newegg.com/Product/Product.aspx?Item=N82E16825134002)

---

### Post by marshag63 on 2010-07-11
asifnaz, I agree with the serial modem - guaranteed to get you online with dial-up until you can get DSL.  I believe GnomePPP is installed by default with any version of ubuntu.

Before you try installing a bunch of additional stuff, you need to let you system update itself and make sure you have all the repositories enabled you will need (like medibuntu for multimedia codecs and such) before you try adding additional stuff.  Do your friends all have dial-up as well?

Have a look at this:  [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html) if you want to download it yourself 
or here if you want to read it online:  [http://books.google.com/books?id=kHLlJzI6L20C&printsec=frontcover#v=onepage&q&f=false](http://books.google.com/books?id=kHLlJzI6L20C&printsec=frontcover#v=onepage&q&f=false)

See chapter Six regarding software management - I'm guessig that VLC is not working because it has dependencies that have not yet been installed.  Its best to let the package manager install VLC, so it grabs its dependencies, codecs, etc.

RE Sound:  Double click your sound icon on the panel bar and play with the settings - sometimes you just need to change to master or PCM.

BTW, you didn't say what version of Ubuntu you are running - it helps to know that to answer questions.

You can install Ubuntu on a flash drive with this in linux and windows:  [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Hope this helps some :)

MarshaG.

---

### Post by asifnaz on 2010-07-11
> **marshag63 said:**
> asifnaz, I agree with the serial modem - guaranteed to get you online with dial-up until you can get DSL.  I believe GnomePPP is installed by default with any version of ubuntu.

Before you try installing a bunch of additional stuff, you need to let you system update itself and make sure you have all the repositories enabled you will need (like medibuntu for multimedia codecs and such) before you try adding additional stuff.  Do your friends all have dial-up as well?

Have a look at this:  [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html) if you want to download it yourself 
or here if you want to read it online:  [http://books.google.com/books?id=kHLlJzI6L20C&printsec=frontcover#v=onepage&q&f=false](http://books.google.com/books?id=kHLlJzI6L20C&printsec=frontcover#v=onepage&q&f=false)

See chapter Six regarding software management - I'm guessig that VLC is not working because it has dependencies that have not yet been installed.  Its best to let the package manager install VLC, so it grabs its dependencies, codecs, etc.

RE Sound:  Double click your sound icon on the panel bar and play with the settings - sometimes you just need to change to master or PCM.

BTW, you didn't say what version of Ubuntu you are running - it helps to know that to answer questions.

You can install Ubuntu on a flash drive with this in linux and windows:  [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Hope this helps some :)

MarshaG.
I am using latest one that is 10.40 .I am using cdma2000 wireless phone modem which is very difficult to install by a new user . Yes my friends are using same dial up modem .
Hopefully we are getting DSL soon .
Just help me download(using xp) a meadia player with .deb format which playes and plays about all formats.

---

### Post by marshag63 on 2010-07-12
Update:
Could use a little more info about your cdma2000 wireless phone modem - manufacturer, is it recognized as usb storage or something else.  Does windows XP use the cdma2000? 


Found this link for updating offline:  [http://superuser.com/questions/145049/offline-updates-for-freshly-installed-ubuntu-10-04](http://superuser.com/questions/145049/offline-updates-for-freshly-installed-ubuntu-10-04).  I've never done this - sorry I can't be of more help.

-->**Official How to"**<--
See "Installing Packackages Without Internet Connection"
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware) (via USB key)

"Note: If you don't have access to a PC with GNU/Linux or emulating/virtualizing GNU/Linux (Cygwin, VMware, VirtualBox, Qemu, etc), **[COLOR="Blue"]just open the script with a text editor and enter all the URLs you see in your browser to download the corresponding packages[/COLOR]**."

If you can get access to a laptop with wifi, you can take it where there is free wifi, boot it via USB flash install of Ubuntu to grab the packages, then install and then let your friends do the same.

I'd like to hear how this turns out :)

MarshaG.

DISREGARD BELOW:
This may help with the Gnome-PPP setup.  [http://ubuntuforums.org/showthread.php?t=763122](http://ubuntuforums.org/showthread.php?t=763122)  You will likely be in offline mode when firefox starts - just go to "File" and uncheck "work offline"

You'll have to update your computer to get the codecs that work with VLC.  None of the programs you are going to install are going to work without updating your computer and installing the codecs.

[https://help.ubuntu.com/10.04/newtoubuntu/C/music-video.html](https://help.ubuntu.com/10.04/newtoubuntu/C/music-video.html)

Again, I hope this helps.

MarshaG.

---

