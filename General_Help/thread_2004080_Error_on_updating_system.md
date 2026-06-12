---
title: "Error on updating system"
date: 2012-06-15
forum: General Help
---

### Post by hiranyaroma on 2012-06-15
Ever time I update the system i get the following error. Why is it so? My browser doesnt always play flash content, although I have installed flash aid. Could this error have something to do with it?

> 
Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

ttf-mscorefonts-installer, flashplugin-installer

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.

---

### Post by tommcd on 2012-06-15
How did you install flash aid?
If you used any third party repos, including those unsupported PPA repos, I would remove those.

I use Lubuntu 12.04 with Firefox 13 and the **flashplugin-installer**, and I can play flash videos just fine.

Try running ```
sudo apt-get update
``` and then ```
sudo apt-get dist-upgrade
``` from the terminal and post any errors that you get here.
This is of course *after* you have removed any third party repos.

---

### Post by hiranyaroma on 2012-06-15
> **tommcd said:**
> How did you install flash aid?
If you used any third party repos, including those unsupported PPA repos, I would remove those.

I use Lubuntu 12.04 with Firefox 13 and the **flashplugin-installer**, and I can play flash videos just fine.

Try running ```
sudo apt-get update
``` and then ```
sudo apt-get dist-upgrade
``` from the terminal and post any errors that you get here.
This is of course *after* you have removed any third party repos.

