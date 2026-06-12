---
title: "I can't see any desktop menu"
date: 2010-05-22
forum: General Help
---

### Post by Dragmah on 2010-05-22
Hey everyone, please be gentle on me i am a newb to ubuntu and do not know the coding aspect, though i do wish to learn. I am having menu issues after upgrading to Ubuntu 10.4. I was using Cairo-dock in Ubuntu 9.10, i did have issues setting it up in the beginning but i eventually got it set upand working fine, that is until i updated to 10.4. Now i can't see any menu at all. Needless to say this has made a few of the tutorials difficult to manoeuvre as they all use the menu and not terminal, which is normally a good thing.

I liked having Cairo dock, but if it this difficult to adjust each time i would much prefer to use another like AWN, which i have heard to be better any way.Just for extra information I have tried to install AWN but this has also not worked - i.e. can't see any menu's - that and the installations guides tell you to open it from the menu... and i tried typing both AWN and "Avant Window Navigator" into the terminal but neither work.

Please help

---

### Post by cespinal on 2010-05-22
welcome to the forums :)
I really did not understand what you meant with the menus. Are your panels visible? 

For using a working dock, install docky, and tell us how it went. 

Run the following commands from your terminal


sudo add-apt-repository ppa:docky-core/ppa  (this adds the docky repo)


sudo aptitude update (this updates the sources list)


sudo aptitude install docky  (this one is pretty obvious :D )

Have a little patience, I'm sure we will come around with a solution. 
Cheers

---

### Post by Dragmah on 2010-05-22
Thanks for the Welcome, I have to say i love Ubuntu so far despite the teething. Everyone is actually helpful and the things that can be done - once i learn them...

Sorry I didn't state my issue clearly, by menu I meant the launch menu or in windows terms the 'start menu'. Basically when you look at my screen all you can see is the desktop short cuts.

I installed Docky, really cool little thing by the way, exactly what I wanted from Cairo-dock.

The problem still half stands in that i cannot see the 'start menu' (it would probably help if you could also tell me the correct term for this, as i have to unlearn all the windows jargon that is mashed in our faces when learning about computers). Has this clarified it more now?? The only way i can think of explaining it is comparing it to the start menu in windows that runs along the bottom of the screen, and when i installed Ubuntu ran along the top of the screen, this is the thing i cannot see at all.

As you can imagine it has caused confusion as i don't know where the application run files (windows comparable .exe file) - once more I don't know the correct terminology but would like to -  and have only by luck found Firefox and terminal.

I do now have additional questions in regards to Docky... How would i go about adding extra docklets to Docky as i only have the standards, 'Docky', 'Mozilla', 'Terminal', 'Rythmbox', and the ones i added from the selection 'computer monitor', 'trash', 'show desktop', 'clock'. Basically i would like to add shortcuts to programs that i run alot.

As for patience, with your help I have all the patience in the world, thank you very much for your help it is much appreciated

---

### Post by psycho5 on 2010-05-22
Did you accidentally delete the "start menu"?

In ubuntu they are called panels. If you can't see them, hit alt+f1 does the menu still show? If it doesn't maybe you accidentally deleted your panel.

---

### Post by Dragmah on 2010-05-22
I just tried Alt+F1 and nothing changed, but to my knowledge Alt+F2 is meant to be a short cut to Terminal, am I right?? But when i hit Alt+F2 it also does nothing so i don't think the short cut keys are working....

As for the panels, cairo dock was my panel in 9.10, it had all of my program short cuts in applications, and a shut down computer button, etc. I don't see how i could have accidently deleted my panel unless i did it whilst installing cairo dock because, as i stated before, i have only had cairo dock to use as my panel since i installed it.

How would i go about getting the panel back??? i would like to access the programs i install in an easy manner, that and if i expect my wife to use this computer it has to be easy to use, i.e. like the start menu in windows

Thanks for the help, it is much appreciated

---

### Post by pj_kare on 2010-05-22
Open your home folder(if you can), from the VIEW menu click Show Hidden Files, find the folder called .gconf, in the Apps folder delete the folder named PANEL, then logout and log in again, or just reboot whichever is easiest. 

