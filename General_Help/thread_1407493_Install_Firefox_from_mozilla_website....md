---
title: "Install Firefox from mozilla website..."
date: 2010-02-15
forum: General Help
---

### Post by gwu777 on 2010-02-15
Now I am sure it is a silly question and I already have some answer to it but it isn always clear in my mind so I thought I will ask:

I have been ready on how to install firefox 3.6 on my 9.1 ubuntu. About adding various repository and the a sudo apt get and all that. I can do it that way, and I am sure it will work.

What stop me to just download the .deb package from mozilla for the version I want and install it? Will it be less integrated to the system, will it not be compatible with my 64bit ubuntu? I just find it so much simpler to download a package from the web and double click on it than going through terminal, yet no-one seems to propose this option. I would like to know why.

---

### Post by mkvnmtr on 2010-02-15
I do not believe Mozilla offers a 64 bit version of Firefox. Thus I believe you would be better to use the repositories.

---

### Post by Enigmapond on 2010-02-15
You won't get a .deb from mozilla..only tar.bz which you just extract and throw all the files into /opt and create a symlink to /opt/firefox/firefox. This will work fine however, you will not get upgrades from the repository and the computer will not show that it's installed....as far as integration...it will work fine but ubuntu will think you don't have FF....you will be better off getting it from the repo in the long run...

---

### Post by crichard on 2010-02-15
Read [this]("http://surferzworld.com/?p=193") to install firefox from mozilla.com. However if you want to install 64 bit firefox, you have to try [dailyPPA.]("https://edge.launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa") 
For more info, follow this thread [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by gwu777 on 2010-02-15
> **Enigmapond said:**
> You won't get a .deb from mozilla..only tar.bz which you just extract and throw all the files into /opt and create a symlink to /opt/firefox/firefox. This will work fine however, you will not get upgrades from the repository and the computer will not show that it's installed....as far as integration...it will work fine but ubuntu will think you don't have FF....you will be better off getting it from the repo in the long run...

Thank you for your answers, there are very good points, I am going to install it from the repository, how ubuntu have a 64 bit version if mozilla didn't release it... Firefox doesn't update itself as it would in windows, it has to be done via synaptic to be automatic?

For further info, if I install chrome - sorry but I like it :) from the deb package from google, it will not be updated via synaptic, is this correct?

I hope my questions are making sens, it is just to understand the process better.

---

### Post by Enigmapond on 2010-02-15
You are correct on both counts. If you haven't installed it through the repos then it will not update. You can install chrome by adding the PPA 

[B]deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic  main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main[/B]

Then getting the key..

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E5E17B5
```update and then it will be in synaptic.

Cheers!

---

### Post by scouser73 on 2010-02-15
> **gwu777 said:**
> Now I am sure it is a silly question and I already have some answer to it but it isn always clear in my mind so I thought I will ask:

I have been ready on how to install firefox 3.6 on my 9.1 ubuntu. About adding various repository and the a sudo apt get and all that. I can do it that way, and I am sure it will work.

What stop me to just download the .deb package from mozilla for the version I want and install it? Will it be less integrated to the system, will it not be compatible with my 64bit ubuntu? I just find it so much simpler to download a package from the web and double click on it than going through terminal, yet no-one seems to propose this option. I would like to know why.

I always mention installing the .tar.gz files, I find it to be easy (clearly not as easy installing via .deb but easy enough).

[[COLOR="Red"]**Download Firefox 3.6**[/COLOR]]("http://www.mozilla.com/en-US/firefox/all.html")

**1** - Right click & Extract the Firefox tar.bz2

**2** - Enter **gksudo nautilus** in Terminal

**3** - Copy & paste the Firefox file that you have just extracted to **/opt**

Enter these commands in Terminal

> **sudo -i**
Enter your password if asked
> **cd /opt**
> **chown -R username firefox**
[COLOR="Red"]**The username is what you use to log in to Ubuntu**[/COLOR]

**4** - Right click on the Ubuntu start logo, select **Edit Menus**, 

**5** - Highlight the Internet sub menu & click New Item

You will now see a small dialogue box appear

**6** - In the Name field, type **Firefox**

**7** - In the Command field type **/opt/firefox/firefox**

**8** - In the Comment field type **Firefox**

You will now have Firefox installed.

---

### Post by gwu777 on 2010-02-16
Thqnk you for all your answers, it does explain a few things. I understand the last solution but I don't think my mum will, the command line is defenitly great and allows you to do everything so simply, but I try to focus on graphical tools because this is what my customers wants and they only agreed to use linux if it is as "easy" as windows!!!

It is like two world meeting in the middle!

---

### Post by gwu777 on 2010-02-18
> **scouser73 said:**
> I always mention installing the .tar.gz files, I find it to be easy (clearly not as easy installing via .deb but easy enough)

would your method be compatible with the 64 bit version downloaded? Even from the ppa, it hasn updated to the 3.7, it is 3.6, is it so difficult to just have a .deb file released by firefox, or this would be too specific to debian?

---