I installed flash aid from the add ons on the mozilla website. ([Link]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/"))
How can I know if I have installed third party repos and how to remove them?

---

### Post by cortman on 2012-06-15
If you remember manually adding repositories, either via Synaptic, USC or sources.list, you'll need to remove them- otherwise not.
Try dist-upgrade, and if that doesn't work run

```
sudo apt-get -f install
```

---

### Post by hiranyaroma on 2012-06-15
> **cortman said:**
> If you remember manually adding repositories, either via Synaptic, USC or sources.list, you'll need to remove them- otherwise not.
Try dist-upgrade, and if that doesn't work run

```
sudo apt-get -f install
```
I may have added some repositories unknowingly. I have done almost everything that is suggested on the flash related posts on forums. How do I know if there are unwanted repos? How to remove them?
I did dist upgrade. what does it do?
My browser still asks me to install flash everytime i visit youtube. Surprisingly I can play some videos on youtube, but most of the time the missing plugin error shows up.

---

### Post by cortman on 2012-06-15
> **hiranyaroma said:**
> I may have added some repositories unknowingly. I have done almost everything that is suggested on the flash related posts on forums. How do I know if there are unwanted repos? How to remove them?
I did dist upgrade. what does it do?
My browser still asks me to install flash everytime i visit youtube. Surprisingly I can play some videos on youtube, but most of the time the missing plugin error shows up.

The videos you can play on YouTube are HTML5, not flash.
As I recall FF gives you a button to press that says "Install missing plugins" or something to that effect- have you gone through with that? I don't think flash aid is what you want.
Like I said, unless you specifically were instructed to add repositories with Synaptic, USC, or by editing sources.list, you probably didn't add a repo.
Dist-upgrade upgrades your entire system including the kernel, as opposed to just upgrade which AFAIK only applies security patches.

---

### Post by hiranyaroma on 2012-06-16
> **cortman said:**
> The videos you can play on YouTube are HTML5, not flash.
As I recall FF gives you a button to press that says "Install missing plugins" or something to that effect- have you gone through with that? I don't think flash aid is what you want.
Like I said, unless you specifically were instructed to add repositories with Synaptic, USC, or by editing sources.list, you probably didn't add a repo.
Dist-upgrade upgrades your entire system including the kernel, as opposed to just upgrade which AFAIK only applies security patches.
Oh, so those youtube videos are HTML5! Alright. And yes, I too think its not a problem with flash aid. Firefox asks me to isntall missing plugins and when I click on that, it says, "flash installed successfully" and asks me to restart firefox. When I restart, the missing plugin button shows up again!

Edit: And, I get the same error that I posted on the first post in this thread when I do a dist upgrade.

---

### Post by tommcd on 2012-06-16
> **hiranyaroma said:**
> I installed flash aid from the add ons on the mozilla website.
This by itself will not add any third party repos. The flash aid is just a FF addon.
> **hiranyaroma said:**
> 
How can I know if I have installed third party repos and how to remove them?
Post the contents of your **/etc/apt/sources.list** file as well as any files in the **/etc/apt/sources.d/** directory.
You can remove third party repos through the Synaptic package manger by going to: software sources > third party repositories, and uncheck any third party sources that are there. Then reload Synaptic when prompted.
There is also a handy tool to regenerate your sources.list. See this answer here:
[http://askubuntu.com/questions/124017/how-do-i-restore-the-default-repositories](http://askubuntu.com/questions/124017/how-do-i-restore-the-default-repositories)
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)
I would just remove them through Synaptic first though.

---

### Post by hiranyaroma on 2012-06-16
> **tommcd said:**
> This by itself will not add any third party repos. The flash aid is just a FF addon.

Post the contents of your **/etc/apt/sources.list** file as well as any files in the **/etc/apt/sources.d/** directory.
You can remove third party repos through the Synaptic package manger by going to: software sources > third party repositories, and uncheck any third party sources that are there. Then reload Synaptic when prompted.
There is also a handy tool to regenerate your sources.list. See this answer here:
[http://askubuntu.com/questions/124017/how-do-i-restore-the-default-repositories](http://askubuntu.com/questions/124017/how-do-i-restore-the-default-repositories)
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)
I would just remove them through Synaptic first though.
Contents of **/etc/apt/sources.list**

> # 

# deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release i386 (20120423.1)]/ precise main multiverse restricted universe

#deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release i386 (20120423.1)]/ precise main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

Files in  **/etc/apt/sources.d/** directory :- medibuntu.list (Its content is empty).

I removed two software sources named "independent" and tagged as 'third party software' in the Synaptic.

---

### Post by tommcd on 2012-06-17
Your **sources.list** looks to be pristine and is free of any third party repos.
Are you still getting the same error you posted in your first post???
If so, try reomving the offending packages that were listed in the error message:
```
sudo apt-get remove --purge ttf-mscorefonts-installer, flashplugin-installer
```
Also remove any other flash you may have installed outside of the Ubuntu repositories.
You can always install the **flashplugin-installer** package again after you get this fixed.
Then try running: 
```

sudo apt-get update
sudo apt-get dist-upgrade

```
and see if you can update the system.

---

### Post by hiranyaroma on 2012-06-18
> If so, try reomving the offending packages that were listed in the error message

Ok. I removed the offending packages. Now I dont get any error on updating the system.

> You can always install the **flashplugin-installer** package again after you get this fixed.

I did this and the error message started showing up again. And, flash still doesnt work.

---

### Post by cortman on 2012-06-18
The easiest way to install flash in Ubuntu that I've found is through Firefox. If that isn't working, maybe try reinstalling Firefox? Be sure to export your bookmarks first if you want to save them.

```
sudo apt-get install --reinstall firefox
```

Then go to a site using flash, and carefully follow through the plugin installation.
Good luck!

---

### Post by hiranyaroma on 2012-06-19
> **cortman said:**
> The easiest way to install flash in Ubuntu that I've found is through Firefox. If that isn't working, maybe try reinstalling Firefox? Be sure to export your bookmarks first if you want to save them.

```
sudo apt-get install --reinstall firefox
```

Then go to a site using flash, and carefully follow through the plugin installation.
Good luck!
I did everything just like you said. Again, the error popped up in the end! May be it is something that you mentioned in your last line. I dont seem to have good luck. :-)

P.S: I connect to the internet using a proxy. Does it have anything to do with this (like, I may have to enter the proxy details somewhere)?

---

### Post by tommcd on 2012-06-19
> **hiranyaroma said:**
> Ok. I removed the offending packages. Now I dont get any error on updating the system.
> You can always install the flashplugin-installer package again after you get this fixed. 
I did this and the error message started showing up again. And, flash still doesnt work.
How did you install the **flashplugin-installer** package? The best way is to install it from the Ubuntu repos like this:
```
sudo apt-get install flashplugin-installer
```
If you installed the flashplugin-installer package any other way then remove it and install it again from the Ubuntu repos as I posted here.

If that does not work; and if you are still getting these error messages; and if flash still does not work, then remove flash altogether like this:
```
sudo apt-get remove --purge flashplugin-installer
```
Then install flash from adobe.com like this:

1. Download the flash .tar.gz file to your home directory from adobe.com:
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
Get the 32-bit .tar.gz file for 32-bit Lubuntu 12.04; or get the 64-bit .tar.gz file for 64-bit Lubuntu 12.04. The adobe download site will check whether you have 32-bit or 64-bit Linux and offer the appropriate version

2. Make a plugins directory in **~/.mozilla/firefox** like this:
```
mkdir ~/.mozilla/firefox/plugins
```

3. Then untar the flashplugin installer to that plugins directory like this:
```
cd ~
tar -xvzf install_flash_player_XXX.tar.gz -C ~/.mozilla/firefox/plugins
```
Note that the XXX in the above command is just a shorthand for the actual name of the flash .tar.gz file that you downloaded. To make it simple, just type in the terminal:
```
tar -xvzf install
``` and hit the **TAB** key and it will auto complete the file name. Then type the rest of the command as shown:
```
-C ~/.mozilla/firefox/plugins
```

4. Then restart Firefox and flash should be working.

I just tested this on my laptop by removing the flashplugin-installer package from the Ubuntu repos and installing the flash from adobe.com to my home directory in the **.mozilla/firefox/plugins** directory and it works for me.

By the way **~** is shorthand for your home directory.

---

### Post by hiranyaroma on 2012-06-19
> I just tested this on my laptop by removing the flashplugin-installer  package from the Ubuntu repos and installing the flash from adobe.com to  my home directory in the **.mozilla/firefox/plugins** directory and it works for me.

Earlier, I had installed flash from ubuntu repos. Now I did it this tar.gz way but flash still doesnt work for me. 
By the way, I enjoyed installing flash this way. Never used a tar.gz file before. What does "-xvzf" do? The whole command and option "tar -xvzf"  just untars the file?

---

### Post by tommcd on 2012-06-20
> **hiranyaroma said:**
> Earlier, I had installed flash from ubuntu repos. Now I did it this tar.gz way but flash still doesnt work for me. 
As I said in my last post, you must remove *all* flash packages that you have installed from *any* repositories. This will remove any conflicts between flash from the Ubuntu repos and flash in your *~/.mozilla/firefox/plugins* directory.
While you are at it, remove the *flash aid* Firefox addon that you installed.
Also, just to avoid a corrupted profile, remove your *.mozilla* directory from your home directory:
```
cd ~
rm -r .mozilla

```
Note that this will remove all of your addons as well as bookmarked web pages; but once you re-launch Firefox it will create a pristine new profile for you. Then follow the instructions again for installing flash from adobe.com that I listed in my last post.
Just to make sure that you do not have any flash installed from the repos. Post the output of:
```
aptitude search flash
```
In the output a "**p**" before a package means it is purged (i.e., not installed) An "**i**" before a package means it is installed. Remove any flash packages that are installed using apt-get:
```
sudo apt-get remove --purge foo
```
Where foo is the name of the package that you want to remove.
> **hiranyaroma said:**
> 
By the way, I enjoyed installing flash this way. Never used a tar.gz file before. What does "-xvzf" do? The whole command and option "tar -xvzf"  just untars the file?
You can read about this from the *tar* man page. Just type *man tar* in the terminal.
The switches I used for tar are:
-x extract the file
-v verbose (i.e., display detailed output in the terminal).
-z if for a .tar.gz (gzip) file. You would use -j instead for a .tar.bz2 (bzip2) file.
-f is for file. This should be at the end of the command for some technical reason I can't remember now!
You type the options you want together in the command: *tar -xvzf; tar -xvjf* etc.
The -C before *~/.mozilla/firefox/plugins/* means "change directory", i.e., untar the file to the indicated directory listed after 
the -C instead of the current directory.

Note that the packages from the Ubuntu repos should always be your first choice for installing any software. I only suggested the flash.tar.gz from Adobe because you were having so much trouble installing flash from the repos.
I suspect your troubles comes from the fact that in post #5 you said:
> **hiranyaroma said:**
> I may have added some repositories unknowingly. I have done almost everything that is suggested on the flash related posts on forums. ...
So you may have done something that is messing this up somehow.
The **flashplugin-installer** package from the Ubuntu repos always works for me. Installing flash from adobe.com to 
your *~/.mozilla.firefox/plugins* directory will work also; but only have *one* flash package installed at a time. If you have multiple flash packages then this would likely cause conflicts.

---

### Post by hiranyaroma on 2012-06-20
Thnaks for the detailed suggestion. Still no luck though. Here is the output that you asked me to post.

> v   adobe-flash-properties          -                                           
p   adobe-flash-properties-gtk      - GTK+ control panel for Adobe Flash Player 
p   adobe-flash-properties-kde      - KDE control panel Adobe Flash Player plugi
p   adobe-flashplugin               - Adobe Flash Player plugin version 11      
p   flashbake                       - automated snapshots with git              
p   flashplugin-downloader          - Adobe Flash Player plugin installer (trans
p   flashplugin-installer           - Adobe Flash Player plugin installer       
v   flashplugin-nonfree             -                                           
p   flashplugin-nonfree-extrasound  - Adobe Flash Player platform support librar
p   flashrom                        - Identify, read, write, erase, and verify B
p   flashybrid                      - automates use of a flash disk as the root 
p   get-flash-videos                - video downloader for various Flash-based v
p   libdancer-plugin-flashmessage-p - Dancer plugin to display temporary, so cal
p   m16c-flash                      - Flash programmer for Renesas M16C and R8C 
p   python-webflash                 - Portable flash messages for Python WSGI ap
p   tvflash                         - Mellanox firmware update utility          
p   vrflash                         - tool to flash kernels and romdisks to Agen

> So you may have done something that is messing this up somehow.

Maybe. I have windows installed on my laptop which i use for all practical purposes. I installed lubuntu on my old desktop just to learn Linux. So flash is not compulsory. I will keep trying. Will post if it gets sorted out.

---

### Post by tommcd on 2012-06-21
> **hiranyaroma said:**
> Thnaks for the detailed suggestion. Still no luck though. Here is the output that you asked me to post.

Your output of *aptitude search flash* indicates that you have no flash installed from the Ubuntu repos.

You should have flash copied to **~/.mozilla/firefox/plugins** if you followed my instructions properly from post #14 in this thread. Make sure the **libflashplayer.so** file is in there.

I don't know what else to suggest at this point. I am not sure why this is not working for you.

---

### Post by rubo77 on 2012-08-15
I had the same Problem and the solution was this:

```

sudo apt-get remove --purge ttf-mscorefonts-installer
sudo apt-get install ubuntu-restricted-extras

```

see
[http://askubuntu.com/questions/153928/annoying-message-is-showing-after-installing-ttf-mscorefonts-installer-package](http://askubuntu.com/questions/153928/annoying-message-is-showing-after-installing-ttf-mscorefonts-installer-package)

---

### Post by hiranyaroma on 2012-08-16
> **rubo77 said:**
> I had the same Problem and the solution was this:

```

sudo apt-get remove --purge ttf-mscorefonts-installer
sudo apt-get install ubuntu-restricted-extras

```

see
[http://askubuntu.com/questions/153928/annoying-message-is-showing-after-installing-ttf-mscorefonts-installer-package](http://askubuntu.com/questions/153928/annoying-message-is-showing-after-installing-ttf-mscorefonts-installer-package)
Thanks for the reply. I looked into that post. Didnt work for me.

---

### Post by rubo77 on 2012-08-16
> **hiranyaroma said:**
> Thanks for the reply. I looked into that post. Didnt work for me.

maybe it worked for me cause i restarted the system before i installed the extras:

```
sudo apt-get remove --purge ttf-mscorefonts-installer
sudo restart
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by hiranyaroma on 2013-02-10
Finally! I was able to install flash player after about 5 months after I first  switched to Linux. This is what worked for me. I wonder why no one  suggested this to me before.


[LIST=1]
[*]Open [http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)
[*]Choose Linux 32-bit on Step 1
[*]Choose Flash Player 11.2 (tar.gz) on Step 2, download the file
[*]Once download is complete, right click on the flie (tar.gz) and click on "Extract here"
[*]  Launch Terminal (Keyboard Shortcut : Ctrl+Alt+T)
[*]Go to that  location where you extracted the file. Get inside the extracted folder  see to the location where lobflashplayer.so is present.
[*]Run this command : sudo mv libflashplayer.so /usr/lib/firefox-addons/plugins
[*]Launch Mozilla Firefox and check do you have Adobe Flash Player
[/LIST]

---

