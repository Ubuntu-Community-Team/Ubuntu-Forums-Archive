---
title: "I installed gnome 3 on ubuntu 11.04 and i cant boot"
date: 2011-09-04
forum: General Help
---

### Post by Yusuke_DS on 2011-09-04
Hi! I tried to install the Gnome 3 on Ubuntu 11.04 just after the installation.. By following this 4 steps on terminal:

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get upgrade

sudo apt-get install gnome-shell




After restarting my computer, i got exactly this screen:

[http://imageshack.us/photo/my-images/215/20110813012250327.jpg/](http://imageshack.us/photo/my-images/215/20110813012250327.jpg/)

Can anyone help me? Why that happened?.. thanks!

---

### Post by neoideo on 2011-09-04
me too, but only when booting kernel 2.6.38-11.
can you boot on older kernel (like 2.6.38-8 )?

---

### Post by phendrome on 2011-09-21
I happen to have the exact same problem. Not sure what to do. I can include that I happen to have Windows 7 installed as well as the Developer Preview of Windows 8 as well. Ubuntu did work before I hadn't installed Gnome 3 though.

[quote=neoideo]         me too, but only when booting kernel 2.6.38-11.
can you boot on older kernel (like 2.6.38-8 )?[/quote]
How do you boot up using the older kernel?

---

### Post by raja.genupula on 2011-09-21
hey Guys
i am seeing many threads with issues of gnome 3 , so i think its better to wait for a while up to Gnome 3 becomes fine . if you wanna downgrade to gnome 2 then i can help you on this issue .

[http://lkubuntu.wordpress.com/2011/06/23/downgrading-from-gnome-3-to-gnome-2/](http://lkubuntu.wordpress.com/2011/06/23/downgrading-from-gnome-3-to-gnome-2/)

---

### Post by phendrome on 2011-09-21
> **raja.genupula said:**
> hey Guys
i am seeing many threads with issues of gnome 3 , so i think its better to wait for a while up to Gnome 3 becomes fine . if you wanna downgrade to gnome 2 then i can help you on this issue .

[http://lkubuntu.wordpress.com/2011/06/23/downgrading-from-gnome-3-to-gnome-2/](http://lkubuntu.wordpress.com/2011/06/23/downgrading-from-gnome-3-to-gnome-2/)
Didn't seem to work buddy. The screen is still completely black as I try to boot up.

I booted up in recovery mode to access the terminal and I executed all these commands and then I decided to reboot with no success. 

Any other ideas?

---

### Post by SidebySide on 2011-11-15
Oh, My God, I've fallen in the same well!
11.04(Unity) => Gnome 3
=> a permanent black screen before coming desktop
Isn't there any solution, really?

---

### Post by no9to5blogger on 2011-11-15
I tried to install the new ubuntu 11.10 on an old laptop averatec 3200 google it anyway it has 59-60 gigs on the HD about 500mb or less amd anthlon processor. it is not many manufactors that build pc's/laptops for linux.

---

### Post by SidebySide on 2011-11-18
> **no9to5blogger said:**
> I tried to install the new ubuntu 11.10 on an old laptop averatec 3200 google it anyway it has 59-60 gigs on the HD about 500mb or less amd anthlon processor. it is not many manufactors that build pc's/laptops for linux.
@no9to5blogger
Why spam? :x this topic is about gnome3.

________
I can't login to Desktop, yet. :(
What should I do?

---

### Post by Silent Warrior on 2011-11-18
Hm... Maybe X.org got a bad update along the way, or the graphics driver's kernel module failed to build? Can you boot into rescue mode?

Even so: if you want Gnome 3, follow raja.genupula's advice.

---

### Post by nixblog on 2011-11-18
I installed 11.10 as a test on my laptop and also installed the latest nvidia drivers too - no problem, all was fine. I decided to try gnome-shell and on the reboot it spat the dummy.

The reason?, my nvidia 7300 GPU (with nvidia driver) doesn't like gnome-shell (or vice versa) and there are a few nvidia cards that are doing similar when you have the nvidia drivers installed too. It seemed ok on the stock nouveau driver but, as soon as you install nvidia's own drivers, kaput!

---

