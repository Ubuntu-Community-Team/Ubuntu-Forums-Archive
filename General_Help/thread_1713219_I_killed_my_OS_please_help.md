---
title: "I killed my OS please help"
date: 2011-03-23
forum: General Help
---

### Post by Felzidf on 2011-03-23
Hi everyone
I was trying to reinstall apt and accidentally uninstalled apt packages, after that i could no longer get conection to the internet and couldnt reinstall it from the terminal, later  i rebooted and can't log on anymore . 
Now the only thing that i can do is enter to the SO from livecd, or enter to the screen menu to select the user and there enter to the terminal with ctrl+alt+f2.
I tried to use sudo apt-get update and a message says that could not resolve co.archive.ubuntu.com and unable to fetch some archives.
and other errors says that [I]the method driver /usr/lib/apt/methods/ttp could not be found.
[/I]
Is there a way to repair this,like running an upgrade from the livecd to restore the missing parts without wiping out my conf and other programs[I]? 
[/I]or using the terminal from the user screen menu, but maybe my sources list has something wrong. please help me fixing this problem.

---

### Post by idoitprone on 2011-03-25
Look like you are in the same boat as this person [http://ubuntuforums.org/archive/index.php/t-90441.html](http://ubuntuforums.org/archive/index.php/t-90441.html) You will have to reinstall apt package manually with dpkg good luck

Here, how to use dpkg.
[http://everyjoe.com/technology/howto-use-dpkg-to-install-deb-files/](http://everyjoe.com/technology/howto-use-dpkg-to-install-deb-files/)

You might have to chroot it, if booting on live cd
[http://ubuntuforums.org/showthread.php?p=9486700#post9486700](http://ubuntuforums.org/showthread.php?p=9486700#post9486700)

Look at drs305 first block of code on how to chroot it


What do you mean you cannot loggin anymore?

Did you ever try command line method to get on the internet? I highly doubt that you uninstall those wireless tools

---

### Post by Felzidf on 2011-03-27
> **idoitprone said:**
>  You will have to reinstall apt package manually with dpkg good luck

 What do you mean you cannot loggin anymore?

Did you ever try command line method to get on the internet? I highly doubt that you uninstall those wireless tools

Hi thanks for answer.

Well i can not log to the os, because when i turn on my laptop ubuntu shows me the user menu, there i select my user/password but when i finish it, the system turns me back to the user menu.
then my only option is using the terminal in the user menu.
I have installed an apt package with dpkg, but i need to do sudo apt-get update because i have uninstalled more packages :/, but when i do that  it says :
Failed to fetch [http://packages.medibuntu.org/](http://packages.medibuntu.org/) could not resolve packages.medibuntu.org.
I think i have uninstalled the wireless tools too.

---

### Post by idoitprone on 2011-03-28
> **Felzidf said:**
> Hi thanks for answer.

Well i can not log to the os, because when i turn on my laptop ubuntu shows me the user menu, there i select my user/password but when i finish it, the system turns me back to the user menu.

that sound like a fail loggin attempt. A simple test is to add an new user and login as a new user
[http://www.howtogeek.com/howto/ubuntu/add-a-user-on-ubuntu-server/](http://www.howtogeek.com/howto/ubuntu/add-a-user-on-ubuntu-server/)


> 
Failed to fetch [http://packages.medibuntu.org/](http://packages.medibuntu.org/) could not resolve packages.medibuntu.org.
I think i have uninstalled the wireless tools too.You could not have uninstalled those wireless tools, you have to manually connect to the internet
Do you use ethernet? 

[http://www.linuxforums.org/forum/suse-linux/19332-connect-internet-through-command-line.html](http://www.linuxforums.org/forum/suse-linux/19332-connect-internet-through-command-line.html)
or wifi?

[http://ubuntuforums.org/showthread.php?t=560500l](http://ubuntuforums.org/showthread.php?t=560500l)

---

