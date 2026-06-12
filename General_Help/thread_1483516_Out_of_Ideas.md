---
title: "Out of Ideas"
date: 2010-05-14
forum: General Help
---

### Post by Bob-Elliot on 2010-05-14
I'm new to Ubuntu and these forums, but I cannot think of another way to find an answer, as the only things I can think of searching for are too general or too specific.

First of all, I'm new to these forums. Educate me in how to best use them. Second of all, I have a problem I can't figure out how to fix (any problems up to this point I would search and figure out on my own). I'm unsure of the terminology, so please bear with me. I've got 10.04 running.

Whenever I try to install packages through the software sources gui, add a source, click close, reload, a progress bar pops for a few seconds and then it closes. This is what it would look like normally, but recently it always goes to the same amount of packages, even if I have nothing selected. I guessed that this was due to one thing or another that I added and didn't work, so I got rid of everything. However, even with nothing selected, the progress bar zips through 30 or so files. Is there anything I can do?

As I said, I'm new to this, but I have a basic understanding of the terminal and stuff. Please help me become better.

---

### Post by darolu on 2010-05-14
Hey, welcome to the forums, the best way to ask is not being affraid to do so, just ask, no one is going to point at you and laugh or treat you with disrespect, well at least I have never seen such behaviour within the Ubuntu community.

It is always good to include all the information you can (that you think is related to your problem that is), including your hardware specs is always good and always describe what you have done, what do you want to happen and what happens instead of what you want.

I don't know if I got you right but seems that you're just updating your software list. When you reload the software list, it updates its repositories lists (software sources), so it is normal that you always see the same number of packages listed, it re-counts the software available, adds or remove new ones if necessary (from the list, not from your actual computer).

Remember, selecting packages won't install or uninstall them right away, you always need to enter your admin password in, in order to install or uninstall a package and it will always show you what it (the software centre) is doing.

If you like, you can run this command in your terminal (it is easy, you'll be loving the terminal in no time), you can find it at Applications -> Accessories -> Terminal:
```
$ sudo apt-get update
```
It will update your software sources and print an error if present. If it does find one, post it here.

---

### Post by Bob-Elliot on 2010-05-14
I don't have the ability to try the code (away from home), so here's my story about my problem.

Alright, thanks for the pointers. Concerning the computer, I'm not entirely sure the specs, but it is a Toshiba satellite that I got for cheap from a friend that couldn't get it to work. I bought it and fixed it with Ubuntu 'cause I wanted to try it out, and so far I have enjoyed it. However, I've recently tried installing Wine to play the games I play on my desktop on it. That is where my troubles began: I got Wine working using the package download method (as well as another program; I think it was Chrome). Because I installed these things without problems, my hunch is that the problem is not the computer.
Anyway, the specific program I was trying to get working was LotRO, which I was following [this guide]("http://lorebook.lotro.com/wiki/LOTRO_under_Linux_and_Mac_OS/X") on how to do that, but when I got to the launcher install I would add the appropriate package and it would go through, say about 80% of the files had some problem or another, install the 20%, and then go on. I thought that maybe retrying would work, so I added the package again. This all happened about a month or two ago. I thought, "no problem. I'll just deal with not playing on the laptop." Just today, I've decided to not let this challenge stand. However, somewhere in my clumsy attempts I messed up one of the dll's used in Wine, so I tried to reinstall. I managed to uninstall, and then tried downloading Wine as a package (like I did the first time). However, even with no other package checked, there are the same 80% or so files not installing. I could ignore this if that was all, but the 4 files (number by which checking/unchecking the Wine package changes the amount of files to download) aren't downloading. I've done all I could to make the package manager not look at any packages in an attempt to fix this, but nothing I've done has changed this. I looked for another way to install Wine, and found it (not at the laptop currently, or would describe it better). However, I fear in my uninstallation I got rid of too much (it's not creating a C: drive with the basic parts of windows anymore), so I was hoping installing it by package would help fix this problem. So, my problem is really twofold: I can't get Wine working right, and my package management screen seems to be having problems.
Thanks for the kind welcome. I hope my story above has enough details, but ask a specific question and I'll try to answer it (I work better with specifics than general). I also want to be a better part of the Ubuntu community, so if there is any terminology I can improve, I'd be glad to learn how to speak like I've been using this system for more than a few months.

---

### Post by finlost on 2010-05-14
In Synaptic, try reinstalling Wine.  Right click on the Wine package and select "Mark for Reinstallation".  Just a thought....  When you uninstalled Wine, did you do a complete removal?

Pet peeve of mine - Very few seem to search the forums for an answer.  This was recently evidenced with Lucid and more specifically moving the min/max/close buttons from the left to the right.  They just post a new topic.  I prefer to see forum users search first and then ask if they don't find the appropriate answer.

Happy Ubuntu'ing!

---

