---
title: "Ubuntu or KUbuntu? New to Linux"
date: 2009-08-02
forum: General Help
---

### Post by therocco2k on 2009-08-02
You Know in the Prefix you have to select before you post a thread in this forum that asks you what OS you're using, I dont know anymore: Hence the Following long but very important questions to me and my develpoment as a Programmer and Marketing Director, and ultimately hopefully an System Administrator.

Im new to Ubuntu Linux and linux in general - I was reading on how to best update my driver for Nvidia GeForce, (which I was told to add the info on this [URL]("https://edge.launchpad.net/%7Eubuntu-x-swat/+archive/x-updates"), which I'm still trying to figure out... anyways..I came across a thread stating this - 

*"Don't have courage to go to the corrupt Ubuntu. So freshly installed Ubuntu. Reboot . Installed nvidia driver (185.xx.xx using terminal). Reboot . No problem. Install nvidia driver in KUbuntu too . No problem."*

KUbuntu, and Ubuntu, What is the difference? - I Always Wondered why I saw a Graphical Loading Screen when loading Ubuntu that has a Splash Screen that says KUbuntu while loading, but really it's ubnutu? 

So, Concerning the Quote above from the gentlemen on another thread, should I be taught more about the differences, because it seemed to have some large outcome on the success of his Software/Driver Installations.

I Downloaded UBUNTU thats all I was told, I love Linux but there's too many Cryptic Secrets.

Could somebody be as kind to explain to me all the differneces between the two, the best way to install a driver, and Oh Ya - I just found out my Computer is a AMD Athlon 64 but I've always downloaded 32bit software, Should I be downloading x64 software - I run a 2.40GHZ CPU with 3GB Ram and a Nvidia GeForce 8800GS with 120GB HD... (I mean is there a difference, and if so what - Should I from now on download when possible the 64 amd software instead of the 32?)

Thanks for all your knowledgeable guidance, it's forums like this that make the Community of Open Source Software and Programmers like me learn, grow, and teach others just as you've done. I really would like to donate to this forum.

---

### Post by Rob_H on 2009-08-02
The difference between Ubuntu and Kubuntu is the desktop environment each uses. Ubuntu is based on the [GNOME]("http://www.gnome.org/") desktop and Kubuntu is based on [KDE]("http://www.kde.org/"). This affects how you interact with the computer, and to some extent, what programs are installed by default. Which one you choose is a matter of taste. In general, GNOME has a reputation for being clean and simple, whereas KDE is highly configurable. I recommend trying them both and then deciding. But don't fret about it too much. They are both based on the same foundation and will run the same programs with very few exceptions. Only the "skin" is different.

---

### Post by Rob_H on 2009-08-02
And by the way, NVIDIA video driver installation doesn't vary between the two. Although GNOME and KDE each have separate utilities for configuring the screen and so forth, NVIDIA supplies its own utility called "nvidia-settings" that works the same across Ubuntu and Kubuntu.

---

### Post by jms1989 on 2009-08-02
Ubuntu used the gnome environment and kubuntu uses the KDE environment. The two are the same but they use  different desktop environments.

For your current setup, you are free to use the 32bit software. You won't gain much of an improvement from the way I see it. If you do decide to use the 64bit software, be aware that there are some programs that may not work without some effort. That problem also exists in windows so its not just linux. Its the developers behind the software that are still living in the past.

The only different I can see from a 64bit app over a 32bit one is the ability to use over 3.2 or 3.5GB or ram, depending on the system. 32bit operating systems are can only utilize up to 3.5GB due to the address space being too small but the 64 bit os can access far more memory and whatnot but it also consumes more disk space.

Also, wikipedia has some nice articles explaining the two architectures.

Did I leave anything out?

---

### Post by hibliss on 2009-08-02
As stated above, there is no need to choose between the two. Install standard Ubuntu, then in Synaptic Package manager, you can install any Desktop Environments you like. 

I have Gnome, KDE, LXDE, and XFCE. When you start the machine, you can change the session to whatever desktop environment you like.

I recommend you try LXDE and KDE along with Gnome. KDE is my favorite, but I use LXDE for my Eee as it is very lightweight and still looks finished and polished.

---

### Post by sasho_zl on 2009-08-02
With the command **sudo apt-get install kubuntu-desktop **, you can install the Kubuntu Desktop and choose your graphical environment from the options menu at your login screen.

---

### Post by keypox on 2009-08-02
> **sasho_zl said:**
> With the command **sudo apt-get install kubuntu-desktop **, you can install the Kubuntu Desktop and choose your graphical environment from the options menu at your login screen.

I have tried kde a few times maybe I will isntall it one more time... though i have gnome setup how i like it.

---

### Post by sasho_zl on 2009-08-02
> **keypox said:**
> I have tried kde a few times maybe I will isntall it one more time... though i have gnome setup how i like it.
My Gnome desktop is also perfectly customized, but I like changing to KDE from time to time just because it's very different and it's fun :D
Also a big advantage is having all the applications from Gnome and KDE installed and working on both of the environments.

---

### Post by therocco2k on 2009-08-02
You've all answered my question wonderfully. - I had one misunderstandingthe gentleman Rob_H who said Nvidia has a software called "nvidia-settings" for Linux - What does this do, also where can I get it.

One of my other MAIN questions IS..... and I know this is touchy in Linux

Can I Play my Games on Linux? Maybe Steam Client running Call of Duty 4 on Ubuntu? - Or is Linux not cut out for Games yet (Which if it isn't, that's a major set back in Linux's Spot on the OS Map.

Not that it isn't better then windows at 1,000,000 other things - MOST , actually over 80% of Computer users play Games or use Software like 3D Graphic rendering and Animation, and Video Editing that relies heavily on the Video Perfomance of the Operating System.

So?

Thanks for all your replys, this is a wonderful forum, and I am DIGGING linux. I'm Pimping my GNOME - With [http://tuxenclave.wordpress.com/2007/11/23/ubuntu-customization-guide-v2/](http://tuxenclave.wordpress.com/2007/11/23/ubuntu-customization-guide-v2/) - That guy made a KILLER tutorial on making your linux GUI Portion of the OS, Amazing in Apperance.

Thanks again.

---

### Post by sasho_zl on 2009-08-02
If you have Nvidia drivers installed on your system you should already have nvidia-settings manager. Just type nvidia-settings in the terminal. Write sudo in front of that if you want the manager to be able to permanently edit your xorg.conf file.
Regarding your question about the games I would suggest to you to look with google for specific tutorials for running games on linux through the Wine software.

---

### Post by Seventh Reign on 2009-08-02
Call of Duty 4 through Steam plays perfectly for me.  Although you may have to 'tweak' the graphics settings quite a bit to make it playable.  

Call of Duty 1, 2 and 4, Half Life 1 & 2, and Episodes 1 and 2, Team Fortress 2 all play for me.  I havent had much luck getting Portal to play with 9.04 yet tho ..

---

### Post by Rob_H on 2009-08-02
> **therocco2k said:**
> Can I Play my Games on Linux? Maybe Steam Client running Call of Duty 4 on Ubuntu? - Or is Linux not cut out for Games yet (Which if it isn't, that's a major set back in Linux's Spot on the OS Map.

There are plenty of good games on Linux, and many are free. But if you're expecting the same number of games as Windows, you'll be disappointed. There simply aren't as many game developers targeting Linux. There is a good site called [Linux Games]("http://www.linuxgames.com/") that tracks the state of the Linux game scene. Also, just google for "linux games" and you'll find some sites.

As Sasho says, you can get some Windows games to run on Linux via WINE or the new release of Virtual Box, but not all of them. Keeping a Windows partition around just for games is not a bad idea.

---

### Post by therocco2k on 2009-08-03
Yah Thanks, I had originally had Windows Vista installed on this machine, I re-partitioned the driver using the ubuntu boot from CD Partioner - Now that I use Linux - I noticed that out of the 147GB of hd I have left on windows, I'm only using 28gb in Linux - and I need more fast! Is there any way I can make more room for my Linux Partition using the Same Method, or is there anoither way?

BTW -Thanks for the great advice all, I have gotten knowledge - I love computer knowledge. If you know what I'm talkin about let me hear you say:

public class W00t {
         public statc void main(String[] arguments)
}

---

