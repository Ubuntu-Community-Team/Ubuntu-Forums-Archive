---
title: "CCleaner for Ubuntu"
date: 2010-04-18
forum: General Help
---

### Post by ubun2warrior on 2010-04-18
Hi 

I use Ccleaner in windows an excellent app to clean my computer. It removes system cache, internet cache, registry cche, etc. Is there any ubuntu equivalent ??

---

### Post by ubername on 2010-04-18
Try bleachbit from the repo's

---

### Post by wilee-nilee on 2010-04-18
> **ubername said:**
> Try bleachbit from the repo's

Good program, but be careful. 

Linux doesn't have the same inherent over-saving of temps...etc that MS does. A good way of cleaning the cache and your computer in general are two different terminal commands.
sudo apt-get autoremove
sudo apt-get autoclean

I use ubuntu tweak generally to remove cache and deleted program dependents.

---

### Post by coffeecat on 2010-04-18
> **ubun2warrior said:**
>  registry cche, etc. 

And Linux doesn't have a registry.

---

### Post by 3rdalbum on 2010-04-18
> **ubun2warrior said:**
> Hi 

I use Ccleaner in windows an excellent app to clean my computer. It removes system cache, internet cache, registry cche, etc. Is there any ubuntu equivalent ??

You don't really need one. All the various caches that I can think of on Linux are either needed to drastically speed up certain programs, or are deleted on shutdown anyway.

Internet cache is limited to 50mb, and the oldest things in the cache will be replaced by the newest things when you hit the limit.

And there's no registry.

---

### Post by hawthornso23 on 2010-04-18
Ccleaner and ilk are solutions to windows problems that linux doesn't have ( - not saying linux is problem free - just that the problems and solutions are different.) Recommend you hold your fire and wait to see what issues you have with linux before rushing to install solutions to problems you probably don't have. I've never needed any kind of `cleaner' in linux. Mostly it doesn't get cluttered. What minimal clutter might arise gets cleared out infrequently whenever I upgrade to a new version.

---

### Post by jimmers on 2010-04-18
Ubun2warrior,
Hi, heed the the wise words of the forum, but if you need to put your mind at rest,
try this HowTo from an earlier Post.
                                 [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG] **HOWTO: Cleaning up all those unnecessary junk files...** 
       **Hello     everyone! So, do you ever get the feeling that your system is being     flooded with a bunch of junk files that you can't get rid of? I know     I do. Well, I'm going to show you a few ways to get rid of most, if     not all, of those annoying junk files.**           

