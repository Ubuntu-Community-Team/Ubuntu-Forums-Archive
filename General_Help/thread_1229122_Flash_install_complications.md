---
title: "Flash install complications"
date: 2009-08-01
forum: General Help
---

### Post by XxionxX on 2009-08-01
I am very new to Ubuntu and Linux. I just installed Ubuntu on my computer and I was very happy with the the OS until I tried to install flash. I had just previously installed PHP, MySQL, and Apache (I am learning PHP) so i felt comfortable with the install process and I was even able to troubleshoot on my own. Then I tried to install flash :confused: and all of my effort was futile. I have spent the last two days trying to install flash. I have unstalled it at least 3 times. I have installed the nonfree plugin, I have used both package managers, and tried at least a dozen terminal comands from various threads and websites. I have no idea what I am doing wrong, and to make things more confusing SOME flash adverts work but youtube, and newgounds do not. I know that it is installed but I don't know why it's not working. Help anyone?

---

### Post by Tclarkie on 2009-08-01
[I]here is the double click .deb   
[http://rapidshare.com/files/155584596/install_flash_player_10_linux.deb](http://rapidshare.com/files/155584596/install_flash_player_10_linux.deb) 			[/I]

---

### Post by michy99 on 2009-08-01
> **Tclarkie said:**
> [I]here is the double click .deb   
[http://rapidshare.com/files/155584596/install_flash_player_10_linux.deb](http://rapidshare.com/files/155584596/install_flash_player_10_linux.deb) 			[/I]

I realize you are trying to help, but it would be better to point to a file on a trusted website than something on rapidshare that could be who knows what.

---

### Post by Tclarkie on 2009-08-01
dont worry, i got mine from hear and i virus checked it manually
it works

---

### Post by XxionxX on 2009-08-01
I tried the same .deb file from the adobe website at least twice!

---

### Post by XxionxX on 2009-08-02
Thats it? A .deb file  from a website that I had already tired? Am I doomed to be frustrated with linux and its non-usability?](*,)

---

### Post by t4ggs on 2009-08-02
just open add/remove and search for ubuntu restricted extras; install it and you will have flash+java+audio&video codecs

---

### Post by XxionxX on 2009-08-02
I had already installed the restricted extras package,(as one of the many tutorial websites showed me) but I un-installed and reinstalled the package anyway just to see if that was the problem. Still no youtube, newgounds, ect. although I am getting flash adverts that work. What does that mean?

---

### Post by wpshooter on 2009-08-02
> **XxionxX said:**
> I had already installed the restricted extras package,(as one of the many tutorial websites showed me) but I un-installed and reinstalled the package anyway just to see if that was the problem. Still no youtube, newgounds, ect. although I am getting flash adverts that work. What does that mean?

XxionxX:

First go into Synaptic and mark for removal (don't mark for complete removal) the flash plugins that you have installed and apply the change so the plugin will be removed.  Then restart your computer.

Then go to the "Real" (as opposed to some fake) Adobe website and download and install the TAR version of the Linux version of Adobe FlashPlayer.

You might want to download the tar file directly to the root of your home directory or move it to there before you untar it.  Once you have it in the home directory, then right hand click on it a extract it to the home directory.  This will create an Adobe Flash subdirectory in your home directory which you will use to install the Flash program to your computer.  You will need do the installation of Flash from the terminal.

You will also, need to know the version of Firefox browser or the location name of the browser that you are using because when you start the flash installer it will prompt you for that location.  For instance mine is:  /usr/lib/firefox-3.0.12

To start the installer from the terminal, first go to the terminal and then change directory to the Flash directory created by the extraction (the name of the directory you are looking for is 

**install_flash_player_10_linux**

and then run:

sudo ./flashplayer-installer

Write back if you need further assistance.

Good luck.

---

### Post by steveneddy on 2009-08-02
> **XxionxX said:**
> Thats it? A .deb file  from a website that I had already tired? Am I doomed to be frustrated with linux and its **non-usability**?](*,)

Look - Linux is as usable as the user wants it to be. Linux is actually more usable than Windows in my opinion.

The Adobe website tells you where to put the plugin - and FYI it goes in the Firefox folders.

There are countless places where you will find the information for correctly installing Flash.

Download the Flashplayer file from Adobe.

Put it on your Desktop.

Right click and select Extract.

There will be a file named** libflashplayer.so** created on your desktop.

Open a terminal and copy these commands into the terminal one at a time:

```
cd ~/Desktop
```then

```
sudo cp libflashplayer.so /usr/lib/firefox/plugins/ /usr/lib/firefox-addons/plugins/ /usr/lib/mozilla/plugins/
```Restart Firefox and in the address bar type

```
about:plugins
```and hit the Enter key

and see if a listing for Flash is in there.

If so go to a Flash web site like You Tube and see if it works.

EDIT:

There is probably a tutorial in the Ubuntu Resources link in my sig that will get you there also.

Please bookmark the links in my sig as you will need them in the future.

EDIT#2:

As you can see, there are a variety of ways to install software in Linux.

a.deb file will let you double click the file and install it like a Window's way.

You can find other automated and manual ways for installing software in Linux.

I suggest that if you are going to work in this environment then you need to study software installation.

Once you learn the ways of the force the Jedi battles become easier.

---

### Post by t4ggs on 2009-08-03
wich browser are u using?? is it firefox???

---

### Post by Tclarkie on 2009-08-03
this works heaps well [http://ubuntuforums.org/showthread.php?t=1230177](http://ubuntuforums.org/showthread.php?t=1230177)

---

### Post by XxionxX on 2009-08-06
Ok so I tried the way that steveneddy told me to install Flash, to no avail.  I got all the way up to this command

 ```
sudo cp libflashplayer.so /usr/lib/firefox/plugins/ /usr/lib/firefox-addons/plugins/ /usr/lib/mozilla/plugins/
```

And then I had this error message:

```

sudo cp libflashplayer.so /usr/lib/firefox/plugins/ /usr/lib/firefox-addons/plugins/ /usr/lib/mozilla/plugins/
cp: omitting directory `/usr/lib/firefox/plugins/'
cp: omitting directory `/usr/lib/firefox-addons/plugins/'

```

So I changed the command to this to get rid of the error message:

```
sudo cp -r libflashplayer.so /usr/lib/firefox/plugins/ /usr/lib/firefox-addons/plugins/ /usr/lib/mozilla/plugins/ 
```

This still did not install Flash.  But there were no error messages, and it seemed to execute alright.  Flash still still seems to be only working with ads and not on YouTube.

I tried wpshooter's method, and I got stuck when I extracted the install_flash_player_10_linux.tar.gz file. I didn't know what to do when I extracted the the file and I got a libflashplayer.so instead of the afformentioned install_flash_player_10_linux directory
Am I not getting the right file from Adobe wpshooter?

t4ggs I am using firefox.

Tclarkie I already tried both of the methods that you have on the link provided.

---

### Post by warp99 on 2009-08-06
Are you using the 32-bit or 64-bit version of Ubuntu? There are different versions of Adobe Flash with different methods to install.

---

### Post by XxionxX on 2009-08-06
I am using the 32-bit 9.04 Jaunty version of Ubuntu.

---

### Post by warp99 on 2009-08-06
Here's how you can clean up the mess:

1) Open the Synaptic package manager and in the search locater enter "flash" without the quotations.

2) Remove and purge any packages that pertain to Flash, Gnash, Adobe Flash, or SWF. To remove and purge the packages right click on the package and choose "Mark for Complete Removal".

3) Go into your .mozilla/plugins directory, which is located in your user home directory, and remove ANY flash plugins that may have been installed.

