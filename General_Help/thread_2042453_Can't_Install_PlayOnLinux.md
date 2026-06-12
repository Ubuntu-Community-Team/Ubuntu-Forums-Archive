---
title: "Can't Install PlayOnLinux"
date: 2012-08-14
forum: General Help
---

### Post by Bagels on 2012-08-14
Hey guys!

I'm new to Ubuntu and also the forums * Sorry if I'm posting in the wrong thread* I read online that you can install and play some Steam games on Ubuntu.

I've tried installing playonlinux but i keep getting a error message saying " Package dependencies cannot be resolved, playonlinux: Depends: x-terminal-emulator but it is a Virtual package"

I'm not really sure what that means and any help would be appreciated!

---

### Post by Paddy Landau on 2012-08-14
Please tell us which version of Ubuntu you have, and how specifically you are trying to install PlayOnLinux.

---

### Post by Bagels on 2012-08-14
I have 12.04 LTS  and through the Ubuntu Software Center

---

### Post by johnathansmith on 2012-08-14
Hi, this problem is appeared before. Here is a [thread]("http://ubuntuforums.org/showthread.php?t=2024609&page=3"). So far the guy having this problem solved it with fresh installation of 12.04 64bit. Hope this help you.

---

### Post by Moose on 2012-08-15
Why don't you just get Wine? It is basically the same download size and it serves the same purpose. And it works for more than just games, i can run any program that works on windows. (Although some programs might not run or will need third party software to run like java etc)
 
-Anarchy

---

### Post by Paddy Landau on 2012-08-15
> **AnarchyTech said:**
> Why don't you just get Wine?
Because PlayOnLInux hides Wine's complexity, and makes it very easy to uninstall Windows applications without affecting other Windows applications.

Bagels:

[LIST]
[*]Have you fully updated your system? If not, please open your Update Manager, press *Check*, and then *Install Updates*.
[/LIST]

[LIST]
[*]Then, open a Terminal and enter the following command (it will prompt for your password).```
sudo apt-get install playonlinux
```
[/LIST]

[LIST]
[*]Finally, copy the results of the command (highlight the lines with your mouse, right-click > Copy), and paste them here (between [FONT=Lucida Console][noparse]```
[/noparse][/FONT] and [FONT=Lucida Console][noparse]
```[/noparse][/FONT]).
[/LIST]

---

### Post by Bagels on 2012-08-17
I updated like you said and tried that command and got this

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 playonlinux : Depends: wine or
                        wine-unstable but it is not installable
E: Unable to correct problems, you have held broken packages.
```

---

### Post by Bagels on 2012-08-18
Bump! *Sorry!*

---

### Post by zombifier25 on 2012-08-18
Try adding the Wine PPA. Type this in the terminal:
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```

---

### Post by Bagels on 2012-08-19
Got this

```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.nQx76t7kpd --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 883E8688397576B6C509DF495A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: key F9CB8DB0: "Launchpad PPA for Ubuntu Wine Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1 
```
Tried installing again and still doesn’t work

---

### Post by Paddy Landau on 2012-08-19
I am a bit perplexed about your problem. Let's try adding the official PlayOnLinux PPA to see whether or not it fixes things.

Open a terminal and enter the following commands. I have presumed that you have 12.04 Precise. If not, please replace "precise" in the second command with your distro. Use cut-and-paste to prevent typing errors.

```
wget http://deb.playonlinux.com/public.gpg -O- | sudo apt-key add -
sudo apt-add-repository 'deb http://deb.playonlinux.com/ precise main'
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install playonlinux
```Please paste any errors you get.

If it still does not work, please enter the following command and paste the errors:
```
sudo apt-get install wine
```

---

### Post by alagiri on 2013-07-16
Hi i am new the ubuntu. i have encountered a problem installing playonlinux. below is the copy from the terminal.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 playonlinux : Depends: icoutils but it is not installable
               Depends: p7zip-full but it is not installable
E: Unable to correct problems, you have held broken packages.

Please help.

---

### Post by Paddy Landau on 2013-07-16
> **alagiri said:**
> … i have encountered a problem installing playonlinux…

[LIST=1]
[*]Which version of Ubuntu are you using? 
[*]Specifically how are you attempting to install PlayOnLinux? (Are you using the standard repositories; are you using a different repository; or did you download the package from a website?) 
[/LIST]

---

