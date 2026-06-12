---
title: "Avast Finds Viruses but Cannot Move to Chest!"
date: 2012-07-31
forum: General Help
---

### Post by fapestar on 2012-07-31
I'm trying to quarantine a virus on a outside hard drive and everytime It finds a virus it say not to worry and choose to delete or move to chest. 

It recommends to move to chest but I get an error message saying cannot move to chest...no such directory exist. It also says it could not rename it. 

Is the virus nutralized or should I expect it to still be active. 

I haven't reinserted the original HDD yet back into the computer it came from, but it was one of those viruses that currupted how you're bios booted and cause bios screen restarts.

But my main question is did Avast fix the problem, or is it saying it couldn't do  anything for me. 


and also, how many viruses out there are dangerous for Windows AND linux? I've been scanning infected hard drives on Ubuntu and Knoppix thinking that the viruses will not hurt the linux OS. Am I mostly right or sadly mistaken?

---

### Post by GreatDanton on 2012-07-31
> **fapestar said:**
>  I've been scanning infected hard drives on Ubuntu and Knoppix thinking that the viruses will not hurt the linux OS. Am I mostly right or sadly mistaken?

At this time there are no known viruses for Linux. There were some in the past, but nothing serious (I can't remember the name of the site where I saw this info).

For the rest of your text I can't tell you what is wrong. The best solution you will get at Avast forums --> [http://forum.avast.com/index.php?board=2.0](http://forum.avast.com/index.php?board=2.0)

Hope this helps.

Regards.

---

### Post by GreatDanton on 2012-07-31
It's not the link I was looking for but anyway: [https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

---

### Post by houseworkshy on 2012-07-31
It could be a permissions problem, especially likely if the hdd was under a differant user name and password.
  
I used to like saying there are no viruses for linux.  Sadly this is no longer true.   There are viruses that affect linux though ususally one has to be socially engineered to install them.  [https://en.wikipedia.org/wiki/Linux_malware](https://en.wikipedia.org/wiki/Linux_malware)   
Also virtual machines, such as java in a browser, or visual basic for cross platform stuff,  can get infected even if the main system is not afftected.  Apparmour helps against that sort of thing.  
For an open source antivirus I like clamAV, and for detecting rootkits rkhunter is good. 
Some good habits are:
Password lock your bios.  
Set up the firewall and enable the firewall "sudo ufw default deny" and "sudo ufw enable" will get to you the default on a new install, though you have a firewall in Ubuntu freshly installed it is not turned on by default.   
Know the source of things you install and be cautious of adding repros.
Create a none admin' account for general internet activity.
Be aware when sudo is running and "sudo -k" it when it's not needed.
Don't let programs have root access if they don't need it.  wine for example lists / ( which is root ) as one of the drives it can read and write to when first installed.  So it can partially inherit admin system powers from being installed.  Handy for being able to open a windows .exe from anywhere but not really nessesary if you don't mind putting it's .exe's on the virtual drive it creates.  So remove that. 
Put and configure trusted protective addons in your browser, no-script in firefox for example.
Backup to external media just in case. Even if there was no such thing as malware things go wrong anyway.
Scan the lot occasionally.

---

### Post by fapestar on 2012-08-04
Thanx for that info on the firewall brother. I didn't realize that the software firewall was not automatically active. It is now. 

i"m a noob at ubuntu, I used to use Knoppix soleley for recovering data on compromised windows machines. 

Although you have gave me a lot of knowledge I was talking about using Ubuntu to scan an external drive of which I don't use and belonged to another persons computer. 

Rootkit's would take over the bios for example and cause restarts. I found deleting gives me less problems than move to chest. 

However, I don't know how viruses cause a bios to reset. 

I used to just load Bios defaults and or Remove the Cmos battery or short the Cmos pins to reset and I can get pass bios...but these new viruses won't let you. 

Sometimes, If I have an infected HDD connected to one of my computers and even though I havn't fully booted up, it won't allow any of my logical partitions with xp or win 7 get into safe mode. 

Basically I was trying to find a way that I can't remove rootkits and viruses withough having to do a System Recover or Clean install.

---

### Post by mastablasta on 2012-08-05
it seems that is a rootkit which are not depending on OS.

some antivirus porgrammes can remove them but usually the free ones are not good at that. if you managed to find a specific  rootkit and know it' sname it might pay off to find something on the net. i once remember having this virus that simply won't remove until i found a tool made by a desperate dude. it worked great in my version of the virus/rootkit. he tried to keep up with the virus makers but eventually decided he doesn't have resources to keep upgrading the tool.

---

### Post by fapestar on 2012-08-06
Yeah, I figure Clean installs will save me the most time. I guess there is no easy way to fix rootkits...I won't even waste time trying to scan for systems that badly infected. 


But I was wondering, by doing the ufw comand up there to enable firewall, is that permanent?

---

### Post by houseworkshy on 2012-08-06
It should last untill you tell it not too.  "sudo ufw status" will tell you how it stands.  To read up on it use the inbuilt help; the manual pages for any command can be accessed with "man" typed in front it.  "man man" will tell you how to use it.  In this case "man ufw" will take you to the firewalls manual.  A quick "man sudo" would also be worth looking at, along with being the most common command posted it is also the one should be most cautious of using. If you don't recognise a command in a guide or something posted in a forum, man the things you don't recognise.  There have been reports of malicious postings, I haven't seen it but there is a sticky about it at the head of this forum. Useful way of learning too.
Well worth getting used to the man pages as it is one form of help which is always available for any linux, even offline.  Whichever of the hundreds of flavours of linux you use almost all the commands are the same, variations are only things like package management, so if you know them you'll know your way round any distribution.
There are a few graphic firewall managers, gufw for example.  They tend to come in with their own defaults so readup before using.  I don't bother.
If you're new to Ubuntu, this is a good start
[https://help.ubuntu.com/](https://help.ubuntu.com/)  gives a good overview and the chance to install stuff if you want.  
This is a very handy free pdf to have living on the drive [http://ubuntu-manual.org/](http://ubuntu-manual.org/)
Whilst knowing the command line is really useful it's a bit deep end, bit like putting windows on and starting with cmos.  So the two links above are probably better places to start.

Oh and as an aside I prefered the ClamAV package to Avasti.  Mostly because ClamAV is fully free and open source so they have no incentive in holding anything back, even the engine gets updated every few months.  Back in the windows days I always used something free usually one year trials of fully featured ones.  I may have the order I used them wrong, it was a long time ago, but definately started with Norton proffesional, then Macafee, then AVG, then Kapersky, then Avasti, and finally Clamwin, a version of ClamAV modified for windows, and it found stuff that had been living there since Norton and right through the others.  ClamAV doesn't talk to you, which is a pity as I like that old sci-fi film-like feeling,  but it's very good at digging out viruses.

---

### Post by fapestar on 2012-08-06
> **houseworkshy said:**
> It should last untill you tell it not too.  "sudo ufw status" will tell you how it stands.  To read up on it use the inbuilt help; the manual pages for any command can be accessed with "man" typed in front it.  "man man" will tell you how to use it.  In this case "man ufw" will take you to the firewalls manual.  A quick "man sudo" would also be worth looking at, along with being the most common command posted it is also the one should be most cautious of using. If you don't recognise a command in a guide or something posted in a forum, man the things you don't recognise.  There have been reports of malicious postings, I haven't seen it but there is a sticky about it at the head of this forum. Useful way of learning too.
Well worth getting used to the man pages as it is one form of help which is always available for any linux, even offline.  Whichever of the hundreds of flavours of linux you use almost all the commands are the same, variations are only things like package management, so if you know them you'll know your way round any distribution.
There are a few graphic firewall managers, gufw for example.  They tend to come in with their own defaults so readup before using.  I don't bother.
If you're new to Ubuntu, this is a good start
[https://help.ubuntu.com/](https://help.ubuntu.com/)  gives a good overview and the chance to install stuff if you want.  
This is a very handy free pdf to have living on the drive [http://ubuntu-manual.org/](http://ubuntu-manual.org/)
Whilst knowing the command line is really useful it's a bit deep end, bit like putting windows on and starting with cmos.  So the two links above are probably better places to start.

Oh and as an aside I prefered the ClamAV package to Avasti.  Mostly because ClamAV is fully free and open source so they have no incentive in holding anything back, even the engine gets updated every few months.  Back in the windows days I always used something free usually one year trials of fully featured ones.  I may have the order I used them wrong, it was a long time ago, but definately started with Norton proffesional, then Macafee, then AVG, then Kapersky, then Avasti, and finally Clamwin, a version of ClamAV modified for windows, and it found stuff that had been living there since Norton and right through the others.  ClamAV doesn't talk to you, which is a pity as I like that old sci-fi film-like feeling,  but it's very good at digging out viruses.

I was going to use clam av, but post on how to download it are over a year old, and the commands are not working..thanx for all the help...i'm going to start watching linux + nuggets to get even more use to it. 

But can you direct me to current clamav download tutorial, because I gave up after an hour of trying to download it.

---

### Post by houseworkshy on 2012-08-06
Do it from inside the system, as you are on linux that is always best. It's not like windows where you pull in an .exe from outside and run it.  Use the "software centre" or "synaptic package manager" which pulls only from tested software collection called repositories.  3rd party repositories can be added but don't do it until you know what your doing or perhaps never.  I'm guessing that you are on 12.04 and I'm not ofey with that one, as I'm still on an older version, so consult the documentation.  The pdf I suggested above would guide you through the entire setting up the system process, including installing and using an anti-virus.
  
With command lines it would be "sudo apt-get install clamav" and "sudo apt-get install freshclam" which is the virus database updater. "man clamscan" would tell you how to use the antivirus scanner, and "man freshclam" would show you how to update the database.    The manual pages for a package should be pulled in when the package is installed so untill 'apt-get install whatever' has been done 'man whatever' won't work.  The last is only an imagined example; I'm not aware of any program called 'whatever' though someone's bound to write one.  Possibly for pulling in wallpapers of bikini babes for surfer dudes but it'd most likely be from some untested 3rd party repository and full of malware so I wouldn't trust it.

There is also a gui called  clamtk for clamav, which would probably pull the rest in if installed, using it that way might be more straight forward.  All that said, I'm not knowlagable about 12.04, which has a differant GUI and therefore may have changed the GUI way of doing it,  so you would fare better using that pdf or waiting for someone who knows 12.04 better than I to pipe up.

---

### Post by gifford on 2012-08-06
unfortunately, there are viruses and malicious programs that can infect Linux. Best to practice safe downloading of files and programs. My experience with malicious files has been with java and emails containing malware from windows users. I use BitDefender to scan with at least once per week. It is a good program just a little difficult to install.

---

### Post by fapestar on 2012-08-09
> **gifford said:**
> unfortunately, there are viruses and malicious programs that can infect Linux. Best to practice safe downloading of files and programs. My experience with malicious files has been with java and emails containing malware from windows users. I use BitDefender to scan with at least once per week. It is a good program just a little difficult to install.


I really like Avira for Windows, it stops malicious java code from running, stops your 1st level dns from being altered (host file) it's like a second, more effective UAC...which some don't like but I do.  

I like to sometimes go to Worldstarhiphop.com which i know has malicious code running from thier disquss comment section. 


So the same malicious code that affects windows will also effect Linux...or Ubuntu. Or is the code that is run have to be specifically for linux?

.....If there is code running is avast good enough. or even clam?

---

