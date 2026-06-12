---
title: "Help! I cannot set up file sharing with Windows! :("
date: 2011-06-23
forum: General Help
---

### Post by linuxuser12345 on 2011-06-23
I keep trying and keep trying to set up my father's documents folder on our PC running Ubuntu 11.04 as a shared folder across the network with Windows computers, and I keep getting error messages like this one:

"'net usershare' returned error 255: net usershare add: cannot share path /home/frank as we are restricted to only sharing directories we own.
    Ask the administrator to add the line "usershare owner only = false" 
    to the [global] section of the smb.conf to allow this."

I currently have his home folder set up so anyone on our PC running Ubuntu can access and change the files, at the moment. I also want to know if I can set up this file sharing with Windows, but still have all his files protected with a password?

Thanks,
Linuxuser12345

---

### Post by linuxuser12345 on 2011-06-23
Can somebody please help me out with this? :(

Thanks

---

### Post by haqking on 2011-06-23
> **linuxuser12345 said:**
> Can somebody please help me out with this? :(

Thanks

Do you have samba setup ?

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by linuxuser12345 on 2011-06-23
I have absolutely *no* idea how to follow those instructions. o.0
Is there a way I can set up file sharing with Windows in a GUI?

---

### Post by haqking on 2011-06-23
> **linuxuser12345 said:**
> I have absolutely *no* idea how to follow those instructions. o.0
Is there a way I can set up file sharing with Windows in a GUI?

if you have a problem following instructions then i think you wont get much help ? LOL

try this then [http://www.unixmen.com/linux-tutorials/1060-how-to-configure-samba-using-a-graphical-interface-in-ubuntu](http://www.unixmen.com/linux-tutorials/1060-how-to-configure-samba-using-a-graphical-interface-in-ubuntu)

and get used to using the search facility, SAMBA and windows file sharing has been covered including tutorials on here.

good luck and remember CLI is your friend, GUI has its place but it is right underneath CLI ;-)

---

### Post by linuxuser12345 on 2011-06-23
Thanks! :)

Any other suggestions?

---

### Post by haqking on 2011-06-23
> **linuxuser12345 said:**
> Thanks! :)

Any other suggestions?

Well i have given you  the command line and GUI way to do it, it dont get much simpler than the last link i sent you for GUI setup.

If these are 2 difficult for you to follow then i suggest getting more use to Linux before trying to set up services, file shares etc.

There are plenty of tutorials around on how to do it, keep looking until you find one you can follow but it is pretty simple ;-)

what exactly were you looking for ?

---

### Post by linuxuser12345 on 2011-06-23
I just want to share a folder with a Windows PC in our house. That's it

---

### Post by haqking on 2011-06-23
> **linuxuser12345 said:**
> I just want to share a folder with a Windows PC in our house. That's it

and to repeat and after you asked for a GUI way fo doing it here you are again:

[http://www.unixmen.com/linux-tutorials/1060-how-to-configure-samba-using-a-graphical-interface-in-ubuntu](http://www.unixmen.com/linux-tutorials/1060-how-to-configure-samba-using-a-graphical-interface-in-ubuntu)

it is the same link i provided before with step by step instructions that couldnt be any clearer,this will do what you are wanting to do !

---

### Post by akand074 on 2011-06-23
> **linuxuser12345 said:**
> I just want to share a folder with a Windows PC in our house. That's it

Right click a folder you want to share and choose "Sharing Options". Choose "Share this folder" and it'll automatically ask you if you want to install the necessary services, choose yes. It'll install them all and you'll have to restart. After the restart, go back to that folder and do the same thing, it'll let you this time. You can now share any folder with Windows. In Windows it should come up in your network shares. If it doesn't at first, go to "run" in windows (Windows Logo + r) and type

```
//computer-name
```

and change computer-name with the name of your Ubuntu computer.

---

### Post by linuxuser12345 on 2011-06-23
> **akand074 said:**
> Right click a folder you want to share and choose "Sharing Options". Choose "Share this folder" and it'll automatically ask you if you want to install the necessary services, choose yes. It'll install them all and you'll have to restart. After the restart, go back to that folder and do the same thing, it'll let you this time. You can now share any folder with Windows. In Windows it should come up in your network shares. If it doesn't at first, go to "run" in windows (Windows Logo + r) and type

```
//computer-name
```and change computer-name with the name of your Ubuntu computer.
I already tried that.

After I go type in "//computer-name" into the Run dialog, do I log in with my Windows username and password, or the username and password under Ubuntu?

---

### Post by haqking on 2011-06-24
> **linuxuser12345 said:**
> I already tried that.

After I go type in "//computer-name" into the Run dialog, do I log in with my Windows username and password, or the username and password under Ubuntu?

[https://help.ubuntu.com/8.04/internet/C/networking-shares.html](https://help.ubuntu.com/8.04/internet/C/networking-shares.html)

---

### Post by akand074 on 2011-06-24
> **linuxuser12345 said:**
> I already tried that.

After I go type in "//computer-name" into the Run dialog, do I log in with my Windows username and password, or the username and password under Ubuntu?

No your Ubuntu username and password

---

### Post by NRios on 2011-08-08
> **haqking said:**
> [https://help.ubuntu.com/8.04/internet/C/networking-shares.html](https://help.ubuntu.com/8.04/internet/C/networking-shares.html)

Can you please stop repeating the same nonsense and stop being patronising? The page you quote was written three years ago and diverges from current reality in step two (step one: you right click, step two: there is no "sharing options"). Did you know that?

So if you have nothing helpful to say, do shut up and stop insulting people who need help. Because this is a "help" forum, OK?

Thanks for nothing.

---

### Post by Morbius1 on 2011-08-08
> The page you quote was written three years ago and diverges from current  reality in step two (step one: you right click, step two: there is no  "sharing options")If you are using Ubuntu - Gnome there is a "sharing options". If it's not there install the following:
```
sudo apt-get install nautilus-share
```If you are not using Gnome what are you using?

---

