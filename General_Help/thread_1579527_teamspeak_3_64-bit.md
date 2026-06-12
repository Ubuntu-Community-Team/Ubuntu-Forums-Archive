---
title: "teamspeak 3 64-bit"
date: 2010-09-22
forum: General Help
---

### Post by sirtigger on 2010-09-22
Hey whats up! I was just wondering how to install Teamspeak 3 in Ubuntu 9.10 64bit.  I download the file to my home folder and also when I tried to extract it, it said this message.  Thank you Guys.

(gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.)

---

### Post by supermorph on 2011-03-25
heres a link, its got how i set up my teamspeak (server 2 & 3 clients)

[http://ubuntuforums.org/showthread.php?p=10593783#post10593783](http://ubuntuforums.org/showthread.php?p=10593783#post10593783)

also

when u goto teamspeak.com
download the 64bit linux client as usual


save it to your user folder for now


when downloaded
open (insert preffered console tool here)
and navigate to your home folder 

e.g cd /home/you

when there (keep it open),
you will need to open your home folder using e.g nautilus or dolphin etc

rename the file you downloaded to ts3c.run

close the file manager

return to that console

type:

chmod +c ts3c.run && ./ts3c.run

it will ask you to read thier licence agreement.
press return (to open it up) , once opened press Q
it will ask do you agree, press Y (and enter if it stays idle after such)

it will then extract the contents to its folder

as i have a custom layout, you can check to see if its usable to yourself
using the link above,  but to do such you need to use the root user to make folders in the root of your filesystem, 

you will also need to set permissions for your user to have at least read and execute permissions (as a minimum, i mean :-p )


kind regards,
supermorph

---