4) Go to the Adobe Flash site located here:

[http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP)

And Choose the "deb for Ubuntu 8.04+", then press install

5) Choose the gdebi package manager to install the deb if Firefox asks, enter you sudo password and install as normal.

6) Open a terminal and type the following:

```
sudo update-alternatives --config firefox-flashplugin
```

There should only be one flash alternative so nothing to configure. If not then choose the alternative that points to the following:

```
/usr/lib/adobe-flashplugin/libflashplayer.so
```

After this the flash plugin will work. Be sure to follow all of the steps since we need to back out some of the other flash alternatives that you may have installed.

---

### Post by XxionxX on 2009-08-06
Thank you warp99!:KS!! That did the trick! I am so happy that the problem is fixed! I would love to know what I what I did wrong so that I do not make a similar mistake.

---

### Post by warp99 on 2009-08-06
> **XxionxX said:**
> Thank you warp99!:KS!! That did the trick! I am so happy that the problem is fixed! I would love to know what I what I did wrong so that I do not make a similar mistake.

You tried to install either the flash plugin manually or installed a flash alternative, such as gnash, then installed the Adobe plugin without removing gnash. 

In the future only use the Adobe deb package from Adobe.com or the flashplugin-installer package in Synaptic that specifically states "Adobe Flash Player plugin installer" in the package notes. Personally I would just use the Adobe.com deb package since it's dead bang easy to install with a couple of mouse clicks and gdebi.

---

### Post by theRam on 2009-08-25
Thank you guys for your help. I've been struggling with this sh!t for days.

wpshooter: Thank you for pointing out that the file that needs to be downloaded and extracted is the "TAR" file, not the deb file for Ubunto8.04+ and up. You described this very well.(I'm running 8.10)

steveneddy: I wanna know what the magic line of code you wrote did. I think it's what got this working.
---------------------------
Just to give you guys an idea of what beginners are encountering. Non of the other methods to install flash worked for me. The direct plugin install from the youtube website will give me this error:
E: dpkg was interupted. You must manually run "depkg.......................

synpatic would give me the same error.

and Gdebi would give me the error:
Only one software managment tool is allowed to run at the same time.
-------------------

Any way thanks again for your help.

---

