---
title: "Installing Tweetdeck results in broken dependency - Lucid- 64bit"
date: 2010-05-07
forum: General Help
---

### Post by sayantandas on 2010-05-07
Hi,

I have installed adobe air following the tutorial to install adobe air on 64 bit systems from adobe website. after that i installed Tweetdeck. The software runs without a glitch but the update manager throws up an error saying some software have unmet dependencies and needs to be removed. when i go ahead with the removal, Tweetdeck is removed. 
Any ideas how to fix it?

Thanks,
Sayantan

---

### Post by sayantandas on 2010-05-09
bump! 
anyone?

---

### Post by kbsali on 2010-05-12
same problem here (with adobe air 2beta),
could not find a solution yet.

---

### Post by soleblaze on 2010-05-24
This is because if you install the deb it shows it under i386.  However, some programs like tweekdeck are looking for the adobeair 64bit package.  The solution is either to force the deb to install as a 64bit, or install adobe air using the .bin file instead of a deb.

This is supposed to be fixed in the first non-beta release of adobe air 2.

---

### Post by sayantandas on 2010-05-25
> **soleblaze said:**
> This is because if you install the deb it shows it under i386.  However, some programs like tweekdeck are looking for the adobeair 64bit package.  The solution is either to force the deb to install as a 64bit, or install adobe air using the .bin file instead of a deb.

This is supposed to be fixed in the first non-beta release of adobe air 2.

thanks so much. your info solved my problem. 
i can use tweetdeck now :guitar::guitar:

---

### Post by dckirba on 2010-07-05
Hi guys,

I have the same problem. I force installed the .deb for Adobe Air first. Then I tried the .bin but it said the same software was already installed. 

Running tweetdeck results in a synaptic error. 

I want to uninstall adobe air and reinstall with just the .bin but since it doesn't show up in the package manager I'm not sure how to do this. 

Help would be greatly appreciated.

Also, once tweetdeck is up and running, is it possible to replace gwibber in the notification area (envelope icon)?

Thanks,
David K

---

### Post by dckirba on 2010-07-05
> **dckirba said:**
> Hi guys,

I want to uninstall adobe air and reinstall with just the .bin but since it doesn't show up in the package manager I'm not sure how to do this. 



Hey guys, please ignore that. Apparently a simple ```
sudo dpkg -P adobeair
``` is all that is needed.

I'd still like to know if I can get Tweetdeck to replace gwibber in all the menus though :)

Thanks and have a good day,
David K

---

