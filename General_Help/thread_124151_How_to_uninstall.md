---
title: "How to uninstall???"
date: 2006-01-31
forum: General Help
---

### Post by alexal on 2006-01-31
I have installed the official ati drivers in ubuntu but not from the package manager.
So how can i uninstall it? Basicaly i will buy nvidia.
You can tell me a method to use for all the software that i want to uninstall which is not installed from the package manager.

---

### Post by Seanuntu on 2006-01-31
I was going to ask the same question.  Just a few minutes ago I installed SeaMonkey.  I used the automated installer program and installed it to the default location (/usr/loca/seamonkey).  I checked it out for a few minutes and quickly decided it wasn't for me.  The broswer looked just like Netscape (from 1997).  I really don't understand why Firefox wouldn't be bundled with Seamonkey.  Why develop a different browser aside from Firefox.  Maybe I am missing something.  But I digress....  

To unstall it, I just deleted the /usr/local/seamonkey folder.  Is this the proper way to do it?  Did I leave remnants of the program/settings on my 'puter?  In other words, would deleting this folder be the equivalent of deleting a folder from the /program files/ folder in windows?

-Seanuntu

---

### Post by RAOF on 2006-01-31
[QUOTE=Seanuntu]I was going to ask the same question.  Just a few minutes ago I installed SeaMonkey.  I used the automated installer program and installed it to the default location (/usr/loca/seamonkey).  I checked it out for a few minutes and quickly decided it wasn't for me.  The broswer looked just like Netscape (from 1997).  I really don't understand why Firefox wouldn't be bundled with Seamonkey.  Why develop a different browser aside from Firefox.  Maybe I am missing something.  But I digress....  

To unstall it, I just deleted the /usr/local/seamonkey folder.  Is this the proper way to do it?  Did I leave remnants of the program/settings on my 'puter?  In other words, would deleting this folder be the equivalent of deleting a folder from the /program files/ folder in windows?

-Seanuntu[/QUOTE]
Yes, there can be stuff left lying around.   Particularly libraries in /usr/local/lib, and settings in /etc & hidden directories in your home folder.

Sadly, there's no generic way to properly uninstall stuff that isn't registered with the package manager.  Your best hope is to run the installer again, and see if there's an "uninstall" option.

As for the ATI binary driver - the nvidia installer has an --uninstall option to remove it.  Maybe the ATI one does too.

---

### Post by designflaw on 2006-02-01
> 
Quote:
Originally Posted by Seanuntu
I was going to ask the same question. Just a few minutes ago I installed SeaMonkey. I used the automated installer program and installed it to the default location (/usr/loca/seamonkey). I checked it out for a few minutes and quickly decided it wasn't for me. The broswer looked just like Netscape (from 1997). I really don't understand why Firefox wouldn't be bundled with Seamonkey. Why develop a different browser aside from Firefox. Maybe I am missing something. But I digress....

To unstall it, I just deleted the /usr/local/seamonkey folder. Is this the proper way to do it? Did I leave remnants of the program/settings on my 'puter? In other words, would deleting this folder be the equivalent of deleting a folder from the /program files/ folder in windows?

-Seanuntu
Yes, there can be stuff left lying around. Particularly libraries in /usr/local/lib, and settings in /etc & hidden directories in your home folder.

Sadly, there's no generic way to properly uninstall stuff that isn't registered with the package manager. Your best hope is to run the installer again, and see if there's an "uninstall" option.

As for the ATI binary driver - the nvidia installer has an --uninstall option to remove it. Maybe the ATI one does too.

I just installed Java 2 SDK 1.4.2 using the installation notes on suns website ([http://java.sun.com/j2se/1.4.2/install-linux.html](http://java.sun.com/j2se/1.4.2/install-linux.html)) However, I installed it in the wrond folder (ended up installing in the user folder I was logged in as). So should I just delete the folder and then install it back again? Will the binary files that were creating installing java sdk in the first place get over written and everything will be the same. Which folder should I be installing it in ? (I know it dont matter but whats the best folder).

---

### Post by RAOF on 2006-02-01
[QUOTE=designflaw]I just installed Java 2 SDK 1.4.2 using the installation notes on suns website ([http://java.sun.com/j2se/1.4.2/install-linux.html](http://java.sun.com/j2se/1.4.2/install-linux.html)) However, I installed it in the wrond folder (ended up installing in the user folder I was logged in as). So should I just delete the folder and then install it back again? Will the binary files that were creating installing java sdk in the first place get over written and everything will be the same. Which folder should I be installing it in ? (I know it dont matter but whats the best folder).[/QUOTE]
I don't think that Java installs anything into weird places.  Just deleting the directory it installed to is (probably) sufficient.

Many people suggest that under the /opt directory is a good spot to install things manually.

---

