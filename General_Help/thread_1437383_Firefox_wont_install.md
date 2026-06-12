---
title: "Firefox wont install"
date: 2010-03-23
forum: General Help
---

### Post by KaiDog on 2010-03-23
I'm running Ubuntu 9.10 and had Firefox 3.5.8 installed on my computer. I repeatedly tried to upgrade to 3.6 but each time nothing happened. So I tried uninstalling 3.5.8 and installing 3.6. So far, no luck. I've tried installing it using the software center and using the command line and the update manager. So far nothing. I'm at a total loss at what to do!

---

### Post by KaiDog on 2010-03-23
Update:

It seems to be installed now. But it doesn't show up in my program files. I can only launch it from the command line. Is there a way to get the icon in the menu tray again?

---

### Post by Colo2 on 2010-03-23
When you said you had no luck installing, what do you mean? there was an error?

---

### Post by abbaazaabba on 2010-03-23
You can edit the grub menu by right clicking on the applications launcher and selecting edit menus.

You can add a launcher from point to any sub-menu you wish.

---

### Post by KaiDog on 2010-03-23
When I tried upgrading to 3.6 from 3.5.8 using either the command line or the update manager, it would download and go through the installation process but nothing would happen.

So I uninstalled 3.5.8 and as it turns out I installed 3.6.3 by accident, when all I'm trying to do is upgrade to 3.6.

---

### Post by mechro on 2010-03-23
I don't think 3.6 is yet officially in the Karmic repositories so you would have experienced difficulties installing it via The Software Centre or apt-get. Because it's not in the Ubuntu repositories 3.6 won't necessarily be set up with the Ubuntu menu items and launchers.

You'll have to create your own menu items and/or launchers.

---

### Post by KaiDog on 2010-03-23
That explains it. I'll try and do a manual install then.

---

### Post by 2hot6ft2 on 2010-03-23
> **KaiDog said:**
> That explains it. I'll try and do a manual install then.
If it's installed and will start from the terminal all you have to do is create the launcher in the menu.

Right click on the ubuntu logo in the top left corner, select Edit Menus.
On the left select Internet, On the right click on New Item

Use the pic below to put the info in. Click close and close. You can also click on the icon where you see the firefox icon on mine and find the firefox icon.

---

### Post by mechro on 2010-03-23
You could try the Lucid package which includes the 3.6 version...

[http://packages.ubuntu.com/lucid/web/ubufox](http://packages.ubuntu.com/lucid/web/ubufox)

---

### Post by KaiDog on 2010-03-23
Thanks everyone for your help. But in my fumbling around, I accidentally installed Namoroka and I can't seem to get it off my computer. I haven't been able to find a strait forward instruction for removing it that works. In the about section it says it's Firefox 3.6.3. If I can, I'll like to downgrade back to firefox 3.5.8 and figure it out from there.

---

### Post by mkvnmtr on 2010-03-23
The easiest way I have found to install the latest Firefox which is now 3.6.2 is to use the Ubuntuzilla site. Follow the instrunctions and paste a couple of commands in the terminal and you will have a repository that will keep upgraded.
For removing the stuff you tried to install use the synaptic package manager. Use the searlch feature to find the app and then remove it.

---

### Post by lovinglinux on 2010-03-24
> **KaiDog said:**
> Thanks everyone for your help. But in my fumbling around, I accidentally installed Namoroka and I can't seem to get it off my computer. I haven't been able to find a strait forward instruction for removing it that works. In the about section it says it's Firefox 3.6.3. If I can, I'll like to downgrade back to firefox 3.5.8 and figure it out from there.

Disable the ubuntu-mozilla-daily ppa from the Software Sources and re-install Firefox. It should revert to the default version.

See the [COLOR="Sienna"]**Installing Other Versions**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by KaiDog on 2010-03-25
I managed to uninstall Namoroka, install 3.6.2 and fix my flash problem. Consider the problem solved!

Thanks everyone for your help!

---

