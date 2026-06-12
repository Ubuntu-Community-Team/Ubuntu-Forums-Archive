---
title: "Any difference between Ubuntu Software Center and Synaptic Package Manager?"
date: 2010-08-06
forum: General Help
---

### Post by fterh on 2010-08-06
As the title goes. I searched for this and found out that they are the same, just that USC is Windows-users-centric while SPM is more advanced but preferred. True?

---

### Post by utilitytrack on 2010-08-06
What is it? I know [FONT="Courier New"]aptitude[/FONT] only :)

---

### Post by inameiname on 2010-08-06
They are different. Both are GUIs instead of upgrading and installing through the terminal, such as using aptitude and apt-get. Both will allow you to search for updates and new programs, with Synaptic being far more fancy and advanced. However, Software Center is becoming very cool after the most recent updates (through a PPA repo). Software Center is definitely easier to figure out for a novice. Personally I never use Synaptic, as I'm a terminal man. But for those rare times I seek out new software, Software Center is easier to find and install. Overall, I think for a lot of us who have used Ubuntu for a while, a combination of the two would be ideal someday. In general, both will get the job done for searching for applications, installation of any, removal too, and whatever else you desire.

---

### Post by clhsharky on 2010-08-06
> USC is Windows-users-centric while SPM is more advanced but preferred. True?
True

SynapticPackageManager - GUI with complete package control,very good tool.

Terminal - Fast, complete OS control, real geek tool.

Ubuntu Software Center - Easy, limited control, great for noobs.

---

### Post by fterh on 2010-08-06
> **inameiname said:**
> They are different. Both are GUIs instead of upgrading and installing through the terminal, such as using aptitude and apt-get. Both will allow you to search for updates and new programs, with Synaptic being far more fancy and advanced. However, Software Center is becoming very cool after the most recent updates (through a PPA repo). Software Center is definitely easier to figure out for a novice. Personally I never use Synaptic, as I'm a terminal man. But for those rare times I seek out new software, Software Center is easier to find and install. Overall, I think for a lot of us who have used Ubuntu for a while, a combination of the two would be ideal someday. In general, both will get the job done for searching for applications, installation of any, removal too, and whatever else you desire.
Example i wanted to install Wine. I searched for it on USC and got only 1 result. I searched on SPM and got a lot (1.0, 1.2, 1.0 dev, 1.2 dev, 1.0 gecko, 1.2 gecko, etc.). Why is that?

---

### Post by fterh on 2010-08-06
> **clhsharky said:**
> True

SynapticPackageManager - GUI with complete package control,very good tool.

Terminal - Fast, complete OS control, real geek tool.

Ubuntu Software Center - Easy, limited control, great for noobs.
How do you use Terminal to search for available software packages and install them? Is there a guide somewhere? I like Terminal a lot (really powerful :D)

---

### Post by inameiname on 2010-08-06
Well fterh, I'm afraid I can't really help you in regards to the Synaptic Package Manager throwing up a bunch of different versions for Wine as I never use that application at all. As I said, terminal's always been my thing. My guess is Synaptic pops up all versions available, and you can install any of the stable or unstable versions. For a newbie, best to stick with the version in USC.  Currently with Wine, there are testing versions and stable ones.

As for using the terminal, I don't really search for software that way. I've just searched through Google searches and whatnot for what's best, and if and when I find something that seems worth throwing on, I will 'sudo apt-cache search' for it and see if it's any of the available repositories I have on my system. If not, I just find out where to download it from the application's website, whether it asks to install from there or to add their own repository. 

For a guide, I suggest just doing some Googling. There is ALOT that can be done through the terminal. Oh, and if you do want to use the terminal, best to tweak various shortcuts through the '.bashrc' file in your home folder. You can tweak all sorts of things through it.

---

### Post by sisco311 on 2010-08-07
> **fterh said:**
> Is there a guide somewhere? I like Terminal a lot (really powerful :D)

