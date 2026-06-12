---
title: "I am thinking of switching from Windows, please help"
date: 2011-08-03
forum: General Help
---

### Post by lovenhim on 2011-08-03
Hello everyone.  I consider myself to be a PC user.  I am not a geek but I do enjoy computers as a hobby.  I do not work in IT but rather am a house husband.  I am trying to go back to college after many years out of school.  I will be taking Online classes.  I am thinking about switching from WinXP because I am tired of viruses, malware and working on the thing all the time with defrags and scans and such.  I want a simple to use machine for these tasks:

web surfing
writing papers for college
music
watching movies
iPod use for the classic and shuffle

I am over MS costing money....hundreds of $$$ for Win7 and MS Office 2010....even with student discounts.  Where should I start?  My computer has these specs:

laptop
2.6Ghz Intel dual core CPU
64bit
4GB RAM
500GB HDD & 2TB USB HDD
512MB video

Do I need to know the command line to use Linux or can I simply use it in the GUI without having to "geek out" and have a steep learning curve?  

Thank you for the help.

---

### Post by pqwoerituytrueiwoq on 2011-08-03
i suggest the using the LTS much less headache for a beginner
[LIST]
[*]web surfing
 easy out of the box
i suggest updating firefox like this after a clean install of ubunut 10.04.x
```
sudo add-apt-repository ppa:mozillateam/firefox-stable;sudo ap-get update;sudo apt-get install firefox
``` type password (yes i know you cant see your typing just do it and press enter) and you will be good to go
[*]writing papers for college
 easy out of the box
[*]music
 easy out of the box
   you will be prompted to install mp3 support when you need it just click ok/next and you will be good to go
