---
title: "Can't install downloaded DEB files"
date: 2011-08-02
forum: General Help
---

### Post by mark2741 on 2011-08-02
Just installed Ubuntu 11.04 32-bit on an older Dell D610 laptop. Everything was running a little slow but all in all running fine except one thing - I downloaded the Chrome deb file and also the deb file from Moneydance. When I double-click on either of these deb files, it opens up the Ubuntu Software Center and shows an 'Install' button for the app. I click Install and then enter my root password, then nothing happens. A short while later the Install button turns from grayed out to clickable again. So I click it again, and it says that the deb file is not packaged correctly.

I've tried it with multiple deb files now and get the same thing. Installing directly through the Ubuntu Software Center works fine, but unortunately Chrome and Moneydance aren't in there (I prefer Chrome to Chromium). What could be causing this?

Also - due to the slowness of the Ubuntu install I did a clean install to Xubuntu and I like that much better and it is running perfectly except for this issue of not being able to install any 3rd-party downloaded apps.

---

### Post by Kira_Belka on 2011-08-02
easiest way to install anything that you wanna) is 
1. [http://ubuntu-tweak.com/app/](http://ubuntu-tweak.com/app/)
2. found needed programm ppa
3. add ppa for this programm
4. open synaptic and click update
5. found your program in software list and install it without any problems(usually)

small notice.. don't use daily ppa or test builds..

About Xubuntu..so different Desktop Environment Gnome is very powerful and beauty ..but sometimes it needs rather big amount of system resources..certainly LXDE or Afterstep demand less )).. also you can try ubuntu-trinity with kde3.5
it's powerful and fast..kde4 is tooooo slow) on weak PC.

---

### Post by garvinrick4 on 2011-08-03
Put .deb file on Desktop and;
cd Desktop
ls
sudo dpkg -i (name of .deb file copy and paste sometimes for long ones)
##It is now installed.

Here is .ppa's for Ubuntu
[http://www.ubuntuupdates.org/ppas](http://www.ubuntuupdates.org/ppas)
After install ppa from that site:
One at a time below:
```
sudo apt-get update
sudo apt-get install (name of package you wanted in ppa)
```

---

### Post by Kira_Belka on 2011-08-03
2 garvinrick4 ..you forgot about gdebi utility.. it's my lovely terminal and gui utility for packages)

---

### Post by Kira_Belka on 2011-08-03
> **garvinrick4 said:**
> Put .deb file on Desktop and;
cd Desktop
ls
sudo dpkg -i (name of .deb file copy and paste sometimes for long ones)
##It is now installed.

Here is .ppa's for Ubuntu
[http://www.ubuntuupdates.org/ppas](http://www.ubuntuupdates.org/ppas)
After install ppa from that site:
One at a time below:
```
sudo apt-get update
sudo apt-get install (name of package you wanted in ppa)
```

why "Desktop"? ))) I think why not "home" for example?))))
and cd Desktop )) if start point is "home" then it sounds logical)

---

### Post by Kira_Belka on 2011-08-03
and Ubuntu-tweak ..is no bad utility for begginers..

---

### Post by garvinrick4 on 2011-08-03
> why "Desktop"? ))) I think why not "home" for example?))))
and cd Desktop )) if start point is "home" then it sounds logical) 	

Relax Kira_Belka slow down take a breath no more coffee and Twinkee's you are making
me hyper just reading your post's. Everything is OK, we will all use /home from now on.
No more cd Desktop I promise. Have a good day Kira_Belka and take the joke do not go
balistic on me please. We are all here because we enjoy Ubuntu and to learn and help when we can, right.

---

### Post by dog-soldier on 2011-08-03
in 11.04 the software center is set to open deb files. what i did was get gdebi from the software center . then when you try to install a deb file you just right click on the file and choose open with gdebi.

---

### Post by mark2741 on 2011-08-03
Thanks! I used GDebi and it works perfectly. 

I'm not a complete newbie so I remember GDebi from before. Not sure why they made it so that in 11.04 the Software Center opens up deb files unless it actually worked : (. I used Ubuntu as my sole OS from versions 6.10 thru 8.04 (I  wound up getting a new PC that had all kinds of trouble with Ubuntu so I switched back to Windows).

Other than my work laptop I'm now without a PC so I grabbed this old laptop that had been sitting in my closet, previously was for my kids (they now have my desktop). I'm thinking about just buying a new inexpensive laptop for running Ubuntu on but this will do for now.

---

### Post by Kira_Belka on 2011-08-03
> **garvinrick4 said:**
> Relax Kira_Belka slow down take a breath no more coffee and Twinkee's you are making
me hyper just reading your post's. Everything is OK, we will all use /home from now on.
No more cd Desktop I promise. Have a good day Kira_Belka and take the joke do not go
balistic on me please. We are all here because we enjoy Ubuntu and to learn and help when we can, right.
yep)) mmmm..  :popcorn: I simply was angry on lsi 1068 based adapter)))))))))) all 's ok) don't mind

---

### Post by Kira_Belka on 2011-08-03
gdebi is really cool.. it's so)

---

### Post by garvinrick4 on 2011-08-04
> **dog-soldier said:**
> in 11.04 the software center is set to open deb files. what i did was get gdebi from the software center . then when you try to install a deb file you just right click on the file and choose open with gdebi.
Ubuntu is making it so easy to install these packages now, you got gdeb to do it and software center with a double click on .deb package and done. gdeb is efficient one day terminal will be used once in a blue moon. Sure good for new users, Ubuntu seems to be accomplishing there goal.

---

### Post by mark2741 on 2011-08-04
I agree it is getting better all the time, but let's be honest - I shouldn't have had to install GDebi just to install a downloaded application. I love the idea of any deb file that gets double-clicked defaults to opening up the Software Center...but only if it actually works and installs it as it is intended. But it doesn't. Very annoying.

---