Check out the community documentation:
[uhelp]community/InstallingSoftware[/uhelp]
[uhelp]community/AptGet/Howto[/uhelp]
[uhelp]community/AptitudeSurvivalGuide[/uhelp]

---

### Post by fterh on 2010-08-07
Thanks for all the input guys :D I think I'll try using Terminal to manage my software packages :) Just curious, is aptitude better than apt-get (I read that it automatically removes software dependencies after installation)? 

And in what way is Terminal aptitude better than SPM?

---

### Post by inameiname on 2010-08-07
No prob. 

I always use the terminal. I have a .bashrc command that I simply can put in the terminal whenever I feel like and it automatically checks for any updates or upgrades that are available and will automatically install them, and when done, will clean up whatever and that's all. I rarely ever open the Update Manager anymore.

Aptitude is better than apt-get. Really, they are pretty much the same, but aptitude can do a bit more for and is better at installing dependencies, as well as removing them, when removing software. Doesn't really matter which is used. 

In a comparison between using the terminal and the SPM, it's hard to say which is truly better. Terminal is pretty much a non-gui way of viewing everything and doing everything in the SPM, whereas the SPM is a gui way of using the terminal. It's what you want to use. If you get really good, you are more free to do much more through a terminal than through Synaptic, as you are bound by the limitations of it's programming and what it can do.

As to what is a GUI- "GUI is an acronym for "graphical user interface", such as Mac   OS, Mac OS X, Microsoft Windows, and the X   Window System.  A GUI lets you interact with your computer   using pictures and symbols, rather than having to memorize many   complicated commands and type them precisely, as with a command-line   interface such as DOS.  Most computer users today become familiar   with using GUIs before using any other type of interface."

---

### Post by neoargon on 2010-08-07
> **fterh said:**
> Thanks for all the input guys :D I think I'll try using Terminal to manage my software packages :) Just curious, is aptitude better than apt-get (I read that it automatically removes software dependencies after installation)? 

And in what way is Terminal aptitude better than SPM?

Unless you are already familiar with terminal , it would be difficult for you to use it . Synaptic is enough . Terminal is fast only if you can type fast . You will need to spend a lot of time to study a terminal application.

---

### Post by inameiname on 2010-08-07
Very true. It's certainly something you gotta do some research with and have a little bit of understanding with linux before going hard and heavy with the terminal. 

Although, when I first installed Ubuntu and used the terminal for the first time, I started with it and only it, as I thought SPM was just too complicated. Of course, I've always liked the terminal, (ie, such as in using dos back in the day), and was sort of used to using it when I was just a wee lad.

---

### Post by neoargon on 2010-08-07
Many people in this forum started using computer in terminal . For such people, terminal is very easy . It's a kind of personal preference thing .

---

### Post by fterh on 2010-08-07
I am from the 1990s so I have practically 0 experience with DOS/terminal. But when I first used the Terminal I loved it, from the sudo commands to pretty much everything. Anyway I think I'll go with SPM for now, Terminal seems a tad too complicated ;)

---

### Post by amite on 2010-08-07
> **fterh said:**
> How do you use Terminal to search for available software packages and install them? Is there a guide somewhere? I like Terminal a lot (really powerful :D)
go through man page of apt-get u will find enough knowledge.i use only apt-get ,it's good and sufficient for all ppurpose.

---

### Post by dryphi on 2011-01-12
I like the look and simplicity of the new Ubuntu Software Center, but to be honest I miss the old Add/Remove Programs thing that had 5-star ratings and showed what everyone else was using.
What happened to that package manager? Can we integrate the two and have USC display ratings and usage statistics for programs?

---

### Post by inameiname on 2011-01-15
It will have ratings very soon.

[http://www.ubuntuvibes.com/2010/11/ubuntu-software-center-in-1104-to-add.html](http://www.ubuntuvibes.com/2010/11/ubuntu-software-center-in-1104-to-add.html)

---