Or if you prefer to use Terminal (or can't access your home folder) just copy and paste this->     rm -r ~/.gconf/apps/panel
And hit enter obviously, then logout/login or reboot....hope this helps..

---

### Post by Dragmah on 2010-05-22
I tried the folder way and rebooted, didn't work, did it again as the folder reappeared, making sure to delete it from trash, still didn't work and repopulated the folder which i am guessing is what should happen. So i tried the terminal way but it doesn't do anything, it just asks for the next command as if nothing happened.

I do vaguely remember changing some setting whilst i was trying to make cairo-dock work, and for anyone reading this i am not bagging cairo-dock, i know a lot of people put alot of effort into making these things and trust me it is much appreciated and i do not take your efforts for nought, would just like everything to work.

Thanks for the try, i am sure we will get a solution . By the way i am loving the help so far, thanks for this, it is giving me good vibes for the Ubuntu community

---

### Post by Dragmah on 2010-05-22
Hey guys I feel like such an idiot, i finally found the location for all the applications and double clicked on the panel, and BAM up it comes, working like a charm. Sorry to waste your time guys, but you gave me such good information, and i will definitely be using Docky as it is really useful.

Thanks for all your help and any cool suggestions you have for programs let me know

I do have one last request, what program would you suggest for installing and running Windows programs, namely adobe creative suite programs, i have work copies and if i could install and run them from ubuntu that would be great

Once more thank you very much and am looking forward to a very happy relationship with ubuntu, and its fantastic community

---

### Post by Angel Joaniquet on 2010-05-22
> **Dragmah said:**
> I do have one last request, what program would you suggest for installing and running Windows programs, namely adobe creative suite programs, i have work copies and if i could install and run them from ubuntu that would be great

Use wine:

$ sudo apt-get install wine

or instaled with ubuntu sofware center, in the apps panel.

it will allow you to execute  *.exe 

see(for example, the net is full of tutorials): [http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by fabounet on 2010-05-22
in Cairo-Dock you can have the menu by enabling the "GMenu" applet.

---

### Post by pj_kare on 2010-05-23
> **Dragmah said:**
> So i tried the terminal way but it doesn't do anything, it just asks for the next command as if nothing happened.

As you have solved this yourself, which is great by the way, you may not return to read this reply, but, for future reference, the Terminal command does the same  as my previous suggestion, it deletes the -Panel- folder, and unless you actually had the .gconf/apps/ folder open you would not have noticed anything happening, and yes, you're correct, a NEW Panel folder is created/repopulated, which usually fixes/restores the panels when things are missing or accidentally deleted from a panel. (You will lose any customising you have done).

Not knowing exactly what had happened, I just though it may work in this instance.

Also, welcome.......if it wasn't for these forums I wouldn't be using Ubuntu. I still have XP installed but rarely use it any more. Besides, sick of paying through the nose for MS OS's (I've had 95,98, 98SE, ME, and XP since it was released) then when you do buy it you gotta buy anti-virus (or hope for a good freebie), every time you re-install you gotta prove you own it. :(

Cheers......

---

### Post by Dragmah on 2010-05-25
Yes i am certainly thankful for these forums, and given the speed at which it is spreading ubuntu will definantly be the top used OS. I am loving it, and Docky is by far the **coolest **application, it works like a dream. As for Ubuntu 10.4, loving it. Unfortunately i **have **to use windows for my work computers but all my home computers have ubuntu and the fact that i have customised them so that anything works on them is a dream.
 
Unfortunately now my only issue to solve is getting Office 2007 to work on them fluently as my wife needs that over open office, stupid proof reading industry, making my life difficult. And for anyone reading this saying that open office is as good, i agree **but **my response is, "meet my wife, she is stubborn". That and if work gives her the codes to use it, why the hell not...

---

### Post by vs8 on 2010-09-27
Hi! If you want to use a very nice front-end for Wine, Install PlayonLinux. 

Ubuntu Tweak is a must-have to make your life easier. It enables you to manage your software, add PPAs with just one click, clean your disk and tons of other stuff. I can't live without it and I highly recommend it to everyone.

And read OMG!Ubuntu! for the latest stuff in Ubuntu's world! [http://www.omgubuntu.co.uk/](http://www.omgubuntu.co.uk/)

---

