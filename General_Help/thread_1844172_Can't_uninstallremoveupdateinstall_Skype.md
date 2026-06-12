---
title: "Can't uninstall/remove/update/install Skype"
date: 2011-09-14
forum: General Help
---

### Post by mattzilla on 2011-09-14
While trying to update to the new beta version of Skype, I received the following error message:
dpkg: error processing /var/cache/apt/archives/skype_2.2.0.35-0natty1_amd64.deb (--unpack):
 skype:  2.2.0.35-0natty1 (Multi-Arch: no) is not co-installable with skype:i386  2.1.0.81-1 (Multi-Arch: no) which is currently installed
&#65279;
Now I had a previously installed version of skype, that I downloaded from the official skype website.
I  tried all of the outlets to uninstall, including sudo apt-get remove,  synaptic package manager and ubuntu software center and none of them  even recognized that I had skype installed.
 
I then did the  dumb thing and simply removed every file associated with skype on my  computer, but (of course) that didn't work either. Now I can neither run  the skype my computer thinks I have installed, nor can I install (or  re-install) any other version of skype.
 
The only thing I  find strange in this instance is that it says I have the i386 version  installed on my 64-bit system, which I see neither how or why it would  do that, could that be related?
 
Any and all help is apprecaited!
-matt

---

### Post by esperanto3000 on 2011-10-24
I had the same issue. It was most probably caused by installing the i386 package of a former Skype version on an AMD64 system via a dpkg -i --force-all. 

You need to get rid of the skype:i386 package. The command 

   dpkg -r skype:i386 

did the job for me. 

Hope that helps.

---