[*]watching movies
 for dvd's a copy paste in the command line 
 ```
sudo apt-get install libdvdread4;sudo /usr/share/doc/libdvdread4/install-css.sh
``` type password (yes i know you cant see your typing just do it and press enter) and you will be good to go
 for flash install [flash aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")
[*]iPod use for the classic and shuffle
 should work out of the box
 i use this on my shuffle [http://shuffle-db.sourceforge.net/](http://shuffle-db.sourceforge.net/)
[/LIST]
here is the torrent for the 64 bit lts [http://releases.ubuntu.com/lucid/ubuntu-10.04.3-desktop-amd64.iso.torrent](http://releases.ubuntu.com/lucid/ubuntu-10.04.3-desktop-amd64.iso.torrent)

---

### Post by Mr.Kappa on 2011-08-03
Actually 90% of the time when you install Ubuntu everything works out of the box. I recommend you try it on a live cd or usb stick before installing it on your hard drive to see how it works.
When you're ready to install it you can also leave your windows partition intact and keep using it along side with ubuntu.
All the applications you need (firefox,libreoffice,banshee,totem) there are already installed and do not require the command line, actually on the newer ubuntu versions the terminal (command line) is not very used :(
If you need any help installing/using/loving ubuntu you can ask here on the forums! :P

---

### Post by LMP900 on 2011-08-03
Ubuntu should be fine for the uses you have listed, although you might want to do some research on iPod compatibility as I do not own one. If LibreOffice does not suit you, the browser-based office suite GoogleDocs is a good alternative. As far as the command line goes, I often use it by choice, but it has been quite some time when I have had to use it because I didn't have any other options.

One last thing, make sure the courses you are taking will not require the MS Office Suite. Several of the courses I took required Excel. Good luck in your courses and have fun using Ubuntu.

---

### Post by irv on 2011-08-03
From your specs there's more then enough room to run Windows and Ubuntu Linux side by side. The reason I say this is because you watch movies. If you have Netflix you will need Windows because Netflix does not support Linux on a PC. It will support boxes like Roku which runs Linux but does not support it on a PC. 
	
You can do everything else you mentioned on your list. As far as the GUI you can do just about everything you could do in a terminal but after awhile you will find out using the terminal is easy and fun, and much faster then doing things in the GUI. Windows has brainwashed us in thinking there way is better but it is not. 

When I installed the 11.04 version I installed the 64bit, but now I wished I would have installed the 32bit because I have some issues with Java on some webpages. I never had these problems with the 32bit. When 11.10 comes out I am going to do a clean install with the 32bit version. 

When you do the install it will walk you through it, it is straight forward and easy. The help out here on the forum is also great. Hope this helps.

---

### Post by nothingspecial on 2011-08-03
> **lovenhim said:**
> Hello everyone.  I consider myself to be a PC user.  I am not a geek but I do enjoy computers as a hobby.  I do not work in IT but rather am a house husband.  I am trying to go back to college after many years out of school.  I will be taking Online classes.  I am thinking about switching from WinXP because I am tired of viruses, malware and working on the thing all the time with defrags and scans and such.  I want a simple to use machine for these tasks:

web surfing
writing papers for college
music
watching movies
iPod use for the classic and shuffle

I am over MS costing money....hundreds of $$$ for Win7 and MS Office 2010....even with student discounts.  Where should I start?  My computer has these specs:

laptop
2.6Ghz Intel dual core CPU
64bit
4GB RAM
500GB HDD & 2TB USB HDD
512MB video

Do I need to know the command line to use Linux or can I simply use it in the GUI without having to "geek out" and have a steep learning curve?  

Thank you for the help.

Hi I am also at home studying distance courses.

I surf the web
write papers for college
have a enourmous music collection
watch movies
and have both an iPod classic and shuffle (but I prefer my sansa clip+)

We only have linux in the house (My kids have never clicked the "Start" button at home)

I do know my way around the command line, but my wife has been using linux exclusively for over 5 years and wouldn't know how to open a terminal if her life depended on it. She also does all of the above.

Just remember it's different, go with the flow, don't try and make it work like windows, let it work like Ubuntu and you will be fine.

---

### Post by DangerOnTheRanger on 2011-08-03
Hi, and welcome to the forums! :)
Let me see if I can answer your questions:

> 
Do I need to know the command line to use Linux or can I simply use it  in the GUI without having to "geek out" and have a steep learning curve?   
No, knowledge of the command-line (normally called the "terminal" on Linux) isn't necessary, at least for Ubuntu Linux. However, as you've already seen, the preferred method of giving solutions here are terminal commands, for several reasons:

[LIST]
[*]They work no matter what version of Ubuntu you're running
[*]They're much quicker than using an equivalent GUI application (if one exists - besides, a GUI app's interface might change across Ubuntu releases)
[*]They still don't require knowledge of the terminal to run - just open up a terminal (Applications > Accessories > Terminal on Ubuntu Lucid Lynx [10.04]), copy-paste the posted terminal command, and press Enter. It's that simple!
[/LIST]
> 
 I want a simple to use machine for these tasks:

web surfing
writing papers for college
music
watching movies
iPod use for the classic and shuffle
I myself use Ubuntu for all of those tasks (except for the iPod one - I don't own one of those): I can watch YouTube videos, watch movies, write documents, listen to music, and much more, so I think Ubuntu will suit all your needs. Netflix doesn't support Linux yet though, so if you use Netflix to watch movies, you might need to keep a Windows installation around on your hard drive.

Some other things I think you'll find useful as you take your first steps in Ubuntu are:

[LIST]
[*]WINE (Wine Is Not an Emulator) - a program that allows you to run most Windows program inside Ubuntu. Install it with this terminal command: ```
sudo apt-get install wine
```Remember, you'll have to type your password in, but it won't be seen on-screen (in case someone is looking over your shoulder). Just type it in anyway, and press Enter.
[*]The Ubuntu Software Center - a giant (over 40k apps on my machine) repository of free and open-source applications that you can install with a single mouse click (in fact, it's a GUI front-end to that [FONT=Courier New]apt-get[/FONT] command you installed WINE with). In Ubuntu 10.04 (Lucid Lynx), it's available at Applications > Ubuntu Software Center.
[/LIST]
If you have any questions, don't be afraid to ask - that's what these forums are for! :)

---

### Post by krytorii on 2011-08-03
If you want to try it out first (not from a cd where you can't save changes), try using [wubi]("http://www.ubuntu.com/download/ubuntu/windows-installer"). It'll install ubuntu sort of inside windows. You can try it out, and then if you don't like it, uninstall it like anything else in windows. If you like it, you can install ubuntu properly later.

Also,  would recommend using Lucid, rather than natty for someone who is hesitant. You can customise the appearance more. Having your own personal layout makes a computer feel more like yours and less like a generic giant calculator. Plus there have been quite a few people who have not like the newest release

---

### Post by blane2 on 2011-08-03
To make your transition less painful, you can start using linux software on your windows machine to get a feel for most of the software.

Netflix doesn't work with linux.

---

### Post by lovenhim on 2011-08-03
I do not have Netflix but I do have Last.fm that I use.  Thanks for all the great help.  :)

---

### Post by Maheriano on 2011-08-03
Windows 7 on the student discount is $30. what are you talking about with hundreds of dollars?

---

### Post by krytorii on 2011-08-03
> **Maheriano said:**
> Windows 7 on the student discount is $30. what are you talking about with hundreds of dollars?

Even if it works out at $30 for windows (which I find rather surprising), you "need" things like office, norton and so on which all cost money.

---

### Post by blane2 on 2011-08-03
> **krytorii said:**
> Even if it works out at $30 for windows (which I find rather surprising), you "need" things like office, norton and so on which all cost money.

It's $35 with a student discount (no joke)
Office can be replaced with libre office, and norton is crap compared to free alternatives like AVAST!

There is a TON of free, and open source software available for windows. 

My typical windows setup
----------------------
Anti-virus = avast $0
browser = firefox + adblock plus $0
media player = VLC + itunes $0
Office programs = LibreOffice $0
Pdf Reader = Foxit $0
image editing = Gimp
Painting program = MyPaint $0


windows doesn't have to cost an arm and a leg. Most of the above programs are available for linux too.
You do need to maintain your windows system (no getting around that)

But if you use those programs on your windows machine, and get used to them after that all you have to learn is the way ubuntu's desktop manager works.

---

### Post by Maheriano on 2011-08-04
> **blane2 said:**
> It's $35 with a student discount (no joke)
Office can be replaced with libre office, and norton is crap compared to free alternatives like AVAST!

There is a TON of free, and open source software available for windows. 

My typical windows setup
----------------------
Anti-virus = avast $0
browser = firefox + adblock plus $0
media player = VLC + itunes $0
Office programs = LibreOffice $0
Pdf Reader = Foxit $0
image editing = Gimp
Painting program = MyPaint $0


windows doesn't have to cost an arm and a leg. Most of the above programs are available for linux too.
You do need to maintain your windows system (no getting around that)

But if you use those programs on your windows machine, and get used to them after that all you have to learn is the way ubuntu's desktop manager works.

Ya, really. I bought it, the deal was $30 in the USA and $40 in Canada, so I got Windows 7 for $40. And I got Office 2007 on the student discount for $64. I still fail to see where it's hundreds of dollars.

Though I never installed either of them, I gave them to my brother.

---

### Post by lovenhim on 2011-08-04
Hello everyone.  I have good news.  I have been accepted @ Liberty University for an Online BA in Religion....I just found out about it this morning.  I also have Ubuntu 11.04 up and running.  I installed VLC media player and Wine using the package manager.  I love that feature, why Windows does not have that is interesting to me.  Ubuntu gave me a message that said something to the effect that my computer does not have the resources to run the new interface so it defaulted back to Ubuntu Classic on login.....does that mean anything good or bad?  I also found under System/Administration the additional drivers link.  In there it found a driver for my NVIDIA video card and I used the recommended driver for that.  I am trying to learn as I go, so far I like it because you can get what you need from the system itself rather than look all over the web for software like in Windows.  I also setup Ubuntu One but have not done a chat client or email client yet.  Thank you for the help.  What should I do next, any more ideas?

---

### Post by irv on 2011-08-04
The reason it went to Classic is because you didn't have NVIDIA video driver loaded. Now that you have your video driver loaded, log Out, and when you go to log back in select Unity. You will find this option at the bottom of the login screen. Hopefully it will load. If there is still a problem in might go back to Classic.

---

### Post by lovenhim on 2011-08-04
I have a problem.  Ubuntu will not let me use my external monitor.  I can normally press alt F2 to switch monitors but nothing happens.  The monitor is connected via HDMI cable from laptop to monitor.  What is going on and how do I fix it?

---

### Post by pqwoerituytrueiwoq on 2011-08-04
> **lovenhim said:**
> I have a problem.  Ubuntu will not let me use my external monitor.  I can normally press alt F2 to switch monitors but nothing happens.  The monitor is connected via HDMI cable from laptop to monitor.  What is going on and how do I fix it?
post what you get from this command
```
lspci | grep VGA
```BTW you don't have to right click copy on Linux 
Just highlight the text ant click where you want to paste it using the wheel on the mouse

which version of ubuntu did you decide on?

are you trying to clone the display or use them like two independent monitors?

---

### Post by lovenhim on 2011-08-04
I am trying to clone a display....use my 22 inch monitor as the only display and not use the laptop display

paul@bedroomlinuxlaptop:~$ lspci | grep VGA
08:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)

Ubuntu 11.04 64bit

---

### Post by kaldor on 2011-08-04
> **lovenhim said:**
> Hello everyone.  I consider myself to be a PC user.  I am not a geek but I do enjoy computers as a hobby.  I do not work in IT but rather am a house husband.  I am trying to go back to college after many years out of school.  I will be taking Online classes.  I am thinking about switching from WinXP because I am tired of viruses, malware and working on the thing all the time with defrags and scans and such.  I want a simple to use machine for these tasks:

web surfing
writing papers for college
music
watching movies
iPod use for the classic and shuffle

I am over MS costing money....hundreds of $$$ for Win7 and MS Office 2010....even with student discounts.  Where should I start?  My computer has these specs:

laptop
2.6Ghz Intel dual core CPU
64bit
4GB RAM
500GB HDD & 2TB USB HDD
512MB video

Do I need to know the command line to use Linux or can I simply use it in the GUI without having to "geek out" and have a steep learning curve?  

Thank you for the help.

You don't *need* a command line. But, I recommend you learn it; I find using the commands to be much more efficient than poking around on a desktop where I need to keep searching for things (that goes for Mac and Windows too for me). The Linux commands are much better than on the Windows command prompt too, imo.

I recommend you install some of the Linux equivelents of the programs you use on Windows first. See how you enjoy using the following:

- Google Chrome, Mozilla Firefox, or Opera for Web Browsing and internet-based activities. 

- Install Pidgin and see how well that works for your IMing needs. If you use MSN, try a program called "emesene".

- Try LibreOffice 3.4 for all of your Office requirements. 

- For movies, music, etc, try the VLC Media player.

I am also going to be taking online classes. The software I need for that is cross platform (Java based) which gives me no headaches. For you, I have no idea how that will work.

From your later posts, I see you have been giving Ubuntu a go. What kind of graphics card do you have? There are a few things related to that to keep in mind. Regarding commands you see here, it isn't because commands are *needed* to do the tasks. It's just very easy for us to be able to write out exactly what we need so you can simply copy/paste what we request. This way, we don't need to direct you via menus and icons and the solutions can come quicker ;)


Edit: I see you have an NVIDIA graphics card. By default, you have the open source (community-developed) drivers. Try enabling the Proprietary Drivers. To do this, use the Additional Drivers program. Check the screenshot I have attached for an example (note I have an AMD card).

---

### Post by leeper69 on 2011-08-04
Ubuntu Linux is easy to use and should work on your laptop if you have a empty partition on your hard drive, if not try the live CD.

---

### Post by pqwoerituytrueiwoq on 2011-08-04
go into nvidia settings
under display settings
next to configuration click configure
select twin view
under position select clone
then click apply
if you figure out how to get both screens with there native resolution let me know
my laptop only shows part of my screen when i use cloned twinview with a larger monitor

---

### Post by lovenhim on 2011-08-04
> **pqwoerituytrueiwoq said:**
> go into nvidia settings
under display settings
next to configuration click configure
select twin view
under position select clone
then click apply
if you figure out how to get both screens with there native resolution let me know
my laptop only shows part of my screen when i use cloned twinview with a larger monitor

I do not see what you are asking me to do.  Twin view is grayed out and I can not click it.

---

### Post by pqwoerituytrueiwoq on 2011-08-04
here is a video i just made
i used a vga output on my monitor as i don't have hdmi
it is less than 40 seconds long
uploading sucks when your upload speed is 160Kbps
i made the video using xvidcap if anyone wants to know
[http://www.mediafire.com/?364tuyb109cp2cu](http://www.mediafire.com/?364tuyb109cp2cu)

---

### Post by lovenhim on 2011-08-04
Alright, I started having other rpoblems with the 11.04 install so now I wiped the computer and am trying 10.04LTS to see what that does.  In when I went to run on the battery my screen flickered in brightness and my volume did the same and it will not detect my external monitor.  I thought Ubuntu "just works" right out of the box.....nope it does not.  LOL  :)  I am joking, I am not upset or anything.  I will try LTS and see what that does.

---

### Post by pqwoerituytrueiwoq on 2011-08-04
> **lovenhim said:**
> Alright, I started having other rpoblems with the 11.04 install so now I wiped the computer and am trying 10.04LTS to see what that does.  In when I went to run on the battery my screen flickered in brightness and my volume did the same and it will not detect my external monitor.  I thought Ubuntu "just works" right out of the box.....nope it does not.  LOL  :)  I am joking, I am not upset or anything.  I will try LTS and see what that does.
if ubuntu 10.04 is not to your liking you can try xubuntu 10.04
[http://www.xubuntu.org/getubuntu#lucid](http://www.xubuntu.org/getubuntu#lucid)
only issue i had when i used it was the theme looks crappy if you install compiz lol

---

### Post by lovenhim on 2011-08-04
My 22 inch external monitor works right out of the box withLTS....wonder why?  I will try this and see what happens.  Now, what add ons of software do I need to add to LTS?

---

### Post by walt.smith1960 on 2011-08-04
> **lovenhim said:**
> Alright, I started having other rpoblems with the 11.04 install so now I wiped the computer and am trying 10.04LTS to see what that does.  In when I went to run on the battery my screen flickered in brightness and my volume did the same and it will not detect my external monitor.  I thought Ubuntu "just works" right out of the box.....nope it does not.  LOL  :)  I am joking, I am not upset or anything.  I will try LTS and see what that does.

11.04 has some pretty big changes compared to 10.04 & 10.10.  If you're not adventurous, stick with 10.04 'til the next LTS - 12.04 has been out about a month. I run 2 Ubuntu installs. One is quite stable, the other is bleeding edge --11.10 now.  But it depends on your inclinations and time.  Most important is to get one install working and DON'T MESS WITH IT!! :lolflag:

---

### Post by lovenhim on 2011-08-04
I am the "tried & true" person, do not need bleeding edge.  I want it to work and not break all the time.  I do not care about a pretty looking OS....I am more interested in an easy to use and reliable OS.  Maybe LTS is for me, so far it is working fine for the hour it has been running and such.  Are there any packages or software that I should install via the package manager?

---

### Post by pqwoerituytrueiwoq on 2011-08-04
> **lovenhim said:**
> I am the "tried & true" person, do not need bleeding edge.  I want it to work and not break all the time.  I do not care about a pretty looking OS....I am more interested in an easy to use and reliable OS.  Maybe LTS is for me, so far it is working fine for the hour it has been running and such.  Are there any packages or software that I should install via the package manager?
see the 1st post i made on this thread

this will get some extra compressed files support
```
sudo apt-get install p7zip-full rar
```

more screensavers (over 200)
```
sudo apt-get install xscreensaver-gl-extra rss-glx xscreensaver-gl-extra
```

go to system->administration->software sources
make sure the 1st 5 boxes are checked and the 1st box ([http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner) is checked under "other sources"
```
sudo apt-get install sun-java6-plugin
```

update the video drivers
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates;sudo apt-get update;sudo apt-get upgrade
```

add google software to the software center
```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add - 
sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
sudo sh -c 'echo "deb http://dl.google.com/linux/earth/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
sudo sh -c 'echo "deb http://dl.google.com/linux/talkplugin/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
```

allow latest version of wine to be installed (runs windows software) 
```
sudo apt-add-repository ppa:ubuntu-wine/ppa;sudo apt-get update
```

fix issue with empathy icon that becomes visible if you remove indicator-messages  
```
cd /usr/share/icons/Humanity/actions/16
sudo ln -s im-message-new.svg notification-message-im.svg
cd ../22
sudo ln -s im-message-new.svg notification-message-im.svg
cd ../24
sudo ln -s im-message-new.svg notification-message-im.svg
sudo gtk-update-icon-cache -f /usr/share/icons/Humanity/
cd ~
```

---

### Post by marianlibrarian on 2011-08-04
4 years ago, I came here an absolute complete Nubee. I needed help setting up public access computers for a small rural public library. There were some fits and starts and some tears - but I always got the help I needed and some kind words and lots of encouragement from this forum. Our library still runs a modified version of Ubuntu called Groovix. It is the best Kiosk and is specifically made for public libraries. Our two staff computers also have Ubuntu. 

I highly recommend Ubuntu!

@ Mr. Kappa I still use the command line!!! My library server (Debian) does not have any kind of interface and I love it.

---

### Post by lovenhim on 2011-08-04
I get this when I try and run any of that code in a terminal:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Ms_Angel_D on 2011-08-04
> **lovenhim said:**
> I get this when I try and run any of that code in a terminal:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Make sure you don't have ubuntu software center open or synaptic package manager when you run that command. The reason for that error is because you can only access apt with one program at a time.

---

### Post by pqwoerituytrueiwoq on 2011-08-04
> **lovenhim said:**
> I get this when I try and run any of that code in a terminal:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
you have a package manager running
close the software center/synaptic
you may have have a terminal installing software

---

### Post by lovenhim on 2011-08-04
I restarted the system and did this all again....it seemed to work this time.  Java gave an error message though so I am not sure that it installed.

---

### Post by scouser73 on 2011-08-04
As has been previously mentioned, you could try Ubuntu via the live cd and see how you think it will best suit your needs.  The specifications that you stated will work very well with Ubuntu, 

> web surfing
writing papers for college
music
watching movies
iPod use for the classic and shuffle

Web Surfing is excellent under Linux as there are no known viruses in the wild that would affect your PC if you stumbled onto a malware website.

Ubuntu comes pre-loaded with LibreOffice which is an office suite that it has Base, Calc, Draw, Impress, Math & Writer.  It is constantly being developed upon and as and when new iterations are released then you can wait for the version to be updated or you can download and install it.

Banshee Music Player comes as standard with Ubuntu and is an excellent media player, if you don't like using Banshee then you can simply remove it and install another application such as Rhythmbox or one of many others that are available in the Ubuntu Software Centre.

For watching movies there is the Totem Movie Player which is good, but I would suggest that you install VLC Media Player which can handle loads TV & Film media.

As for iPod use I hope that someone else can better advise you on how to get the best from that.

I would also like to suggest that you install Ubuntu Tweak which comes with a wide range of software and not only that but it will also make your use of Ubuntu that much better.

Using the command line isn't a necessity but you may find it useful.

You can always use the forums to find answers and if you can't see an answer then please ask as I'm sure that there will be people ready and willing to help you.

---

### Post by pqwoerituytrueiwoq on 2011-08-04
> **lovenhim said:**
> I restarted the system and did this all again....it seemed to work this time.  Java gave an error message though so I am not sure that it installed.
you can always try to install it again it will tell you if it got in
did you accept the agreement? if not it is not installed
you can install adobe reader if you want pdf file to be displayed inside firefox

if you like playing with graphic effects
you will enjoy this one
```
sudo apt-get install compizconfig-settings-manager compiz-fusion-plugins-extra
```
System -> Preferences -> CompizConfig Settings Manager

---

### Post by lovenhim on 2011-08-04
This is fun and a tad confusing at the same time.  :)

---

### Post by pqwoerituytrueiwoq on 2011-08-04
> **lovenhim said:**
> This is fun and a tad confusing at the same time.  :)
the massive anmout of effect options can get overwhelming immaging if there were as many effects as screensavers
screensaver marathon :popcorn:
if you installed them there is one called web college it displays random images from the Internet including x rated ones just warning you be nice if you could disable individual screensavers like you can on xubuntu

---

### Post by lovenhim on 2011-08-04
Ubuntu 10.04 is neat in the fact that my file backups such as pictures, videos, music, etc all transferred into Ubuntu with no issues and the things I have tried all work.  :)  I am liking Ubuntu so far.

---

### Post by pqwoerituytrueiwoq on 2011-08-04
the only glitches i have encountered where at login my panel did not load properly but game no error popups 
changing size of panel back and forth fixes this (odds about 1 out of 20)
some times a applet failed to load a error message comes up i click don't delete and run *killall gnome-panel* (odds 1 in 175 ish)
and from time to time my title bars do not load i just run *gtk-window-decorator  --replace &* to fix that when it happens
if you want your music to play at login let me know i made something to get that working

---

### Post by Rodney9 on 2011-08-04
[http://ubuntuforums.org/showthread.php?t=1469825&highlight=complete](http://ubuntuforums.org/showthread.php?t=1469825&highlight=complete)

Ubuntu Desktop Computing Made Easy (Lucid Lynx v10.04) Thanks to TrakerJon

I always use this [page]("http://ubuntuforums.org/showthread.php?t=1469825&highlight=complete") to get my Ubuntu 10.04 working the way I want or this [page]("http://ubuntuforums.org/showthread.php?t=1602315") for 10.10

---

### Post by Lighthorse01 on 2011-09-10
> **Maheriano said:**
> Ya, really. I bought it, the deal was $30 in the USA and $40 in Canada, so I got Windows 7 for $40. And I got Office 2007 on the student discount for $64. I still fail to see where it's hundreds of dollars.

Though I never installed either of them, I gave them to my brother.

Well that is fine if you are a student. If you aren't you have to pay full price.

What I paid
Windows 7 Pro $150.00
Microsoft Office 2007 $185.00
Adobe Photoshop CS5  $550.00
plus a lot more programs. Not every one has the ability to buy at student discounts.
so yes it does add up. Hell my copy of AutoCAD cost over $3000.00
and Im sure you can get it for $100 as a student .

---

### Post by JonM33 on 2011-09-10
> **lovenhim said:**
> Hello everyone.  I consider myself to be a PC user.  I am not a geek but I do enjoy computers as a hobby.  I do not work in IT but rather am a house husband.  I am trying to go back to college after many years out of school.  I will be taking Online classes.  I am thinking about switching from WinXP because I am tired of viruses, malware and working on the thing all the time with defrags and scans and such.  I want a simple to use machine for these tasks:

web surfing
writing papers for college
music
watching movies
iPod use for the classic and shuffle

I am over MS costing money....hundreds of $$$ for Win7 and MS Office 2010....even with student discounts.  Where should I start?  My computer has these specs:

laptop
2.6Ghz Intel dual core CPU
64bit
4GB RAM
500GB HDD & 2TB USB HDD
512MB video

Do I need to know the command line to use Linux or can I simply use it in the GUI without having to "geek out" and have a steep learning curve?  

Thank you for the help.

I doubt you paid for your Windows 7. Most new computers come with it. Regarding Office, I can understand that crazy price but there's LibreOffice for Windows as well as Linux.

---

### Post by irv on 2011-09-13
> **JonM33 said:**
> I doubt you paid for your Windows 7. Most new computers come with it. Regarding Office, I can understand that crazy price but there's LibreOffice for Windows as well as Linux.

When you made the comment "I doubt you paid for your Windows 7, Most new computers come with it." is not a true statement. I am an ex-computer manufacture/dealer and every computer I build/sold I had to add the cost of Windows to the computer when I priced it to my customers. So you see you do pay for Windows, now or later when you buy a new PC. It's the same with a Mac you pay for the OS with the hardware.

---

### Post by marianlibrarian on 2011-09-14
Well said irv. When I purchased computers for our library, I specifically asked that no operating system be installed. I installed Ubuntu. Each machine was about $280. 

Every now and then I come across people who are shocked to find that public libraries have to "purchase" books.

---

### Post by marianlibrarian on 2011-09-14
Hmmm... I guess I held the enter key down to long and made a double post.

---

### Post by irv on 2011-09-16
> **marianlibrarian said:**
> Well said irv. When I purchased computers for our library, I specifically asked that no operating system be installed. I installed Ubuntu. Each machine was about $280. 

Every now and then I come across people who are shocked to find that public libraries have to "purchase" books.

I wish people would think when they see the word "Public", That means it belongs to the people but that it is also paid by the people, (tax dollars). I try to make donations to our public Library, schools, etc. It would be nice to talk our elected officials into using open source software and quit spending tax payers money to MS.
Just my two cents worth. If I can use open source why can't our government?

---

