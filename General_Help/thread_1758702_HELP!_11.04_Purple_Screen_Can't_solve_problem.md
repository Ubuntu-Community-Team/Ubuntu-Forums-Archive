---
title: "HELP! 11.04 Purple Screen Can't solve problem"
date: 2011-05-14
forum: General Help
---

### Post by eastcoastandrew on 2011-05-14
When I first update to 11.04 I had the issues with just having the desktop and no menus and nothing to click, eventually got Ubunto Classic to work, and it was just fine.

However today, I switch out of Classic and couldn't get it to switch back. So I was looking for a more permanent fix. 

I followed this websites advice: [http://www.ubuntugeek.com/how-to-fix-common-gnome-3-issues-on-ubuntu-11-04-natty.html](http://www.ubuntugeek.com/how-to-fix-common-gnome-3-issues-on-ubuntu-11-04-natty.html)

After I ran that, I ended up with a computer that turns on and all I have is a purple screen that shows the ubuntu logo and has the circles under in and what not. I can acess the terminal by pressing control + alt + F1, but other than that I can't do anything.

I'm looking for any possible solution.

Or just a way to somehow say all my files and do a clean install.

---

### Post by Hedgehog1 on 2011-05-15
Those instructions wiped out Unity. 

If you don't already have one, please make a LiveCD/LiveUSB of Natty/11.04.

If you boot from the 11.04 LiveCD/LiveUSB, you may have an upgrade path offered in the 'install 11.04'.

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

**If this is not offered**, if you have your data in a separate '/home' partition you can reinstall 11.04 over your 10.10 '/' partition and be sure to not format the '/home' partition:

First, define your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Then define your '/home' partition:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE OR A RE-INSTALL, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

***The Hedge***

:KS

p.s. To learn how to move your '/home' into it's own partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

---

