---
title: "Chess help"
date: 2009-12-29
forum: General Help
---

### Post by JJ 3000 on 2009-12-29
Hello, I'm having a problem with the chess program that comes installed with Ubuntu. It has been working fine until tonight. I though that I might try the 3d mode. When I tried to switch I got: "Unable to enable 3D mode Your system does not have the required software to enable 3D mode". 

So I searched the Ubuntu forum for the the solution. I found this page:
[http://ubuntuforums.org/showthread.php?t=551414](http://ubuntuforums.org/showthread.php?t=551414)

KIAaze responded to the problem and suggested entering the following into the command line: 
sudo apt-get install python-opengl python-gtkglext1 libgtkglext1

So I opened up the terminal and copied and pasted the code. Then I opened chess and clicked on view and chose 3d view. I got the same error as before. I thought that the problem might be that the chess program was running when I ran the code. So I exited chess and tried to open it again. This is where the problem started. 

Chess crashed. When I clicked on it I could see the "starting chess" in the bottom toolbar and then It would appear for a second. Then it would just disappear. 

I shut down the computer and then rebooted. Now I cant open chess at all. I'm getting really frustrated because I really like to play this game. Every time I try to launch it the game crashes. 

I read the thread again and noticed that the original poster said that he had version 7.04. I have version 9.04. Does that make a difference? 

Can someone please help me. I just want to play chess again.

---

### Post by howefield on 2009-12-30
> **JJ 3000 said:**
> I just want to play chess again.

There are options in the repositories, including xboard and gnuchess, brutalchess, emacs-chess, eboard, dreamchess, plus a load of other programs and engines.

If you want to play online, try Babaschess running through wine and connect to FICS or run playchess through wine and connect to playchess.com

Both run very well.

You need not forgo your chess fun simply because the included game is giving you grief. :)

---

### Post by gimcrack on 2009-12-30
brutalchess is my favorite chess game in Linux. You'll will need a 3D video card with the correct drivers.

If you can play other 3D games like Tux Racer & Sauerbraten, then you are set.

---

### Post by iloveunix on 2009-12-30
When you did ```
sudo apt-get install
```, what did terminal say? It might have not found the package, in which case you need to download it your computer. Also, your graphics card might not support 3D mode.

PS: If you really like Chess, you could buy Chessmaster.

---

### Post by howefield on 2009-12-30
> **iloveunix said:**
> PS: If you really like Chess, you could buy Chessmaster.

Talking about commercial products, how about a native Linux application...

