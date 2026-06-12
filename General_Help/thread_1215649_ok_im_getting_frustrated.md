---
title: "ok im getting frustrated"
date: 2009-07-17
forum: General Help
---

### Post by mypp on 2009-07-17
ok i just installed fresh copy of ubuntu and i was using windows xp sp3 pro before hand. im pretty skilled in windows but im pretty clueless now that i am a noob at linux. everytime i try to install anything it always comes in this tar.bz2 format and when i open it i have NO idea what to do, theres no installation file and even if there is the file type just says unknown. i tried to install rpm er w/e it is to recognize the files. not sure what to do in need of help.

heres what it looked like when i tried to install firefox 3.5

---

### Post by CatKiller on 2009-07-17
Ubuntu uses [packages]("http://en.wikipedia.org/wiki/Package_management_system") to install software. You can read [this page]("http://www.psychocats.net/ubuntu/installingsoftware") to learn more about installing software in Ubuntu.

---

### Post by iamkrazee on 2009-07-17
for your convenience, you can open shell, and type 

```
cd /firefox
```
then
```
./firefox-bin
```

---

### Post by CatKiller on 2009-07-17
> **iamkrazee said:**
> for your convenience, you can open shell, and type 

```
cd /firefox
```

Actually, no. First he'd have to extract it somewhere, and then it would be ```
cd wherever/he/extracted/it/to/firefox
```for example,

```
cd Desktop/firefox
```

**cd /firefox** would try to change directory to a sub-directory of /, which won't exist.

---

### Post by Cityscape on 2009-07-17
I have the same problem.
So where do i type these commands? In Terminal?
_________________________
Be Patient, I'm a Linux Newbie

---

### Post by nikhilbhardwaj on 2009-07-17
yes ofcourse in the terminal
but if you are a noob
then use the synaptic package manager instead

---

### Post by Armor Nick on 2009-07-17
In the archive you downloaded, the firefox file should be an executable though. Can you rightclick and choose the permissions tab, then check whether executable rights are allowed?

---

### Post by lukeiamyourfather on 2009-07-17
Its important to know the differences between how Windows software is distributed and how Linux software is distributed. Windows typically provides an installer which places files where they need to be and adds configuration information to the registry. When uninstalling all of the files and registry that needs to be removed is stored in a local database with the rest of the software on the system.

In Linux software can be distributed in a package, a binary file, and as source code. A package is similar to a Windows installer and is usually distribution specific (for example a Fedora pacakge will probably break in Ubuntu). The package knows what other software is required to run, where everything goes so it can be uninstalled later, and is easy to install. Many packages are available directly through the Ubuntu servers. For example if you want to install Firefox 3.5 there are several ways. The package already prepared for Ubuntu can be obtained through a package manager like Synaptic or the Add/Remove Programs in the applications list. Or you can use the command line tools like:

```
sudo apt-get install firefox-3.5
```

The "sudo" makes you root, "apt-get" is the package manager, "install" is what you want to do, and "firefox-3.5" is the name of the package you want to install. To remove it use "purge" instead of install.

What you downloaded in the screenshot is a binary executable, basically like running the software without having to install it. This can be handy but won't have features that a package does like updates through the package manager, and it won't add itself to the applications menu or system path, and would require manual uninstall if you want to get rid of it. Binary executable downloads like that are not distribution specific which is handy for some software but is more cumbersome for the end user than a package.

The last option is to install something from source code but that can wait until you're familiar with using packages. I've found 99% of the time you don't have to install something from source because there's already a package available for it from one place or another. Cheers!

---

### Post by UranUtan on 2009-07-17
This seems to indicate that you are new to Linux. I am in the same situation. The quick answer is I would suggest you to install software via the Menu:

- Application / Add Remove Programs
or
- System / Administration / Synaptic Pakage Manager
or
- Donwload a *.deb package and install using sudo dpkg -i nameOfProgram.deb

Avoid installing program from sources. You will go to an endless road where there is always a library missing, each of them is a cryptic message where the error message is sometime vaguely unrelated to the cause. Something like XYZ library missing, but actually you have to install another library. Even once you succeed to compile, there is no guarantee that it will work and worst yet, there is no guarantee you can uninstall it. This is what has happened to me when I had the bad idea of trying to compile the latest Ekiga 3.2.5. I contacted the dev team directly in the Ekiga mailing list and even them are clueless.

In the case of Firefox 3.5, wait may be a few more weeks and the version 3.5 will be available in the Ubuntu repository you will get it automatically. Even if you can get FF 3.5 by compiling now, is there any guarantee that it won't conflict with the "regular" Firefox which is maintained by Ubuntu auto update? Meaning, will it confuse Ububtu auto-update so that it can no longer update Firefox?

---

### Post by jerome1232 on 2009-07-17
> **UranUtan said:**
> 
- Donwload a *.deb package and install using sudo dpkg -i nameOfProgram.deb

Or you know double click the downloaded .deb ;)

Also 3.5 is in intrepid repositories (as has been pointed out a few posts ago), it's firefox-3.5 you can search for it in synaptic (System - Administration - Synaptic Package Manager) just start typing firefox-3.5 and look for it, then mark it for installation, it will be branded as Shiretoko Web Browser.

---

### Post by bodhi.zazen on 2009-07-17
As CatKiller indicated, you should user the repositories.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

IMO I prefer to teach new users synaptic

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

Firefox 3.5 is here :

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

