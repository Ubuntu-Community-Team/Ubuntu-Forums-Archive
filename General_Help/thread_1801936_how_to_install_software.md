---
title: "how to install software ?"
date: 2011-07-11
forum: General Help
---

### Post by vikash_chandola on 2011-07-11
this is my first software install in the Linux. In windows i am familiar how install a software but how to do this in Linux.

This is VLC media player for Ubuntu 10.04 but i am trying to install in my xubuntu 11.04. 

thanks for help.

---

### Post by Elfy on 2011-07-11
Any particular reason why you want to install the old version?

The first place to look for apps is in the software centre. 

[https://help.ubuntu.com/11.04/ubuntu-help/addremove.html](https://help.ubuntu.com/11.04/ubuntu-help/addremove.html)
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

---

### Post by vikash_chandola on 2011-07-11
> **forestpiskie said:**
> Any particular reason why you want to install the old version?

The first place to look for apps is in the software centre. 

[https://help.ubuntu.com/11.04/ubuntu-help/addremove.html](https://help.ubuntu.com/11.04/ubuntu-help/addremove.html)
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)
When i open archieve there was a file name readme,txt it was written there
```

***************************************
Thank you for downloading this package.
***************************************

This Installer is intended to install VLC 1.0.6 with out internet connection.

###############################
Installing Restricted Packages
###############################

1. Double click on the "install.sh" file

2. In the new window click "Run in Terminal"

3. Enter your password in Terminal (if it asks)

Thats it...

##############################################

```
OK i open  "install.sh"
Bu after that that a similar file open with this message
```

#!/bin/bash
########################################
# This script is to install "VLC_1.0.6" on Ubuntu 10.04
# on a system without internet connection
# created by ubuntu user
###################################

#Initial message
echo "VLC_1.0.6" offline installer
echo for Ubuntu 10.04
echo
echo by ubuntu user
echo
sleep 3

#Install packages
echo Please do not interrupt the installer...
sleep 3
sudo dpkg -i packages/*

#Final message
echo
echo
echo
echo
echo
echo
echo
echo The package "VLC_1.0.6" should now be installed!
echo
echo All finished here! You can now close this window...
sleep 1d
exit

```
What should i do how to install i am confused.

Thanks to any person who try to help.

---

### Post by Surendil on 2011-07-11
try
```
 apt-get install vlc 
```

---

### Post by Elfy on 2011-07-11
You need to first forget the "I'll get it from the internet somewhere" Windows mentality - it's rarely needed. 

Use the apps that are available in the repositories - read the links I gave you, they'll give you a start.

---

### Post by vikash_chandola on 2011-07-11
> **forestpiskie said:**
> You need to first forget the "I'll get it from the internet somewhere" Windows mentality - it's rarely needed. 

Use the apps that are available in the repositories - read the links I gave you, they'll give you a start.
tell me how to install this one don't give unwanted advices.

**Surendil** where to write command you gave me.

---

### Post by Elfy on 2011-07-11
you write the command in a terminal - you need to run it as root, that is sudo command 

That though will have nothing to do with any package you downloaded from the internet,  to use that you can search for installing from a tarball. 

> tell me how to install this one don't give unwanted advices.Is likely to get people to not bother to help you.

---

### Post by vikash_chandola on 2011-07-11
> **forestpiskie said:**
> 

Is likely to get people to not bother to help you.
I am intended so i  want that you help in that point in which i want your help not in that point in which you think is appropriate. 

BIG **** i am feeling to abuse.
Why i can't install a software. 
If  i install vlc from software center then will i able to reinstall that without using Internet.
I have a limited Internet connection so i will not download a software multiple times It will be wastage of money.

---

### Post by Elfy on 2011-07-11
When you install something using apt-get (that covers command line, synaptic, add/remove and software centre) the downloaded file is stored on your PC - if you then removed and reinstalled - the downloaded file would still be there - UNLESS you used the apt-get clean command. 

If you install something via the repos then they are tested to work with the version of ubuntu you are using. 

Sometimes you'll get something from the 'web' and you'll find that you don't have the necessary files on your system to use it. 

It is rare that you'll need to get something externally. Not never - but rare.

You might also look into aptoncd and keryx - offline installers.

---

### Post by Mark Phelps on 2011-07-11
The text that you provided already says that installation script is for 10.04 -- NOT for the version of Ubuntu you have installed.

It is very likely that what you want to do can NOT be done -- the way you want do to it -- and you lecturing folks who are only trying to provide you a way that it CAN be done -- that is not helping the situation.

So, either follow the advice you've been given or stop complaining.

---

### Post by vikash_chandola on 2011-07-11
Thanks to all after an hour try i have installed vlc media player.;)
> ]When you install something using apt-get (that covers command line,  synaptic, add/remove and software centre) the downloaded file is stored  on your PC - if you then removed and reinstalled - the downloaded file  would still be there - UNLESS you used the apt-get clean command. 

If you install something via the repos then they are tested to work with the version of ubuntu you are using. 

Sometimes you'll get something from the 'web' and you'll find that you don't have the necessary files on your system to use it. 

It is rare that you'll need to get something externally. Not never - but rare.

You might also look into aptoncd and keryx - offline installers.
I install it(vlc) from software center it makes me happy that all files of installation of vlc media player are still in my computer and if i remove vlc then i can reinstall that without Internet,
Thanks :D:D:D:D:D:D:D

---

### Post by el_koraco on 2011-07-11
Yes, it will be stored in the cache, and when you go to install it next time it won't need to pull it from the internet. Make sure you don't clean the cache then. 

In the future, if you want to download stuff from the internet, look for .deb files. You just double-click on those.

---

