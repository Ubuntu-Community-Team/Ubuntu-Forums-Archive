---
title: "Installed Ubuntu 11.04 and have proplenms"
date: 2011-06-27
forum: General Help
---

### Post by linuxguy86 on 2011-06-27
Hello I just installed Ubuntu 11.04 and after I log in, the Desktop wont come up just the wallpaper. So I switch it to Ubuntu Classic (No Effects) and it works there but I want unity. It Doestn work on Ubuntu or Ubuntu Classic. Just the No effects work. Again i am able to log in but after that it wont go into the desktop just shows the wallpaper thats it.

---

### Post by dFlyer on 2011-06-27
Open a terminal and run this command:

/usr/lib/nux/unity_support_test -p

All answers have to be yes to run unity. Chances are it's the video card.

---

### Post by linuxguy86 on 2011-06-27
all of then are yes

---

### Post by nzjethro on 2011-06-27
Have you installed your video card drivers yet?

---

### Post by Alwimo on 2011-06-28
If you do have the proprietary video drivers installed (perhaps you chose to install proprietary stuff in the installation), I suggest uninstalling them through the Additional Drivers application and seeing if that helps. 
 
I have some issues that come having additional drivers, if I choose to install the proprietary stuff during installation or additional drivers through the Additional Drivers application. The driver that it says I am required to have to run Unity makes it so that Unity doesn't work at all for me. Without it, it works perfectly. :)

---

### Post by linuxguy86 on 2011-06-29
the only thing that came up on additonal drivers are my wirlesss thats it. Nothing else came ep. Know i have another problem, my wireless was working fine before I installed the updates, but after I installed the updates know my wireless doestn work.

---

### Post by moonport on 2011-06-29
> **linuxguy86 said:**
> the only thing that came up on additonal drivers are my wirlesss thats it. Nothing else came ep. Know i have another problem, my wireless was working fine before I installed the updates, but after I installed the updates know my wireless doestn work.

Did you try connect via ethernet cable? 
If everything's fine, next question: Are you using a built-in wifi or a  a plug-in wifi adapter?
You can check this typing the command lspci in a terminal window.

---

### Post by linuxguy86 on 2011-06-30
its on my laptop so built in, i have no video drivers that i can install throught the addtional software

---

### Post by georgelab on 2011-06-30
Try this on terminal: dmesg | grep "card"

What info did u got?

---

