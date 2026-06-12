---
title: "Unable to install or remove software"
date: 2010-03-25
forum: General Help
---

### Post by tlillies on 2010-03-25
Hello, i have had ubuntu installed for a few months now and have been loving it. Yesterday i wanted to get JDK installed for a found a forum that said how to install it on ubuntu. The installation was not a success(i am not sure why because i am not skilled when it comes to the command line and i didn't understand the error). Later, i tried to install a different application just through the ubuntu software center and it said it was waiting for a different software manager to finish. I didn't understand what was still running because i had all other applications closed that i know of. Once i restarted the problem was the same. Then i found a bug where people had the same problem with the software manager and they entered this and fixed it:

sudo dpkg --configure -a

Now whenever i try to apt-get anything i get:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I am not sure what to do now. I am a ubuntu noob and so i need help! Thanks!

---

### Post by UCSBGauchosRock on 2010-03-25
Your problem may be the fact that whatever program you are using to install/remove software is being blocked by another running program meant to install/remove software. 

Example: You are trying to install/delete something with Synaptic Package Manager, but Update Manager is Working or you are trying to install/remove something with Ubuntu Software Center.

Let me know if you have any questions about the information at the top :)

---

### Post by tlillies on 2010-03-25
Ahh thanks for the help. I figured it out. Something that i had tried to download before had downloaded but for some reason not all the way and i sudo apt-get it so it was running in the terminal. I removed it and now everything is working fine and dany. Sorry for the trouble.

---

