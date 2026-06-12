---
title: "zlib causing problem with gdm"
date: 2010-07-15
forum: General Help
---

### Post by LittleGyko on 2010-07-15
hi,
 
i use ubuntu 10.04 on a dell studio 14 laptop. everything had been working fine for about a month. today, when i switched on my machine, only the purple background of ubuntu is appearing, i.e. no menu where i can type in my password. 
 
i saw a few posts dated a few months back with people having similar problems, but none of them were marked solved, and so i am creating a new post. can someone please help.
 
the only thing i had tried earlier was to download and try and install some gtk+ packages.
 
i tried ctrl + alt+F1 and startx, but that gave a fatal error. 
 
thanks

I even tried :
 
sudo dpkg-reconfigure gdm and then startx brought me to the same purple screen, again without the login menu. 
 
sudo /etc/init.d/gdm restart
sudo /etc/init.d/gdm stop and sudo /etc/init.d/gdm start 
 
but none of the above helped.

further, some time back i saw the following post
 	Quote:
 	 	 		 			 				 					Originally Posted by **Saser** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9298409#post9298409") 				
 				*Now my Ubuntu works perfectly. It seems that I get this problem when I compile and install a few packages from their sources, like libpng and zlib.*
 			 		 	 	 
and it turns out that i too had installed zlib today. i got the impression that it was required for GTK.

is there some way to uninstall zlib or uninstall the packages i installed today??

thanks

 		 []("http://ubuntuforums.org/editpost.php?do=editpost&p=9590137")

---

### Post by sbergman on 2011-07-28
Hi.

About a year after the initial post was made, and I've just encountered the exact same problem with zlib-1.2.5

Uninstalling zlib worked for me, but now I need to find another way of using the package that needed zlib in the first place.

In my case, I had initially installed zlib from source and after encountering the problem:
1) I did a ctrl+alt+f1 and logged in text mode 
2) cd to the location of the source
3) typed ```
sudo make uninstall
```
4) reboot the pc

Hope this helps anyone else who has this problem.

---

### Post by hadaxu on 2011-09-09
Exactly the same problem for me today Ubuntu 10.04 LTS, zlib-1.2.5 compiled from source code. Uninstall zlib and restart solved. Now what to do to have zlib!!!!!

---

