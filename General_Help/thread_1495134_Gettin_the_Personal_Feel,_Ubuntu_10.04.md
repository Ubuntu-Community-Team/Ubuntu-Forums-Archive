---
title: "Gettin the Personal Feel, Ubuntu 10.04"
date: 2010-05-27
forum: General Help
---

### Post by That IT Guy on 2010-05-27
Remember that, back on the old 9.04 or whatever. When you could simply put across something and make that your log on screen. Yeah, been stuck too long in the world of windows and yesterday thought. Yeah, I need a challenge and dumped my windows platform for linux 10.04 distro. Fully installed. 

I downloaded an Ebook known as Sams ubuntu unleashed 2010. Been reading through it and it erased all fears for ubuntu and well gave me the confidence I needed to get the ball rolling. Now. I need someones experience in helping me learn the basics of tooling up, getting my distro looking unique and appealing as of right now. Its basic. 

- How do I add the fantastic visual effects, <Yes i have adanced effects on, compiz installed.>
- How do I install new log on screens, custom themes, beryl?
- WIth ubuntu, what programs would be reccomended for a standard user who is steppig into the HUGE world of ubuntu's arena; armed only with Windows world knowledge. 

- What other programs are there to customise ubuntu and are there any walkthroughs? <need to give my 9600 graphics card a work out.> 

- Are there any other browsers for Ubuntu?
- Are there ways to run windows games inside a Unbuntu OS?

---

### Post by X-Windows on 2010-05-27
Hi and welcome to the Ubuntu forums! As a recent convert like yourself with a long windows history, I'll share some things that helped me out.

If you already have Compiz installed (make sure you have the extra plugins installed too), go to system > preferences > CompizConfig Settings Manager. For starters, enable the desktop cube, rotate cube, and wobbly windows. If you want transparent windows, go to Opacity, Brightness and Saturation, window specific settings > New (**Important: Set the slider to 100**!) then click the plus button > grab then click on an active file explorer window. Adjust the opacity as you see fit. There are many more effects, but they are best learned by experience instead of text.

For themes, try [http://gnome-look.org/](http://gnome-look.org/). To install themes save them to your HD, leave the file "compressed" then right click your desktop > Change Background > Theme tab then drag-and-drop the file into the window. It should ask if you want to apply the new theme immediately. 

Personally the thing that helped me most was just to look around in the file explorer and see how the file system was laid out. For instance, the /home directory more or less correlates to the Users/<username> directory in windows. while the mysterious "/" directory is simply "C:". Another thing that I did, and am eternally grateful for, is creating a separate partition to keep all my documents, music ect... on. This way when I mess stuff up in Ubuntu, I can do a clean install relatively quickly, without having to back up all my data.

Another thing that helps, and this ties into your last question, is the WINE program. This is a program/layer that runs windows programs on the ubuntu OS. To be frank, I have never gotten it work perfectly and would recommend setting up a VirtualBox instead, but I know people who have gotten it to run some pretty hefty games.

Customizing Ubuntu is pretty much based off themes and compiz. Download the Emerald theme manager to handle window effects and use themes for everything else. You can get *far* more personalization in Ubuntu than you ever could in windows.

There are plenty of other browsers out there, but why would you want to change from Firefox? I used IE on all my windows boxes for many years and have just recently tried Firefox. I totally fell in love with its spell check feature, something IE can't touch, as well as its plethora of add-ons. However if you are looking for other browsers Opera would be my next choice, followed with Google Chrome running on Wine.

As for games, you're pretty much stuck. Sure there are pleanty of puzzle games like majahong and suduku, but there are very few FPS games. I would recommend, if you are a die-hard gamer, to keep your latest version of windows on a separate partition and dual-boot into it whenever you get the gaming urge.

---

### Post by That IT Guy on 2010-05-27
Im an Opera broswer user, so i tend to bounce between firefox and Opera from time to time. Thanks for the information. Can you explain anything about Beryl in the past, I've seen these wonderful yotube videos of windows spinning in a circle instead of a cuble based and so on. Its amazing what the Ubuntu world has thought up. 

- Would wine be able to run some video games? Sure im a die hard gamer, but thats now what my PS3 is for, my current system is outdated for the latest games. So i'll be saving up for a set windows system, but keeping my linux system as my primary box on the network. Ideally because i wanted to challenge myself to experience the other side of the OS spectrum and kick myself out of my comfy chair of windows and into the larger, freestyle world of linux. 

- With what you said to themes, is that the same way with applying login screens etc? I'll be loading up screenshots later <if I can figure that out on linux XD> 

Well. apart from that, thank you for you response. 

T I G

---

### Post by X-Windows on 2010-05-27
By windows spinning in a circle I assume you mean changing the cube to a "sphere", an effect that requires the extra plugins for Compiz. This is in the CCSM settings under Reflections and Deformation. For some reason whenever I enable Reflection and Deformation it always uses a sphere, but the selection is under Deformation tab > Deformation.

Sure wine can run some games, but it is not as simple as windows. For instance make sure when installing through wine that you do **not** install any direct-x related things, most games will say something like "Requires Direct-x version X.Y.Z, Install now?" Just click No and continue. If you are dual-booting windows it is easier to install the game through windows and use wine to launch it, otherwise windows gets confused because it cant find registry entries for the game. I have gotten several older games to work on Wine, namely Deus Ex and Morrowind although there are some glitches.

I'm not so sure about login screens, I've heard that it is possible with third-party apps but I haven't tried it. If you are the only user on your computer you can set it up to bypass the login screen if you want. System > Admin > Login Screen > Unlock > Log in as <username> Automatically. You can also turn off that annoying login sound here (to turn off the other sound go to System > Preferences > Startup Applications and uncheck "GNOME Login Sound").

---

### Post by jerenept on 2010-05-27
Midori is fast, and has a few useful features from Opera (like Speed Dial) that I find useful. As a plus, it is open source! It is however, a little unstable.

---

### Post by That IT Guy on 2010-05-27
I was actually referring to the wall thing on Ubuntu where it turns into a small O with the small squares of the desktop. I'll post a link of the video later. it amazed me. Pretty cool though but still just as epic.

---

