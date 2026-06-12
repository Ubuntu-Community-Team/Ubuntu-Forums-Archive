---
title: "Cannot Remove Broken Packages"
date: 2010-07-06
forum: General Help
---

### Post by Samulus on 2010-07-06
Last night I was installing gbrainy and while it was installing I started a fullscreen game on accident. Fullscreen games cause crashes on my intel integrated graphics (an unrelated issue) and while gbrainy was in the process of installing my computer crashed. So I had to restart. When I restarted I knew I would see broken packages so I did:

sudo dpkg -configure -a and my feedback was:
```
dpkg: dependency problems prevent configuration of mono-runtime:
 mono-runtime depends on mono-gac (= 2.4.4~svn151842-1ubuntu4); however:
  Package mono-gac is not configured yet.
dpkg: error processing mono-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono-posix2.0-cil:
 libmono-posix2.0-cil depends on mono-runtime (>= 2.4); however:
  Package mono-runtime is not configured yet.
dpkg: error processing libmono-posix2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono-addins-gui0.2-cil:
 libmono-addins-gui0.2-cil depends on libmono-posix2.0-cil (>= 2.4); however:
  Package libmono-posix2.0-cil is not configured yet.
dpkg: error processing libmono-addins-gui0.2-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gbrainy:
 gbrainy depends on mono-runtime (>= 1.1.8.1); however:
  Package mono-runtime is not configured yet.
 gbrainy depends on libmono-addins-gui0.2-cil (>= 0.4); however:
  Package libmono-addins-gui0.2-cil is not configured yet.
 gbrainy depends on libmono-posix2.0-cil (>= 2.4); however:
  Package libmono-posix2.0-cil is not configured yet.
dpkg: error processing gbrainy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono-corlib2.0-cil:
 libmono-corlib2.0-cil depends on mono-runtime (>= 2.4.4~svn151842); however:
  Package mono-runtime is not configured yet.
 libmono-corlib2.0-cil depends on mono-runtime (<< 2.4.4~svn151843); however:
  Package mono-runtime is not configured yet.
dpkg: error processing libmono-corlib2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2.0-cil:
 libgtk2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
dpkg: error processing libgtk2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libart2.0-cil:
 libart2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
dpkg: error processing libart2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgconf2.0-cil:
 libgconf2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
dpkg: error processing libgconf2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblaunchpad-integration1.0-cil:
 liblaunchpad-integration1.0-cil depends on libgtk2.0-cil (>= 2.12.9); however:
  Package libgtk2.0-cil is not configured yet.
 liblaunchpad-integration1.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
dpkg: error processing liblaunchpad-integration1.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono-addins0.2-cil:
 libmono-addins0.2-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
dpkg: error processing libmono-addins0.2-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2.24-cil:
 libgnome2.24-cil depends on libart2.0-cil (>= 2.24.0); however:
  Package libart2.0-cil is not configured yet.
 libgnome2.24-cil depends on libgconf2.0-cil (>= 2.24.0); however:
  Package libgconf2.0-cil is not configured yet.
 libgnome2.24-cil depends on libgtk2.0-cil (>= 2.12.9); however:
  Package libgtk2.0-cil is not configured yet.
 libgnome2.24-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
dpkg: error processing libgnome2.24-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libglade2.0-cil:
 libglade2.0-cil depends on libgtk2.0-cil (>= 2.12.9); however:
  Package libgtk2.0-cil is not configured yet.
 libglade2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
dpkg: error processing libglade2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono-cairo2.0-cil:
 libmono-cairo2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
dpkg: error processing libmono-cairo2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono-i18n-west2.0-cil:
 libmono-i18n-west2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
dpkg: error processing libmono-i18n-west2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-vfs2.0-cil:
 libgnome-vfs2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
dpkg: error processing libgnome-vfs2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libglib2.0-cil:
 libglib2.0-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
dpkg: error processing libglib2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono-sharpzip2.84-cil:
 libmono-sharpzip2.84-cil depends on libmono-corlib2.0-cil (>= 1.2.2.1); however:
  Package libmono-corlib2.0-cil is not configured yet.
dpkg: error processing libmono-sharpzip2.84-cil (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mono-runtime
 libmono-posix2.0-cil
 libmono-addins-gui0.2-cil
 gbrainy
 libmono-corlib2.0-cil
 libgtk2.0-cil
 libart2.0-cil
 libgconf2.0-cil
 liblaunchpad-integration1.0-cil
 libmono-addins0.2-cil
 libgnome2.24-cil
 libglade2.0-cil
 libmono-cairo2.0-cil
 libmono-i18n-west2.0-cil
 libgnome-vfs2.0-cil
 libglib2.0-cil
 libmono-sharpzip2.84-cil
```
I've tried just about everything to resolve the broken packages but I can't fix them. Does anyone have any idea what I can do to fix this?