[http://www.shredderchess.com/linux.html](http://www.shredderchess.com/linux.html)

---

### Post by JJ 3000 on 2010-01-01
Thanks for all of the responses guys. I'm still having this problem. I don't think that my video card is capable of running the 3d mode:(


> **iloveunix said:**
> When you did ```
sudo apt-get install
```, what did terminal say? It might have not found the package, in which case you need to download it your computer. Also, your graphics card might not support 3D mode.

I don't remember what the terminal said exactly, but I'm pretty sure that it went though the install routine. There were a few different lines of code that looked like it was installing the python program. Also, the problem started right after I ran the code and tried to enable 3d mode. 

I'm using an older computer. It isn't the best but the specs aren't horrible. The video card is pretty low end. It's an NVIDIA RIVA TNT2 with only 64mb of video RAM. I thought that my problem may be that I was using the generic video driver that comes installed with Ubuntu. So I went to the NVIDIA website and downloaded the driver from there. I ran into another problem here. I cant get the driver to install. 

I followed the instructions on the NVIDIA site. Here's the link:
[http://www.nvidia.com/object/linux_display_ia32_71.86.11.html](http://www.nvidia.com/object/linux_display_ia32_71.86.11.html)

I have next to no experience with Linux, but I thought that installing a driver couldn't be too hard.

I downloaded the file and saved it to my desktop. Then I opened the terminal and typed in: sh NVIDIA-Linux-x86-71.86.11-pkg1.run
 
Every time I do that I get:  Can't open NVIDIA_Linux-x86-71.86.11-pkg1.run
I've tried doing this several times. Also I've tried clicking on the driver and running it but that doesn't help either. Could someone please tell me what I'm doing wrong?

I'm starting to get really frustrated with this problem. Isn't there some way to undo the change I made when I ran that code? Could I find that software that I installed and delete it? If so, where would it be?
 

@ howefield
Could you please post a link to some free chess programs?

---

### Post by OldAlgis on 2010-01-01
> **JJ 3000 said:**
> 
I downloaded the file and saved it to my desktop. Then I opened the terminal and typed in: sh NVIDIA-Linux-x86-71.86.11-pkg1.run
 
Every time I do that I get:  Can't open NVIDIA_Linux-x86-71.86.11-pkg1.run


Is NVIDIA_Linux-x86-71.86.11-pkg1.run accessible and is it made an executable from the console?  To make it executable type and Enter:
```

sudo chmod +x NVIDIA_Linux-x86-71.86.11-pkg1.run

```
To play chess online person to person, I use Jin (FOSS program) and the freechess.org server.  Try googling for Jin, FICA and freechess.org.  There are lots of info there.

---

### Post by 4Orbs on 2010-01-02
Before you try to install the nvidia driver manually... did you look to see if Ubuntu has a driver available for your video chipset? Open the menu System > Admin > Hardware Drivers and see if the 71 driver is available and recommended. If so, then activate that driver and reboot. If there is no recommended driver available, then manually install the one from nvidia's website.

---

### Post by howefield on 2010-01-02
> **JJ 3000 said:**
> @ howefield
Could you please post a link to some free chess programs?

I'll mention first the online options I use(d) because my preference is to play against other people, rather than against software/machines. 

My favourite place to play is playchess.

There are generally about 5,000 players at most times of the day, so you'll always get a game according to your rating/time control requirements.

[http://playchess.com/](http://playchess.com/)

The free client software runs very well on linux through wine. It also looks very good.

You can log on as a guest for free and play in the "Cafe" or pay (a very modest sum) to get a registered nickname and rated play plus many other benefits. A free 30 day trial is available. Generally good atmosphere with lots to offer. 

Babaschess (which I have only previously used in windows) by all accounts runs through wine very well, it was very good software when I used it, I'm sure it is even better now. Allows you to connect to Internet Chess Club, (ICC) my knowledge of ICC is dated but I wouldn't play there even if someone were to pay me ;)  

[http://www.babaschess.net/](http://www.babaschess.net/)

FICS is a free chess server, which I am just about to try again, but when I last used it, (several years ago) the main drawback was lack of users, I am going to try it this afternoon.

[http://www.freechess.org/](http://www.freechess.org/)
[http://www.freechess.org/cgi-bin/Download/FICS_Download_Interface.cgi](http://www.freechess.org/cgi-bin/Download/FICS_Download_Interface.cgi)

As I mentioned before, there are many options within Synaptic Package Manager to download a chess program, especially given that unless you are a very strong player, mostly all the options will give you a good game and beat you up good style, with that in mind, it comes down to features and looks. Dreamchess seems to attract decent comments.

Have a read also at

[http://en.opensuse.org/Chess](http://en.opensuse.org/Chess)

---

### Post by JJ 3000 on 2010-01-05
Thanks for the links howefield! I had no idea there were so many great chess programs. I really appreciate it.  



> **4Orbs said:**
> Before you try to install the nvidia driver manually... did you look to see if Ubuntu has a driver available for your video chipset? Open the menu System > Admin > Hardware Drivers and see if the 71 driver is available and recommended. If so, then activate that driver and reboot. If there is no recommended driver available, then manually install the one from nvidia's website.

When I go to System -->Admin -->Hardware drivers, I get: Searcing for drivers and then I get a window that says No proprietary drivers are in use on this system at the top. The window is empty and I can only click on Help Or Close near the bottom of that window. 

I'm having trouble manually installing the driver from the NVIDIA site. I haven't tried OldAlgis' solution yet, do you think it will work?

---

