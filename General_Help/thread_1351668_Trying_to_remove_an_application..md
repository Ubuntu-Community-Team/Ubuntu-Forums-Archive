---
title: "Trying to remove an application."
date: 2009-12-10
forum: General Help
---

### Post by Silvernail on 2009-12-10
I am at a loss why.

This is all of 'thunderbird' that 'locate' shows to be left on my computer.
> /usr/share/man/man1/thunderbird.1.gz

I issue the command
> dave@gadabout:~$ sudo apt-get install thunderbird
[sudo] password for dave: 

and get this
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
thunderbird is already the newest version.
The following packages were automatically installed and are no longer required:
  gimp-help-en libdns35 gimp-help-common openoffice.org-help-en-gb
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dave@gadabout:~$ 


What else do I need to remove to get 'thunderbird' to install or where else should I look?

TIA
Dave

---

### Post by scouser73 on 2009-12-10
Hi Dave, follow these instructions and you'll be fine.

Download the **.tar/bz2** file from

[[COLOR="Red"]**Mozilla Messaging: Thunderbird 3**[/COLOR]]("http://en-gb.www.mozillamessaging.com/en-GB/thunderbird/")

**1** - Extract the **.tar/bz2** file

**2** - Enter **gksudo nautilus** in terminal

**3** - Go to the folder **/opt**

**4** - Copy & paste the Thunderbird file that you extracted to **/opt**

**5 -** Enter these commands into **Terminal** > **sudo -i**

*Enter your password if asked.*

> **cd /opt**
> **chown -R username filename**

[COLOR="Red"]**Obviously the username refers to you, and the filename to the file**[/COLOR]

**6** - Go to **System > Preferences > Main Menu**

**7** - In Main Menu, click on **New Item**

**8** - In the **Name** field enter **Mozilla Thunderbird Mail/News**

**9** - In the **Command** field enter **/opt/thunderbird/thunderbird**

**10** - In the **Comment** field enter **Mozilla Thunderbird Mail/News**

[[IMG]http://img121.imageshack.us/img121/7329/screenshot2c.png[/IMG]](http://img121.imageshack.us/img121/7329/screenshot2c.png/)

---

### Post by Silvernail on 2009-12-13
I want to mark this solved but no button again. I never can find it.

I want to thank 'scouser73' for his help. I worked as expected.

Thanks
Dave

---

### Post by fancypiper on 2009-12-13
> **Silvernail said:**
> I want to mark this solved but no button again. I never can find it.Look under "Quick Links"

[Mark Your Thread as [SOLVED] After Getting Your Answer](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

---

