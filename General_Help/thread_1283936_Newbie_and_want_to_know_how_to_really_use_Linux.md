---
title: "Newbie and want to know how to really use Linux"
date: 2009-10-06
forum: General Help
---

### Post by BudE on 2009-10-06
Good morning,
I am a newbie to Linux but not to computers and stuff. I really want to convert all the way but not sure how to make some of the Windows programs that I have work with the Wine I installed. When I see all the cryptic stuff I need to do to just install something I have to admit I'm totally baffled. Now is there anywhere I can go to really learn about using Ubuntu Linux, or mostly the Wine program. It's on my system but have no idea how to configure it to work properly. Currently I can surf using Firefox which I love and now have Open Office Org and trying to learn it's database program as I program in Access all the time. You know in a Win computer you can RightClick Start and hit Explore to show all your drives...well is there a way to do similar in Linux? And how to access my network drives? Any help you can offer will be appreciate. Future Linux user.
Thanks
Bud  :confused:

---

### Post by jmszr on 2009-10-06
BudE,

Welcome aboard!

There is a Wine section of these forums: [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313) . The people there are probably better equipped to answer your Wine questions.

This looks like something you might be interested in: [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/) and this: [http://www.ubuntugeek.com/winexs-simple-graphical-environment-to-configure-wine.html](http://www.ubuntugeek.com/winexs-simple-graphical-environment-to-configure-wine.html)

As for the rest of the Ubuntu system:

 I would suggest this sticky by ugm6hr: [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404) . The links to Psychocats Ubuntu Guide:  [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)  and Free Ubuntu Pocket Guide by Keir Thomas:  [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  are of particular note but the entire sticky is full of a lot of good information.

Also: [http://ubuntuforums.org/showthread.php?t=790485](http://ubuntuforums.org/showthread.php?t=790485)  (Newbie 101) and: [http://ubuntuforums.org/showthread.php?t=714338](http://ubuntuforums.org/showthread.php?t=714338)  (Newbie Terminal Intro)
 
Multimedia & Video Howto: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)  

To add the Ubuntu search engine to Firefox: [http://www.ubuntu-search.org/](http://www.ubuntu-search.org/)

---

### Post by scouser73 on 2009-10-06
Hi Bud and welcome to Ubunu and the excellent Ubuntu Forums, here is a list of free e-books that you can download: [[COLOR="Red"]**Free Ubuntu e-books**[/COLOR]]("http://www.ubuntugeek.com/free-ubuntu-linux-e-books.html") & [[COLOR="Red"]**Ubuntu Pocket Guide**[/COLOR]]("http://www.ubuntupocketguide.com/download_main.html")

---

### Post by Bucky Ball on 2009-10-06
What is it you want to do? You might find there are Linux apps that do the job just as well and you can avoid fiddling with Wine. Not all Windows programs are going to work with it and some will work great, others not so good.

Find something native is preferable. If you want to use mostly Windows programs you are better using Windows.

---

### Post by Bonster on 2009-10-06
If ur coming to linux and expecting Wine to be ur life saver then ur trying linux for the wrong reasons.

---

### Post by khelben1979 on 2009-10-06
> **Bucky Ball said:**
> Find something native is preferable. If you want to use mostly Windows programs you are better using Windows.

I agree on this to some extent. [Dos box]("http://en.wikipedia.org/wiki/Dos_Box") is also an alternative if you want to run older Windows applications/games on your Linux system. Just wanted to bring this up and.. welcome to Linux! ):P

---

### Post by 1clue on 2009-10-06
Some of this has already been said, but...

Native software is best.  Rather than Microsoft Office, try OpenOffice, gnumeric and similar.

If you have something you absolutely must run in Windows, then you have several options:
[LIST=1]
[*]Dual boot.
[*]Wine
[*]Crossover Office.
[*]VMware or similar.
[*]Any number of Linux-based emulators and virtualization products.
[/LIST]

Crossover Office is made by the people who make Wine.  It's a commercial version of the same program, with many of the mainstream apps working fairly well, rather than having to fight with it.

VMware is an extremely good choice.  They are free of charge, some of their products have been contributed to Open Source, and they are very accurate at behaving like a Windows box.  The downfall of VMware is that there is an extra layer of abstraction between the hardware and the software, and that can slow things down.  Especially visible with graphics-intensive apps like games or movie players.  Another thing which bothers some Linux users is that VMware installs the guest operating system (Windows, in this case) but you still have to own valid licenses for Windows and all the software you put on it -- One license for each copy installed on any real machine or VMware image.

I use VMware at work.  It's good enough that you can use it to test whether software you develop will work on some specific platform.  Sometimes it seems like the software runs better in VMware than it does on your bare hardware with whatever operating system.


All that said, if you intend to use Linux just to run your Windows apps, and everything you do you use Windows as a test of pass or failure, then you will be miserable in any Linux distribution.

Chances are, whatever document you're trying to use can open in some Linux-native app, and you can probably write that format too.  So you can send everyone Word documents, Excel spreadsheets, and whatever else.  You just won't be running Word or Excel.  Linux is about interoperability, not duplication.

Good luck and have fun.

---

### Post by BudE on 2009-10-07
> **jmszr said:**
> BudE,

Welcome aboard!

There is a Wine section of these forums: [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313) . The people there are probably better equipped to answer your Wine questions.

Thanks to all who replied to my post. First, I am a Newbie coming to Linux and have opted over for a reason. Reason being I am wanting to get away from WINDOWS. I didn't come to Linux to run Windows, but I do have certain specific projects that I developed in Access for my JOB and other users in my sideline work. Time has been spent working on them and I want to be able to maintain them on my LIUX ONLY  system. I have a system just for Linux because I wish to learn it, adapt and completely move over. I really know that if I want ONLY Windows stuff to just stay there. Kinda intelligent guy of some sort. That being said, it's Mainly Access that I would be concerned about, and I tried to access my printer from Linux over my network but I couldn't find the printer or know HOW to find my printer driver to set it up. So I put the driver on the system and after installing Wine tried to run the Setup program, but it would just sit there and do nothing. So that's the reason I was asking about what I asked. I have been using computers in general since the pre-Windows era with Dos 3.0, 5.0, 5.5, all the way up to Window 3.0. Open source is a great thing and maybe it didn't sound like it but I am trying to convert. It takes a while and it's just not something I could just pop on my system and run with it like I have in the past. So I am in my training wheels, if you don't mind. So again, for those of you who offered assistance I thank you very kindly and look forward to being a member here for some time now. I am a member of many forums, but mostly on DBForums.com, which is all about Databases. So you all have a nice day as I take time to check into all of the info provided. 
  Oh, just to let it be know, I already tried OpenOffice.org Database program. Though I know databases I didn't get it to work extremely as well as I am accustomed to. But I'll keep at it. In the meantime I HAVE TO keep with Access, as that's why my job has.

thanks and have a Wonderful Day,
Bud    :)

---

### Post by 3rdalbum on 2009-10-07
I'll bite on the questions that others have forgotten to answer.

> **BudE said:**
> You know in a Win computer you can RightClick Start and hit Explore to show all your drives...well is there a way to do similar in Linux? And how to access my network drives? 

I don't know this bit of Windows, but I think I know what you want. Linux is quite different to Windows in this regard, because on Linux your disks are accessible through a "mount point" (it's like a folder in the filesystem, and when you open it up, there's the contents of your disks). For removable disks, the mount point is usually in /media.

If you open up a file browser window and go to View > Computer, you will see the plugged-in storage devices that Gnome can mount or unmount. You won't see disks that are mounted as part of the main filesystem - for instance, if you have your /home stored on a different disk or different partition, it won't be shown in Computer; it will be accessible through the mount point only.

If that explanation has been too verbose, then I'm sorry; just remember, /media is where your removable disks get mounted!

As for your network shares, if you go to Places > Network you can view them, as long as you don't have a firewall running on your client, because this will interfere with communication.

Finally, for your network printer you should just be able to go to System > Administration > Printing, then go to the Server menu and come down to New > Printer. If it's broadcast to the network using CUPS (Unix and Linux printing system) if should appear in the left pane of the window. If it's connected to the network using Windows SMB networking, choose Windows Printer via SAMBA, and use the little network browser there to find and add the printer.

---

### Post by 1clue on 2009-10-07
The "windows explorer" for Ubuntu is called nautilus.  (Somebody obviously thinks Jules Verne was a lot better author than I think he was)

If your Ubuntu installation is how I think it is (and you're using 9.0.4), you probably just took the defaults and have what they gave you.  That would mean your Nautilus app can be reached in the menu bar, you have a "Places" menu.  All the things the previous poster was saying are reachable through that menu.  Pretty much, you could get by with just your Home folder, since the Ubuntu configuration of Nautilus has the mounted disks, network, etc right there on the left side of the window.

You can also add shortcuts to places you want to go from there, so they show up on the left-hand list.


I didn't mean to rile you up with my earlier response.  I'm pretty sure nobody else did either.  It's just that there are many people who "switch" to Linux simply to get around paying money for an operating system.  Most of them have already paid for Windows anyway, whether they know it or not.  You're a newbie, and we don't know what your expectations are.

Since your job requires you use Access, then you need a good stable Access application, along with whatever else is associated with that.

The application database for Wine ([http://appdb.winehq.org](http://appdb.winehq.org)) lists Access as "garbage" which means it probably doesn't work well enough to do what you want it to.

The commercial version shows better results:
[http://www.codeweavers.com/compatibility/search?name=Access&company=&medal=&date_start](http://www.codeweavers.com/compatibility/search?name=Access&company=&medal=&date_start)[1]=1&date_start[2]=1&date_start[0]=2000&date_start[3]=0&date_start[4]=00&date_end[1]=10&date_end[2]=8&date_end[0]=2009&date_end[3]=13&date_end[4]=18&search=app

And of course, you could have much certainty that it will behave exactly the same as on Windows by installing VMware, Windows of whatever flavor, and Access on that.

Good luck and have fun.

---

### Post by ^_Pepe_^ on 2009-10-08
Hi and Welcome to Linux.

I'd like to add my comments to everybody who encouraged to use native programs. 

Only if you need a Windows application, you can do following with fantastic results (if your machine is powerful).

1. Install VirtualBox. It's in Synaptic.
2. Install a Windows XP machine inside it.
3. Install VirtualBox tools (it's an iso image, and you have to run it to compile). It's really easy, believe me; I'm a newbie too.
4. Start Windows, and change VirtuaBox to FluidMode (Right Ctrl+L). Windows desktop will be hidden, and Windows & Linux applications will appear mixed. 

Really powerful.

Regards and welcome!!!
Pepe

---

### Post by BudE on 2009-10-08
> **1clue said:**
> The "windows explorer" for Ubuntu is called nautilus.  (Somebody obviously thinks Jules Verne was a lot better author than I think he was)

If your Ubuntu installation is how I think it is (and you're using 9.0.4), you probably just took the defaults and have what they gave you.  That would mean your Nautilus app can be reached in the menu bar, you have a "Places" menu.  All the things the previous poster was saying are reachable through that menu.  Pretty much, you could get by with just your Home folder, since the Ubuntu configuration of Nautilus has the mounted disks, network, etc right there on the left side of the window.

You can also add shortcuts to places you want to go from there, so they show up on the left-hand list.  

Hi 1Clue and thanks for your info. I have been out of pocket and unable to try anything suggested here, but the weekend is near and I can catch up then. Nope, I didn't get riled up but just seemed everyone was thinking I wanted Linux for Windows. I want Linux because it's said to be a more stable system first of all, next there are no licensing schemes and junk to work with and you don't spend most of your day  Re-booting. Trust me, I'm not afraid to try new things but you should always Look before you Leap, sort of speak. The other programs that are native Linux will be fine with me. Only needed to make sure I can maintain my other programs already created. Myself, I don't play any games on the computer. Just databases, spreadsheets, lite programming and animation. Just so it's known I didn't run to each new Windows that always came out. On my other system I still have Win 2000 Pro. Didn't need the other stuff, just need something that worked and allowed me to do what I do. No bells and whistles needed, I am just plain jane....er....joe that is....hehehe. I do like it here in the forum and look forward to learning a lot. That's what I am doing, have my training wheels on and as usual, don't read many books to learn to do things. To all, thanks a bunch and hope you have a Wonderful Day. Until next time....
cya
Bud    :)

---

### Post by BudE on 2009-10-08
> **^_Pepe_^ said:**
> Hi and Welcome to Linux.

I'd like to add my comments to everybody who encouraged to use native programs. 

Only if you need a Windows application, you can do following with fantastic results (if your machine is powerful).

1. Install VirtualBox. It's in Synaptic.
2. Install a Windows XP machine inside it.
3. Install VirtualBox tools (it's an iso image, and you have to run it to compile). It's really easy, believe me; I'm a newbie too.
4. Start Windows, and change VirtuaBox to FluidMode (Right Ctrl+L). Windows desktop will be hidden, and Windows & Linux applications will appear mixed. 

Really powerful.

Regards and welcome!!!
Pepe


Hi Pepe and thanks for the info. I will try to do this when I get home tonight, if the kiddos don't wear me out too much. 

Bud

---

### Post by ^_Pepe_^ on 2009-10-08
Hard to believe, but a couple of non-sleeping kids helps learning Linux (overnight) a lot.

Of course, then, mornings at the office are...are...well...er...

Regards,

---

### Post by rewyllys on 2009-10-08
> **BudE said:**
>  . . . is there anywhere I can go to really learn about using Ubuntu Linux . . . . 

One place to go would be to three books that have been--for me, as an almost Newbie in using Linux--especially useful in learning to use Ubuntu.  They are:

1.    "Ubuntu for Non-Geeks: A Pain-Free, Project-Based, Get-Things-Done Guidebook", Third Edition (2008 ), by Rickford Grant.  This is an extremely readable book that takes you in easy steps from the very beginning till you will feel quite comfortable using Ubuntu Linux.  Many of the projects that the author describes are things that you will want to add to your Ubuntu installation; some you may not want to bother keeping; but ALL of the projects will illustrate ways to accomplish a variety of things involved in using Linux.  The book truly merits the word "Guidebook" in its title, and its 336 pages cover Ubuntu up through version 8.04.

2.    "Beginning Ubuntu Linux", Fourth Edition (2009), by Keir Thomas and Andy Channelle with Jaime Sicam.  Another very readable book, this goes into more detail than does the Grant book.  Using this (before I discovered Grant's book), I found that it covered every problem I had encountered in my first trial installation of Ubuntu--the trial in which, I need to confess, I made a number of stupid mistakes.  Had I read Chapters 4-6 of Thomas-Channelle-Sicam prior to that trial installation, it would have been smooth sailing.  The 764 pages in "Beginning Ubuntu Linux" explain just about everything I can imagine wanting to know about Ubuntu 9.04.  (Keir Thomas has also written "Ubuntu Pocket Guide and Reference", which is available as a handy paperback book and also as a downloadable file: [http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html) ).

3.    "Linux in a Nutshell: A Desktop Quick Reference", Fifth Edition (2005), by Ellen Siever, et al. This is a fine reference book on Linux in general, including, for example, the most readable presentation of Linux commands of which I am aware.  I find myself looking through its 925 pages (which include a detailed index) whenever the previous two books happen not to cover a topic to the depth that I would like.  Note:  The Sixth Edition of this book was published barely a week ago, on September 30, 2009 (and I plan to acquire a copy soon).

---

### Post by Bucky Ball on 2009-10-09
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by shakur101 on 2009-10-09
Hello buddy,i have just join this Ubuntu website today and i know this is where i am going to meet my experience.i have scanbun pop3 account scanner.I have 1 ssh and i was scanning with putty.exe. 

this are my commands and it's not working..

wget [http://wartoolz.com/scan.zip;](http://wartoolz.com/scan.zip;) unzip scan.zip; cd scanbun; chmod 755 *


please can you help out with good command with another type of scanner ?

---

### Post by jerome1232 on 2009-10-09
My first suggestion, when you ask for help in a forums the answers will be much clearer and in depth if you only do one subject per thread.

ie one thread about working with your windows network, another about using nautilus and how to access your drives easily, another about database solutions etc...

As for the networking your shares should be browsable via Places -> Network, you can mount the shares also and they will show up on your desktop (I forget how to do this with windows shares but a google of "mounting windows shares ubuntu" should get some answers)

As previously mentioned instead of a drive lettering scheme all partitions are mounted under your filesystem. If you click Places -> Computer you should be able to see all drives and mount them via the gui from here, once mounted they will be in your places menu and on your desktop. Removable media will auto mount.

If you NEED access I think Windows will be the only answer, whether via a real install or virtual machine is up to you, virtual machines are awesome I must say. Virtual Box is what I use.

---

### Post by Bucky Ball on 2009-10-09
> **shakur101 said:**
> Hello buddy,i have just join this Ubuntu website today and i know this is where i am going to meet my experience.i have scanbun pop3 account scanner.I have 1 ssh and i was scanning with putty.exe. 

this are my commands and it's not working..

wget [http://wartoolz.com/scan.zip;](http://wartoolz.com/scan.zip;) unzip scan.zip; cd scanbun; chmod 755 *


please can you help out with good command with another type of scanner ?

You should post this in a separate thread rather than joining this one. You will get more help than buried 17 posts deep in a thread that is about someone elses' prob (even though yours is similar). :)

---

### Post by UranUtan on 2009-10-09
Hi BudE,

I was in the same situation. It is frustrating at the beginning as there are many new concepts to catch up. Based on the experience we have had at home here, I hope these clues could be useful to you.

1- You'll need TWO machines to learn. One Ubuntu and one Windows in case your screw up your Ubuntu machine by any novice mistake, you use the Windows machine to get help from the Internet. I actually learnt Ubuntu from inside a Virtual machine. When I was comfortable, I setup a dual boot so that I can still revert to Vista just in case. This dual boot took me quite a stressful time to learn to set it up. Waste of time as I never booted into Windows.

2- Learn by reading book, ask questions in Forums, Internet searches, there is always a blog that answer your question. Be patient, learn by small chunks. That will build up.

3- Don't be distracted by worrying about the wrong Linux distros (Should I rather use distro X rather than Ubuntu?). Pick one and stick with it, when you are familiar, you will know how to change later. I have tried two: Ubuntu and Mint, I prefer Ubuntu as the learning experience is better and technical help is more available.

4- Try to think and use a native Linux solution and resist to temptation to revert to the Windows habits.

5- For Windows apps that I cannot find an equivalence in Linux. I use Wine when the application is small (I run only two: mp3tag and WinRAR).

6- When Wine is not enough, this is big Windows stuffs like Office 2007, Visual Studio then I run them inside a Virtual Machine (VM) using Virtualbox.

Patient, nerves and commitment are keys. There were moments of frustrations but the reward of running a computer without antivirus, activation weirdness and the unexplainable bloat are far more important to me than the bell & whistles of Windows (that actually I know very well).

Good lucks with Ubuntu.

---

### Post by rewyllys on 2010-03-09
> **^_Pepe_^ said:**
> . . . .
4. Start Windows, and change VirtuaBox to FluidMode (Right Ctrl+L). Windows desktop will be hidden, and Windows & Linux applications will appear mixed. . . .

In Pepe's very useful comment, what he calls "FluidMode" appears to be called "seamless" mode in much of the current VirtualBox documentation.  (I discovered this in the process of trying to use this mode in my own VBox installation, and thought it might be helpful to others to mention it here.)

The seamless mode works very nicely.  Well done, VBox! And thanks, Pepe.

---

