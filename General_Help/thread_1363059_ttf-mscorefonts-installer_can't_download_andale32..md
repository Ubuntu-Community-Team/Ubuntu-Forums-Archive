---
title: "ttf-mscorefonts-installer can't download andale32.exe CancelOk     1. Ubuntu    2. “"
date: 2009-12-23
forum: General Help
---

### Post by Randymanme on 2009-12-23
[B] ttf-mscorefonts-installer can't download andale32.exe       

[/B]


                       
[LIST=1]
[*]     [       Ubuntu            ]("https://launchpad.net/ubuntu")
[*]     [       “msttcorefonts” package            ]("https://launchpad.net/ubuntu/+source/msttcorefonts")
[*]     [       Bugs            ]("https://bugs.launchpad.net/ubuntu/+source/msttcorefonts")
[*]     [              Bug #495492     ]("https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/495492")
[/LIST]
              


Is there a workaround for this?  So far, I've been unable to install *anything* from the software store.

  	 	 	 	 	 	  Setting up ttf-mscorefonts-installer (3.0) ...  
 

 These fonts were provided by Microsoft "in the interest of cross-  
 platform compatibility".  This is no longer the case, but they are  
 still available from third parties.  
 

 You are free to download these fonts and use them for your own use,  
 but you may not redistribute them in modified form, including changes  
 to the file name or packaging format.  
 

 Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.  
 Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.  
 Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.  
 Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.  
 Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.  
 Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.  
 Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.  
 Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.  
 Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.  
 Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.  
 Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.  
 Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.  
 sha256sum: andale32.exe: No such file or directory  
 andale32.exe: FAILED open or read  
 sha256sum: WARNING: 1 of 1 listed file could not be read  
 Checksum mismatch for andale32.exe, aborting!  
 dpkg: error processing ttf-mscorefonts-installer (--configure):  
  subprocess installed post-installation script returned error exit status 1  
 E: Sub-process /usr/bin/dpkg returned an error code (1)  
 randall@randall:~$ 



Furthermore, am I to understand that the functionability of my Ubuntu is being compromised by something that originated at microsoft???  What's it doing here in the first place?

---

### Post by taurus on 2009-12-23
Looks to me like you need to configure the _proxy_ so you could get out into the net.

---

### Post by Randymanme on 2009-12-23
Due to what I assume to be some idiosyncrasy of my DVD ROM, no Ubuntu or Fedora live media will install..  PCLinuxOS and openSUSE would, though.  Finally, I discovered that I could use a Jaunty alternative installation CD to install the base system and grub, and manually install enough packages from the CD to allow me to update and upgrade.  One thing I noticed is that the network icon at the upper right hand of the screen has a red and white X icon on it. When I click on it, it says "Wired networks (etho 0) device not managed, and wired networks (etho 1) device disconnected. "

Do you mean ". . . get out onto the net . . .," as in internet, like now (from my computer to Ubuntu Forums)?  I don't know how to configure a proxy (I'll google and search, though).  I've never had to do it before.  Is there some package that normally makes that unnecessary that I can install (presuming that [Bug #495492]("https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/495492")  will permit that)?

---

### Post by Randymanme on 2009-12-24
Found the solution here: [[IMG]http://ubuntuforums.org/images/misc/navbits_start.gif[/IMG]]("http://ubuntuforums.org/showthread.php?t=1238323&highlight=configure+proxy&page=3#") 				  				[Ubuntu Forums]("http://ubuntuforums.org/index.php")  	> [The Ubuntu Forum Community]("http://ubuntuforums.org/forumdisplay.php?f=130")   	> [Main Support Categories]("http://ubuntuforums.org/forumdisplay.php?f=327")   	> [Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=334")   			 			 				[[IMG]http://ubuntuforums.org/images/misc/navbits_finallink_ltr.gif[/IMG]]("http://ubuntuforums.org/showthread.php?t=1238323&highlight=configure+proxy&page=3") ** 	[COLOR=#980101][B][ubuntu]**[/COLOR] ttf-mscorefonts-installer errors

which directed to: [/B]
**[Howto: Fix ttf-mscorefonts-installer problems in Ubuntu 9.10 Karmic Koala]("http://friendlytechninja.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/"):popcorn:**

---

