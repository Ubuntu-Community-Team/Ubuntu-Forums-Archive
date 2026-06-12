---
title: "How to Clean Out the system"
date: 2010-05-13
forum: General Help
---

### Post by theWrkncacnter on 2010-05-13
Hey everyone

I've had ubuntu installed on this computer, and I've updated it all the way up to Lucid from Dapper over the years. I'd like to clean out settings and old programs that might not be needed anymore to make it more like a fresh install, as I've noticed some problems that people with fresh installs don't seem to have.

[LIST]
[*]Two indicators for Empathy
[*]Computer Janitor freezes
[*]Weird system tools and wine entries, etc.
[/LIST]

What are some tips for knowing what I can remove in synaptic, or anything else I can do?
Thanks!

---

### Post by mörgæs on 2010-05-14
It is a waste of time trying to improve or clean such old system. Just do a clean install: One hour, problem solved.

---

### Post by cap10Ibraim on 2010-05-14
> **mörgæs said:**
> It is a waste of time trying to improve or clean such old system. Just do a clean install: One hour, problem solved.
I would do the same thing

---

### Post by jimmers on 2010-05-14
You could try this tutorial, from someone who I have forgotten his name :-
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
                                                      Click on the "Residual config" text. (If the "Residual     config dialogue does not appear, that means you do not have any     Residual Config packages on your machine and you can skip down to     Tip #2.) Do you see the packages that popped up in the window on the     right? Those are the Residual Config packages. To get rid of these     pests, click on the box to the left of the package name and select     "Mark for Complete Removal". After you have done that for     all of the Residual Config packages, look at the top of the Synaptic     Package Manger window. Do you see the green check mark with the text     "Apply" right under it? Click that button, and you'll     flush all those Residual Config packages down the toilet!         :KS

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


Works for me.


Good Luck

---

### Post by Jimtheplanner on 2010-05-14
If you intend to re-install why not give Bleach Bit a try it's in the repos... 

Jim

---

### Post by DAFORZE on 2010-05-14
Well maybe for him it isn't a waste of time since he had it for years since dapper.. and if it didn't matter to him he probably came up with the same answer as you... don't you think..

So does anybody has a real answer for him? 
Because I don't, but it seems to me the answer to this question is going to be very educative about the linux system.

EDIT: oh i see people already have answered the question :P

---

### Post by mörgæs on 2010-05-14
> **DAFORZE said:**
> Well maybe for him it isn't a waste of time since he had it for years since dapper.. and if it didn't matter to him he probably came up with the same answer as you... don't you think..

So does anybody has a real answer for him? 
Because I don't, but it seems to me the answer to this question is going to be very educative about the linux system.

EDIT: oh i see people already have answered the question :P

You take for granted that there actually is a way to remove all obsolete packages, fix all dependencies, reset all wrong configurations and so on and so on to an extent where the 'fixed' system is just at stable and quick as a fresh install. Well, let's hear from original poster when he is through with whatever solution he picks.

---

### Post by (^_^)Smiley on 2010-05-14
Install bleachbit it cleans all history and removes wrong menu entries and much more!

---

### Post by DAFORZE on 2010-05-14
> **mörgæs said:**
> You take for granted that there actually is a way to remove all obsolete packages, fix all dependencies, reset all wrong configurations and so on and so on to an extent where the 'fixed' system is just at stable and quick as a fresh install. Well, let's hear from original poster when he is through with whatever solution he picks.\\

but what about the emotional attachment =;

---

### Post by mörgæs on 2010-05-14
> **DAFORZE said:**
> 
but what about the emotional attachment =;

Sorry, I don't know of that. I am not attached to emotions :-)

---

### Post by theWrkncacnter on 2010-10-21
Hey guys, thanks for all your advice. I ended up "renewing the install" of Maverick -- I kept the /home partition unformatted and installed Maverick fresh on /.

So far it seems like it worked pretty well (although initially it was a mess and nothing worked since the /home/user/ folders didn't belong to the users anymore -- some quick chown work fixed that)

I had made a lot of small tweaks that I wanted to keep, like setting Gmail as the default mail account, adding a "delete" option to the nautillus context menu, and lots of other little things like that. There were so many little improvements made over time, I didn't want to lose them all and not remember what they were.

---