---

### Post by StuartN on 2010-07-07
> **Samulus said:**
> When I restarted I knew I would see broken packages so I did:

sudo dpkg -configure -a and my feedback was:
```
dpkg: dependency problems prevent configuration of mono-runtime
```


Entirely at your own risk, you could delete the relevant info files for the corrupt package, so it can be overwritten with a fresh install.

```
sudo rm /var/lib/dpkg/info/mono-runtime*
```

---

### Post by jimmers on 2010-07-07
You could try this tutorial :-

  	 	 	 	 	 	  [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG] **HOWTO: Cleaning up all those unnecessary junk files...** 
   	**Hello 	everyone! So, do you ever get the feeling that your system is being 	flooded with a bunch of junk files that you can't get rid of? I know 	I do. Well, I'm going to show you a few ways to get rid of most, if 	not all, of those annoying junk files.**  	

[COLOR=#ff0000]**Please note**[/COLOR] : If doing 	any of this messes up your system, don't blame me. Everything worked 	flawlessly on my machine. Everthing should be beer 'n skittles for 	you if you follow this HOWTO step-by-step. Good luck! 

================================================== 	================================================== 	====================

[SIZE=3]_**Tip #1 - Getting rid 	of Residual Config packages**_[/SIZE] - In Synaptic Package 	Manger, there is a built-in feature that gets rid of old Residual 	Config packages. Residual Config packages are usually dependency 	packages that are left behind after you uninstall a package from 	your machine. To use this feature, go to **System > 	Administration > Synaptic Package Manager**. On the bottom left 	hand corner of the window, click the **Status** button. In the 	list above the **Sections**, **Status**, **Search**, and 	**Custom **buttons, you should see the following text:
 	 	Quote:
 	 		 			 			 				 					Installed
Installed (local or 					obsolete)
Not installed
Residual config  					
 				 			 		 	 	 	Click on the "Residual config" text. (If the "Residual 	config dialogue does not appear, that means you do not have any 	Residual Config packages on your machine and you can skip down to 	Tip #2.) Do you see the packages that popped up in the window on the 	right? Those are the Residual Config packages. To get rid of these 	pests, click on the box to the left of the package name and select 	"Mark for Complete Removal". After you have done that for 	all of the Residual Config packages, look at the top of the Synaptic 	Package Manger window. Do you see the green check mark with the text 	"Apply" right under it? Click that button, and you'll 	flush all those Residual Config packages down the toilet! 

================================================== 	================================================== 	====================

[SIZE=3]_**Tip #2 - Getting rid 	of partial packages**_[/SIZE] - This is yet another built-in 	feature, but this time it is not used in Synaptic Package Manager. 	It is used in the Terminal. To access the Terminal, go to 	**Applications > Accessories > Terminal**. Now, in the 	Terminal, key in the following command (or you can just copy and 	paste from here):
 	 	Code:
 	sudo apt-get autoclean 	Enter your password when prompted and press **Enter**. See the 	package names that appeared in the Terminal? Those were partial 	packages that have just been deleted. Say goodbye! That's it! This 	command deletes the not-so-fully-downloaded packages that you 	acquire when a package that is being downloaded is suddenly 	cancelled. This is my favorite little trick when it comes to getting 	rid of junk files.  	

================================================== 	================================================== 	====================

[SIZE=3]_**Tip #3 - Getting rid 	of unnecessary locale data**_[/SIZE] - For this tip, you need 	to download the "localepurge" package found in Synaptic 	Package Manager. "localepurge" is just a simple script to 	recover diskspace wasted for unneeded locale files and localized man 	pages. It will automagically be invoked upon completion of any apt 	installation run.

To open Synaptic Package Manager, follow 	the instructions in Tip #1. After opening up Synaptic Package 	Manager, click the **Sections** button on the bottom left hand 	corner of the window, if it is not already clicked. Next, at the top 	of the Synaptic Package Manager window, click the **Search** 	button. In the search window, key in the following text :
 	 	Quote:
 	 		 			 			 				 					localepurge  					
 				 			 		 	 	 	Did the "localepurge" package popup in the package window? 	It probably did, unless you do not have the correct Repositories. 	Now, click on the box next to the "localepurge" package 	name. Click on **Mark for Installation**. Now click the **Apply** 	button at the top of the window and wait for the downloading and 	installing of the "localepurge" package to finish. Once it 	is done, a new window should popup that has a bunch of abbreviations 	on it. for example:  	
 	 	Quote:
 	 		 			 			 				 					en
fr
po
sp
ka
etc...  					
 				 			 		 	 	 	You want to select the abbreviation of the language that you speak, 	or use with Ubuntu, ignoring the capitalized ones. For example, I 	speak english, so I would select the "en" abbreviation. A 	french speaker would select the "fr" abbreviation. So on 	and so forth... Then click next. All done! 

================================================== 	================================================== 	====================

[SIZE=3]_**Tip #4 - Getting rid 	of "orphaned" packages**_[/SIZE] - For this tip, you 	need to download the "deborphan" package found in Synaptic 	Package Manager. "deborphan" finds "orphaned" 	packages on your system. It determines which packages have no other 	packages depending on their installation, and shows you a list of 	these packages. It is most useful when finding libraries, but it can 	be used on packages in all sections...

To open Synaptic 	Package Manager, follow the instructions in Tip #1. After opening up 	Synaptic Package Manager, click the **Sections** button on the 	bottom left hand corner of the window, if it is not already clicked. 	Next, at the top of the Synaptic Package Manager window, click the 	**Search** button. In the search window, key in the following 	text :
 	 	Quote:
 	 		 			 			 				 					deborphan  					
 				 			 		 	 	 	Did the "deborphan" package popup in the package window? 	It probably did, unless you do not have the correct Repositories. 	Now, click on the box next to the "deborphan" package 	name. Click on **Mark for Installation**. Now click the **Apply** 	button at the top of the window and wait for the downloading and 	installing of the "deborphan" package to finish. Once that 	is done, open up the Terminal. Instructions for doing that are 	located in Tip #2. After you have gotten the Terminal open, key in 	the following command (or copy and paste from here):
 	 	Code:
 	sudo deborphan | xargs sudo apt-get -y remove --purge 	Enter your password when prompted and press **Enter**. See the 	package names that appeared in the Terminal? Those were orphaned 	packages that have just been deleted. Say goodbye! This is my second 	favorite way of dealing with junk files. 

================================================== 	================================================== 	====================

[SIZE=3]_**Tip #5 - Adding a 	"Find orphaned packages" to Synaptic Package Manager**_[/SIZE] 	- This is not really much of a tip on how to get rid of junk files. 	It's more like adding a "deborphan" shortcut to Synaptic 	Package Manager so that you don't have to use the Terminal to find 	"orphaned" packages.

[COLOR=#ff0000]**Please 	note:**[/COLOR] You must have the "deborphan" package 	installed or else this will not work.

To start this out, open 	up Synaptic Package Manager with the instructions from Tip #1. Now, 	at the top of the Synaptic Package Manager window, click the 	**Settings** button, followed by the **Filters** button. In 	the Filters window, on the bottom left hand corner, push the **New** 	button. You can name the new Filter if you like, but it is not 	necessary. I named mine "Orphaned". With your new Filter 	selected, in the "Status" tab on the right, click the 	**Deselect All** button. Next, check the "Orphaned" 	option under the "Other" category. Then click the **OK** 	button.

To use this new filter, click the **Custom** 	button on the bottom left hand corner of the Synaptic Package 	Manager window. You should see the following text, or something 	similiar :
 	 	Quote:
 	 		 			 			 				 					Broken
Marked Changes
(Whatever you 					named your "deborphan" Filter)
Package with 					Debconf
Search Filter  					
 				 			 		 	 	 	Click on the "(Whatever you named your "deborphan Filter)" 	text. Do you see the packages that popped up in the window on the 	right? Those are the "orphaned" packages. To get rid of 	these buggers, click on the box to the left of the package name and 	select "Mark for Complete Removal". After you have done 	that for all of the "orphaned" packages, look at the top 	of the Synaptic Package Manger window. Do you see the green check 	mark with the text "Apply" right under it? Click that 	button, and you'll get rid of all the "orphaned" packages 	forever (Probably)!  	

================================================== 	================================================== 	====================

Well, I hope all of you enjoyed my HOWTO 	and found it quite easy to follow. Whew, this thing took me over an 	hour to make! LOL! If I have made any mistakes, just let me know. 	Catch you later! 


Luck


Jimmers

 
 Linux User     516269
Ubuntu User   31738

---

### Post by Samulus on 2010-07-07
Thanks for the help guys but I managed to fix it late last night. I basically did what StuartN said, navigate to /var/lib/dpkg/status and find each and every package causing the issue and remove the info about it. Then I reinstalled the package that was causing trouble along with all it's dependencies and it overwrote the half packages causing trouble. Thanks again though.

---

