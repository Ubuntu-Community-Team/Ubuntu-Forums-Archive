---
title: "Thinking of Moving to Ubuntu"
date: 2011-05-27
forum: General Help
---

### Post by tomlam on 2011-05-27
Hi I'm Thinking of moving from windows 7 to ubuntu but wanted to ask a few questions. I would really appreciate your answers.
Thanks in advance.


**DUAL BOOT**
I heard there is away to set the computer to dual boot both windows and ubuntu. This would be a great way to test out ubuntu and see if I like it while keeping windows until i make a decision.
--First of all - is this possible?
--Second - Is there some documentation on how best to do this?
--Third - Will all my files be available on the dual boot installation?
--Final - Can I then migrate from windows to ubuntu or would a system format and reinstall be necessary?


**INSTALLATIONS**
I am fairly savvy with coding and things but I like the wizard style installation processes that windows uses 
-- Do you have to install everything using the command line with ubuntu, or does it come with a simple installation process similar to what i'm used to?


**WORKING WITH CLIENTS**
I need to be able to work with clients who use windows 
-- Would software differences stop me from doing this? For example if they send me word documents, can I even get word on ubuntu - or would the native word document view everything the same?


**WHICH VERSION IS BEST & GNOME3 ?**
There seem to be lots of versions and builds out there 
-- Do people have any preference? Or are there different builds for different jobs? 
-- Finally - I've seen a youtube video of Gnome 3 and think it looks great. I would like to get this, is it a separate install or does it come with some ubuntu builds?
-- Is there an ubuntu build which comes with all the things I will need to get started, instead of me having to go out and get them?


Sorry for all the questions - THanks for your help!

---

### Post by sanderd17 on 2011-05-27
> **tomlam said:**
> Hi I'm Thinking of moving from windows 7 to ubuntu but wanted to ask a few questions. I would really appreciate your answers.
Thanks in advance.


**DUAL BOOT**
I heard there is away to set the computer to dual boot both windows and ubuntu. This would be a great way to test out ubuntu and see if I like it while keeping windows until i make a decision.
--First of all - is this possible?
--Second - Is there some documentation on how best to do this?
--Third - Will all my files be available on the dual boot installation?
--Final - Can I then migrate from windows to ubuntu or would a system format and reinstall be necessary?


Dual boot is the default option when you install ubuntu (if you have enough space left).The files from windows will be visible for Ubuntu (since ubuntu can read the windows NTFS file system) but not the other way around (since windows can not read the Linux ext4 file system)

> 


**INSTALLATIONS**
I am fairly savvy with coding and things but I like the wizard style installation processes that windows uses 
-- Do you have to install everything using the command line with ubuntu, or does it come with a simple installation process similar to what i'm used to?


The ubuntu installation wizard is really good, a lot better than the Windows one.  If you run the wizard in the live CD, you can even surf or do some work while ubuntu is installing. If you just fill in your details and don't mess with the settings, it will do just what you want

> 

**WORKING WITH CLIENTS**
I need to be able to work with clients who use windows 
-- Would software differences stop me from doing this? For example if they send me word documents, can I even get word on ubuntu - or would the native word document view everything the same?



You can instal word via wine (a compatibility layer), but wine does not work as good as native Linux programs. But you can open a word document with the preinstalled Libreoffce writer.

> 
**WHICH VERSION IS BEST & GNOME3 ?**
There seem to be lots of versions and builds out there 
-- Do people have any preference? Or are there different builds for different jobs? 
-- Finally - I've seen a youtube video of Gnome 3 and think it looks great. I would like to get this, is it a separate install or does it come with some ubuntu builds?
-- Is there an ubuntu build which comes with all the things I will need to get started, instead of me having to go out and get them?


Sorry for all the questions - THanks for your help!

Gnome3 is not supported in Ubuntu yet. But you can install it (although I would not recommend installing Gnome3 for a new user, it can break your system since it removes Gnome2).