### Post by WinterRain on 2010-05-15
Or use [http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by gadolinio on 2010-05-15
Hello, and welcome to the Forums.
I'm afraid I don't fully understand what the exact problem is :S
Regarding the reinstallation of  Wine, open Synaptic Package manager (find it in System--> Administration), type "wine" in the search box, select wine from the list, right-click it and select "remove completely". Then you can even remove the folder it has in you home directory: "/home/whatever_your_user_name_is/.wine". That way I think there should be nothing left of the current install. Then back in Synaptic, right-click wine and pick "install".
Regarding LotRO, I've checked the website and found about the ways of installing it; the method of adding sources doesn't mention Lucid Lynx, 10.04. There's a source package called "PyLotRO-0.1.11.tar.bz2" which you can download. It has a readme file with installation instructions. It says: "On Ubuntu you should only need to install python-4suite-xml and python-qt4". You can do that by opening a terminal (Applications--> accesories--> Terminal) and entering
```

sudo apt-get install python-4suite-xml python-qt4

```
Provide you user password when required and follow instructions. (Be aware that the password will not appear, not even like "****", so it will seem like the terminal is not taking your input, but it actually is; you just type it in, and then press enter)

Extract the content of the package you download from the LotRO website, and open a terminal. Type "cd /path_to_the_folder_where_you_extracted_the_package's_content",
and then
```

sudo ./setup.py install

```
or
```

sudo python setup.py install

```

In any case, see the README file yourself.
Well, I hope this helps you... Feel free to reply if you still need assistance.

---

### Post by Bob-Elliot on 2010-05-15
Thanks for the further help. As I said earlier, I am away from home, but as soon as I can I'll try synaptic (wasn't aware of it before) for wine and then using the source for LotRO. I also appreciate the admonishing for searching, and how gentle you guys are here. If it makes you feel better, I tried searching, but I didn't know exactly what I was asking and so the results I got didn't help me with my problem. And regarding the step by step instructions, thank you for the time you put into them.

Even if this does give me the functionality I need, and it sounds like it will, I still have the package screen repeatedly trying to install 30 files that just don't work, even when I remove all packages from the list to download. I'm not even sure what the problem is itself, or I would try another search.

---

### Post by gadolinio on 2010-05-15
> **Bob-Elliot said:**
> Thanks for the further help. As I said earlier, I am away from home, but as soon as I can I'll try synaptic (wasn't aware of it before) for wine and then using the source for LotRO. I also appreciate the admonishing for searching, and how gentle you guys are here. If it makes you feel better, I tried searching, but I didn't know exactly what I was asking and so the results I got didn't help me with my problem. And regarding the step by step instructions, thank you for the time you put into them.

Even if this does give me the functionality I need, and it sounds like it will, I still have the package screen repeatedly trying to install 30 files that just don't work, even when I remove all packages from the list to download. I'm not even sure what the problem is itself, or I would try another search.

I don't understand which package screen you're talking about, what packages, when does that screen appear, how do you get to that point, what are you trying to do/install exactly when that 30-files thing happens, how do you remove those packages from the list to download; that information could give a hint on which application you're using when you have that problem. It sounds like the Software Sources update, but I'm not really sure.

---

### Post by Bob-Elliot on 2010-05-15
I apologize, and completely understand your confusion. I realized my descriptive blunder after I was away from any computers for the rest of the day, but I'm home now. I'll attach a screenshot for clarity (if I can figure out how...) but I get there through System--> Administration--> Software Sources--> other software.
The screen shot is after I uncheck all my packages on the screen by clicking the box next to them, click close, click reload, and this is less than a full second of the dialog box being up. This pops up every time, and adding a package (Wine before Synaptic worked) changes the amount of files it goes through, but not the amount of time. I found one forum post while searching for how to install something a month ago that told me to do it this way. Since Synaptic did work, if nobody can figure his out I'll just have something that I never use, but I'd like to be able to fix this.
I tried to answer your questions, but I am not the expert on this; feel free to ask me more questions that you think will narrow down my problem.

---

### Post by hxcobd on 2010-05-15
I have no idea what an "XCF" image is, but it didn't open in my web browser or Ubuntu's image viewer...

I don't understand the problem you're having at all. Rather than explain what Synaptic is doing, you might try to explain WHY it's BAD and what it's PREVENTING you from doing.

As far as Wine goes, I'd try to Complete Remove all WINE-related packages and then reinstall them, possibly after a reboot.

---

### Post by 3rdalbum on 2010-05-15
> **hxcobd said:**
> I have no idea what an "XCF" image is, but it didn't open in my web browser or Ubuntu's image viewer...

It's a GIMP image.

The screenshot shows Ubuntu getting the package list from the repositories. Each repository splits its package list into several different files for various reasons. If you have all the regular Ubuntu repositories enabled you'll have tens of files that it checks on when you're reloading the package list. If you have a few extra repositories, you could conceivably have 100 or more package lists to download.

So, yes what you have described and screenshotted is normal. These aren't packages that it's downloading - only package lists. And if a package list hasn't changed since you last updated, it doesn't download that list but it still reports it as being retrieved.

---

### Post by gadolinio on 2010-05-15
> **3rdalbum said:**
> It's a GIMP image.

The screenshot shows Ubuntu getting the package list from the repositories. Each repository splits its package list into several different files for various reasons. If you have all the regular Ubuntu repositories enabled you'll have tens of files that it checks on when you're reloading the package list. If you have a few extra repositories, you could conceivably have 100 or more package lists to download.

So, yes what you have described and screenshotted is normal. These aren't packages that it's downloading - only package lists. And if a package list hasn't changed since you last updated, it doesn't download that list but it still reports it as being retrieved.

Exactly. There's no real problem there. You can unselect the entry "http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu lucid main" if the error message you get states that the system cannot find that repository. Wine can be installed and used without that, as it is included in ubuntu repositories. Or you might well leave it there.
There are two main and easy ways of installing software in ubuntu: applications--> software center, and System--> Administration--> Synaptic package manager. (the latter is more advanced that the first, but still easy to use). They work like a catalog of available software, where you pick everything you want to install or uninstall, and then click "apply". The system does the rest.
There are other ways which are a bit (or much) more complicated. 
Here's some reading about this:
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware).
Enjoy it! =D

---