[COLOR=#ff0000]**Please note**[/COLOR] : If doing     any of this messes up your system, don't blame me. Everything worked     flawlessly on my machine. Everthing should be beer 'n skittles for     you if you follow this HOWTO step-by-step. Good luck!         

==================================================     ==================================================     ====================

[SIZE=3]_**Tip #1 - Getting rid     of Residual Config packages**_[/SIZE] - In Synaptic Package     Manger, there is a built-in feature that gets rid of old Residual     Config packages. Residual Config packages are usually dependency     packages that are left behind after you uninstall a package from     your machine. To use this feature, go to **System >     Administration > Synaptic Package Manager**. On the bottom left     hand corner of the window, click the **Status** button. In the     list above the **Sections**, **Status**, **Search**, and     **Custom **buttons, you should see the following text:
          Quote:
                                                                              Installed
Installed (local or                     obsolete)
Not installed
Residual config                      
                                                      Click on the "Residual config" text. (If the "Residual     config dialogue does not appear, that means you do not have any     Residual Config packages on your machine and you can skip down to     Tip #2.) Do you see the packages that popped up in the window on the     right? Those are the Residual Config packages. To get rid of these     pests, click on the box to the left of the package name and select     "Mark for Complete Removal". After you have done that for     all of the Residual Config packages, look at the top of the Synaptic     Package Manger window. Do you see the green check mark with the text     "Apply" right under it? Click that button, and you'll     flush all those Residual Config packages down the toilet!         

==================================================     ==================================================     ====================

[SIZE=3]_**Tip #2 - Getting rid     of partial packages**_[/SIZE] - This is yet another built-in     feature, but this time it is not used in Synaptic Package Manager.     It is used in the Terminal. To access the Terminal, go to     **Applications > Accessories > Terminal**. Now, in the     Terminal, key in the following command (or you can just copy and     paste from here):
          Code:
     sudo apt-get autoclean     Enter your password when prompted and press **Enter**. See the     package names that appeared in the Terminal? Those were partial     packages that have just been deleted. Say goodbye! That's it! This     command deletes the not-so-fully-downloaded packages that you     acquire when a package that is being downloaded is suddenly     cancelled. This is my favorite little trick when it comes to getting     rid of junk files.           

==================================================     ==================================================     ====================

[SIZE=3]_**Tip #3 - Getting rid     of unnecessary locale data**_[/SIZE] - For this tip, you need     to download the "localepurge" package found in Synaptic     Package Manager. "localepurge" is just a simple script to     recover diskspace wasted for unneeded locale files and localized man     pages. It will automagically be invoked upon completion of any apt     installation run.

To open Synaptic Package Manager, follow     the instructions in Tip #1. After opening up Synaptic Package     Manager, click the **Sections** button on the bottom left hand     corner of the window, if it is not already clicked. Next, at the top     of the Synaptic Package Manager window, click the **Search**     button. In the search window, key in the following text :
          Quote:
                                                                              localepurge                      
                                                      Did the "localepurge" package popup in the package window?     It probably did, unless you do not have the correct Repositories.     Now, click on the box next to the "localepurge" package     name. Click on **Mark for Installation**. Now click the **Apply**     button at the top of the window and wait for the downloading and     installing of the "localepurge" package to finish. Once it     is done, a new window should popup that has a bunch of abbreviations     on it. for example:      
          Quote:
                                                                              en
fr
po
sp
ka
etc...                      
                                                      You want to select the abbreviation of the language that you speak,     or use with Ubuntu, ignoring the capitalized ones. For example, I     speak english, so I would select the "en" abbreviation. A     french speaker would select the "fr" abbreviation. So on     and so forth... Then click next. All done!         

==================================================     ==================================================     ====================

[SIZE=3]_**Tip #4 - Getting rid     of "orphaned" packages**_[/SIZE] - For this tip, you     need to download the "deborphan" package found in Synaptic     Package Manager. "deborphan" finds "orphaned"     packages on your system. It determines which packages have no other     packages depending on their installation, and shows you a list of     these packages. It is most useful when finding libraries, but it can     be used on packages in all sections...

To open Synaptic     Package Manager, follow the instructions in Tip #1. After opening up     Synaptic Package Manager, click the **Sections** button on the     bottom left hand corner of the window, if it is not already clicked.     Next, at the top of the Synaptic Package Manager window, click the     **Search** button. In the search window, key in the following     text :
          Quote:
                                                                              deborphan                      
                                                      Did the "deborphan" package popup in the package window?     It probably did, unless you do not have the correct Repositories.     Now, click on the box next to the "deborphan" package     name. Click on **Mark for Installation**. Now click the **Apply**     button at the top of the window and wait for the downloading and     installing of the "deborphan" package to finish. Once that     is done, open up the Terminal. Instructions for doing that are     located in Tip #2. After you have gotten the Terminal open, key in     the following command (or copy and paste from here):
          Code:
     sudo deborphan | xargs sudo apt-get -y remove --purge     Enter your password when prompted and press **Enter**. See the     package names that appeared in the Terminal? Those were orphaned     packages that have just been deleted. Say goodbye! This is my second     favorite way of dealing with junk files.         

==================================================     ==================================================     ====================

[SIZE=3]_**Tip #5 - Adding a     "Find orphaned packages" to Synaptic Package Manager**_[/SIZE]     - This is not really much of a tip on how to get rid of junk files.     It's more like adding a "deborphan" shortcut to Synaptic     Package Manager so that you don't have to use the Terminal to find     "orphaned" packages.

[COLOR=#ff0000]**Please     note:**[/COLOR] You must have the "deborphan" package     installed or else this will not work.

To start this out, open     up Synaptic Package Manager with the instructions from Tip #1. Now,     at the top of the Synaptic Package Manager window, click the     **Settings** button, followed by the **Filters** button. In     the Filters window, on the bottom left hand corner, push the **New**     button. You can name the new Filter if you like, but it is not     necessary. I named mine "Orphaned". With your new Filter     selected, in the "Status" tab on the right, click the     **Deselect All** button. Next, check the "Orphaned"     option under the "Other" category. Then click the **OK**     button.

To use this new filter, click the **Custom**     button on the bottom left hand corner of the Synaptic Package     Manager window. You should see the following text, or something     similiar :
          Quote:
                                                                              Broken
Marked Changes
(Whatever you                     named your "deborphan" Filter)
Package with                     Debconf
Search Filter                      
                                                      Click on the "(Whatever you named your "deborphan Filter)"     text. Do you see the packages that popped up in the window on the     right? Those are the "orphaned" packages. To get rid of     these buggers, click on the box to the left of the package name and     select "Mark for Complete Removal". After you have done     that for all of the "orphaned" packages, look at the top     of the Synaptic Package Manger window. Do you see the green check     mark with the text "Apply" right under it? Click that     button, and you'll get rid of all the "orphaned" packages     forever (Probably)!           

==================================================     ==================================================     ====================

Well, I hope all of you enjoyed my HOWTO     and found it quite easy to follow. Whew, this thing took me over an     hour to make! LOL! If I have made any mistakes, just let me know.     Catch you later!      
 
 

This in OOo, format if you require MS Office, just shout.


Good Luck

---

### Post by scouser73 on 2010-04-18
Excellent tutorial Jimmers

---

### Post by jimmers on 2010-04-18
Can't take the credit for the tutorial Scouser73, but when in the forum, if there is anything I find interesting and think it would benefit the Community, I save and pass on when necessary.

---

### Post by oldos2er on 2010-04-18
> **jimmers said:**
> 
          Code:
     sudo apt-get autoclean     Enter your password when prompted and press **Enter**. See the     package names that appeared in the Terminal? Those were partial     packages that have just been deleted. Say goodbye! That's it! This     command deletes the not-so-fully-downloaded packages that you     acquire when a package that is being downloaded is suddenly     cancelled. 

 This is incorrect. Here's what "autoclean" actually does: 
           Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.

---

### Post by Mark Phelps on 2010-04-18
I would also caution against using something called Computer Janitor.  While it certainly "cleans" your PC, it can also wipe out lots of useful packages in the process.  I used it by mistake and had to do a reinstall to get a working system back.

---

### Post by howefield on 2010-04-18
> **jimmers said:**
> Can't take the credit for the tutorial Scouser73, but when in the forum, if there is anything I find interesting and think it would benefit the Community, I save and pass on when necessary.

Looks like this one

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by ubun2warrior on 2010-04-30
I feel it is better not to worry about Ccleaner type software for Ubuntu because it works fine by itself and one may delete some important file by mistake.

---