11.04 has the unity shell as default, I find it rather buggy, but if you think it's ok, that's a personal choice. Ubuntu 11.04 also offers the Gnome2 fallback mode.

If you don't like Gnome, you could also try KDE or LXDE or XFCE or ...

Those can all be installed next to gnome 2, so that you choose at login time.

I have a preference for Mint over Ubuntu, because I find the default themes easier for the eyes (but that's a personal thing).

---

### Post by Thewhistlingwind on 2011-05-27
> **tomlam said:**
> 



--First of all - is this possible?

**YES.**
--Second - Is there some documentation on how best to do this?
**YES.  (**[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)**) Thats old but the process should be pretty much the same.**
--Third - Will all my files be available on the dual boot installation?
**You will be able to access them by mounting your windows partition.**

--Final - Can I then migrate from windows to ubuntu or would a system format and reinstall be necessary?
**You could delete your windows partition then resize it, so ostensibly no, but a reformat may be in your best interest.**

**INSTALLATIONS**
I am fairly savvy with coding and things but I like the wizard style installation processes that windows uses 
-- Do you have to install everything using the command line with ubuntu, or does it come with a simple installation process similar to what i'm used to?

**It depends, if it's in the repositories, it's one button install, if it's in a tarball, you have to compile, which is easier then it sounds, but harder then it should be.**



**WORKING WITH CLIENTS**
I need to be able to work with clients who use windows 
-- Would software differences stop me from doing this? For example if they send me word documents, can I even get word on ubuntu - or would the native word document view everything the same?

**You can try openoffice/Libreoffice now by installing it in windows if it suits you.**

**Once again, it depends on what your trying to do, Linux cannot run windows binaries, the systems are incompatible.**

**WHICH VERSION IS BEST & GNOME3 ?**
There seem to be lots of versions and builds out there 
-- Do people have any preference? Or are there different builds for different jobs?

**Generally theres different builds for different jobs.** 
-- Finally - I've seen a youtube video of Gnome 3 and think it looks great. I would like to get this, is it a separate install or does it come with some ubuntu builds?

**Ubuntu does not currently support gnome 3**.
-- Is there an ubuntu build which comes with all the things I will need to get started, instead of me having to go out and get them?

**Not if you want gnome 3. I think the mini ISO might let you install it, but besides that the DE is unity.**


Sorry for all the questions - THanks for your help!

Good luck.

EDIT: As a note, that's because the mini ISO is a pure command line install, theres no gnome2 to break.

---

### Post by Frogs Hair on 2011-05-27
1. I and many others dual boot . [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

2. The software center makes it easy to install programs via the GUI and there lists equivalent programs available on the web. Some programs will not be a perfect alternative to windows software.

3. It is possible to set up a data partition making files available to both operating systems . More experienced users could help with that . 

4.I use Ubuntu at home but there are people that use it for work and could better answer work productivity  questions. 

5. If I were using Ubuntu at work I would use a long term support release like 10.04 . Both the Gnome 3 and Unity desktops are very new and need time to mature. A stable version of Gnome 3 is not available on Ubuntu yet.

---

### Post by TBABill on 2011-05-27
Since the questions have been answered sufficiently, one thing that may help you as a new user is to search for distro reviews. There are tons of them and Ubuntu is reviewed by the dozens at each release. If you go to [www.distrowatch.com]("http://www.distrowatch.com") and go to the Ubuntu page, there is a section with the Ubuntu home page URL, forums link, and within all those links are ones that go to reviews on various webpages. Reviews are great when you just want to see screenshots of the system, including the installation process, or you just want to learn a few things from various perspectives. It also helps with understanding the language of desktop environments, package management, drivers, etc. if the author happens to touch on those points.
 
Another great resource can be websites devoted to Ubuntu, such as OMG Ubuntu. There are many and there are many Ubuntu forums as well so you can get a lot of help from reading and asking.
 
Good luck with whatever you choose!

---

### Post by tomlam on 2011-06-10
Hello, Thanks for all your wonderful comments.

I am currently downloading Mint. What I'm looking for us a very interface drivern OS, which will allow me to work very quickly and efficiently. I like things like being able to quickly snap windows to the sidebar, and often have lots of windows open, so easy management of that would be nice.
**-> Do you think mint is right for me?**


Since I'm so new to Linux is there anything that you can suggest that I will need to do upon my first installation to get it running how I want it? I can imagine for a first time user its not completely set up how I'd want it.

Also is it easy to switch between gnome 2, gnome 3, and other desktop interfaces after installation is done?
I understand that not all of them will work with Mint - is that right?

Thanks again.
Tom

---

### Post by sanderd17 on 2011-06-10
> **tomlam said:**
> Hello, Thanks for all your wonderful comments.

I am currently downloading Mint. What I'm looking for us a very interface drivern OS, which will allow me to work very quickly and efficiently. I like things like being able to quickly snap windows to the sidebar, and often have lots of windows open, so easy management of that would be nice.
**-> Do you think mint is right for me?**


Since I'm so new to Linux is there anything that you can suggest that I will need to do upon my first installation to get it running how I want it? I can imagine for a first time user its not completely set up how I'd want it.

Also is it easy to switch between gnome 2, gnome 3, and other desktop interfaces after installation is done?
I understand that not all of them will work with Mint - is that right?

Thanks again.
Tom

Mint is a good distro. Maybe some things you should know: 

[LIST]
[*]Don't be afraid of error messages, most of the time they contain a tip about how to solve it, in the other cases, just google the message
[*]don't be afraid of the command line, most users give explanation in commands because that doesn't change
[*]First look in the software center before you install anything, almost things you find on the web is crap anyway (new and unstable or old and broken) all good working software is in the software center.
[/LIST]

Gnome 3 will not work without breaking gnome2, all others will work (KDE, XFCE, LXDE ...)

---

### Post by tomlam on 2011-06-10
Thanks - very wise words. I am a little bit worried that I wont understand all the commands to type in, but I think I'll get over that if I create myself a help document to store them in.

Something I am more concerned about is the software that won't be available. Such as photoshop! I know there are alternatives, but what about if someone sends me a PSD file. This is a huge part of my work.

Does wine slow photoshop down to a halt?
My laptop is fairly good - good enough to run windows 7.

---

### Post by el_koraco on 2011-06-10
> **tomlam said:**
> 
Since I'm so new to Linux is there anything that you can suggest that I will need to do upon my first installation to get it running how I want it? I can imagine for a first time user its not completely set up how I'd want it.


Mint comes with all the codecs you need to run all multimedia related stuff, even with the Windows fonts, so you probably won't have to do much tweaking to get things in order. Open the Software Manager in the menu, and have a looksee at all the applications you can install. Other than that, a lot of stuff runs like in Windows, e.g. right clicking the desktop gives you a set of options, so does right clicking the taskbar, etc. Don't try to do too much right away, just have some fun exploring.

---

### Post by sanderd17 on 2011-06-10
> **tomlam said:**
> 
Something I am more concerned about is the software that won't be available. Such as photoshop! I know there are alternatives, but what about if someone sends me a PSD file. This is a huge part of my work.

Does wine slow photoshop down to a halt?
My laptop is fairly good - good enough to run windows 7.

Gimp (the photoshop alternative in the software center) can open PSD files. But Photoshop seems to run in Wine [http://appdb.winehq.org/appview.php?appId=17](http://appdb.winehq.org/appview.php?appId=17)

Platinum means it installs without major tweaks and runs fine. Gold means you need to do some tweaks to get it running. Silver means that you CAN get it running. Read the comments on the wine DB.

Once something runs in Wine, it isn't that much slower than native (though it looks ugly because it doesn't follow the system themes).

---

### Post by idoitprone on 2011-06-10
please remember, linux is not windows
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Do not come in with certain expectations on how to do things. It will make your life easier. From your first post, I believe you thought you are force to use the commandline. ubuntu is as clickly click click distro it can be

---

