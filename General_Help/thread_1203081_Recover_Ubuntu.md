---
title: "Recover Ubuntu"
date: 2009-07-02
forum: General Help
---

### Post by krishnik on 2009-07-02
Hi, 
 
I was upgrading from ubuntu 7.10 to 8.04LTS i was able to download all the packages and as installation was about to finish the power went off. After this when i start ubuntu its showing the login screen (user &pwd) but after this nothing is happening.
 
Is there any way to recover ubuntu ? Do i have to download all the upgrade packages again. Please help me.

---

### Post by Boondoklife on 2009-07-02
I would think a reinstall of the packages if possible, are you seeing any error messages or any info in the logs?

---

### Post by synapsys on 2009-07-02
Not good... this is another reason to do fresh installs.... I hate to say it but your quickest and easiest solution would be to re-install. You should probably download the latest version (9.04) and install that fresh. After backing up all your important files of course. You could try running dist-upgrade.

---

### Post by philcamlin on 2009-07-02
theres no gui?

its dropping to shell then 

reinstalling i think is an option but forst boot into live cd and backup all data

---

### Post by sailthesea on 2009-07-02
Do you have any sort of command line after login?
You could get going with xstart
If not hit esc or click options at the login screen and see where that gets you
An aborted upgrade won't be too hard to recover
Hope this helps;)

---

### Post by scrooge_74 on 2009-07-02
It is dumping you into a terminal? No GDM then? 

check if you have internet, log in and type ifconfig if you get detail that you have an ip do a 

sudo apt-get update
sudo apt-get upgrade

if it finish installing you are ok if not try sudo apt-get install ubuntu

---

### Post by krishnik on 2009-07-02
Thank you very much for quick replies. I will reinstall ubuntu, but  my problem is that i have only ubuntu 7.10 CD. 
Ok I will dowload the latest version......
 
Thank you vey much again  for the replies.....

---

