---
title: "ubuntu 11.04 hangs installing updates ?"
date: 2011-06-15
forum: General Help
---

### Post by culham on 2011-06-15
Hi guys Im new to ubuntu I last used it 2 years ago and did not like it one bit but a friend told me about 11.04 so thought id give it a go and I absoluetly love it. its far superior to windows 7 imo. now my only problem so far is when installing updates it seems to hang on applying updates ive only waited 20 mins so far but im sure there should be some indication of progress, Any help much appreciated

---

### Post by plucky on 2011-06-15
> **culham said:**
> Hi guys Im new to ubuntu I last used it 2 years ago and did not like it one bit but a friend told me about 11.04 so thought id give it a go and I absoluetly love it. its far superior to windows 7 imo. now my only problem so far is when installing updates it seems to hang on applying updates ive only waited 20 mins so far but im sure there should be some indication of progress, Any help much appreciated

My update progress bar is also broken,but the updates do install.

You could try from a terminal ```
sudo apt-get update
sudo apt-get upgrade
``` and see what happens.

Good Luck

---

### Post by inameiname on 2011-06-15
From time to time some repos lag. As plucky said, try the terminal and see just if that is the issue. Basically if it freezes loading a particular repository, you'd know which one. There is nothing you can really do if that's the case. Just be glad its not your computer. :P
If you have extra repos accessible, I've noticed GetDeb and sometimes certain PPAs from Launchpad lag here and there.

---

### Post by culham on 2011-06-15
cheers guys it worked after about 40 mins just said system was up to date so atleast I know for future reference, as for the running commands in the terminal im not that advanced yet I only installed it yesterday :D

---

### Post by inameiname on 2011-06-15
Hehe. Yeah, best not to overdo yourself after just one day. If you want, here is a very simple script that will automatically update, install, upgrade, and cleanup whatever. Basically just double click it and it'll automatically open a terminal window for you and you can see what is making it take so long, and when its done, it will close. Simple. Works the same way as the update manager does that you normal use, just the terminal way. Plus I added some options to clean up at the end. No biggie.

---

### Post by culham on 2011-06-15
cheers iname thats real decent of you so what do I just copy and paste the script into terminal and hit enter ??

---

### Post by inameiname on 2011-06-15
No. Just double click the script. It'll probably ask you to run, so choose that. It'll automatically open up a terminal window and you can see what is happening. That's all. Well, it'll ask for your password of course,just like the normal update-manager, and then prompt you for when its ready to install stuff, but that's it.

---

