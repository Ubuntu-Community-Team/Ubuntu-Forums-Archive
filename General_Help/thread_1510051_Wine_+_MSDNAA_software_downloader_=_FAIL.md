---
title: "Wine + MSDNAA software downloader = FAIL"
date: 2010-06-15
forum: General Help
---

### Post by joedanj on 2010-06-15
Hi,

I'm totally new to ubuntu. Sorry.
I tried to download software from my MSDNAA account using wine. 

I installed wine from ubuntu software center, i went into terminal and wrote ```
winecfg
```, a window appeared and I clicked ok.

Then I went into properties of the downloaded .exe file and allowed it to execute. And then I double clicked it and then I pushed the button to download, but it got stucked there. What might be the problem?
Thanks.

---

### Post by Mark Phelps on 2010-06-15
Wine is not the miracle cure many make it out to be; at best, it only runs some MS Windows apps.

You should go to the WineHQ application compatibility site at the link below and do a search on the apps you're trying to install:

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

Anything not listed, or not rated Gold or better is going to be a waste of time with Wine.

Also, you should post your Wine-related questions in the Wine subforum.  You will get faster and more detailed replies there.

---

### Post by ronnielsen1 on 2010-06-15
> Wine is not the miracle cure many make it out to be; at best, it only  runs some MS Windows apps.
True but according to winehq it's supposed to work

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=7314](http://appdb.winehq.org/objectManager.php?sClass=application&iId=7314)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12969&iTestingId=39204](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12969&iTestingId=39204)

In winecfg go to drives tab > autoselect > apply. Then start the program in terminal like wine /home/locationofsoftware.exe (of course subbing the name of your program) and this might display errors

---

### Post by joedanj on 2010-06-15
> **ronnielsen1 said:**
> 
In winecfg go to drives tab > autoselect > apply. Then start the program in terminal like wine /home/locationofsoftware.exe (of course subbing the name of your program) and this might display errors

YES!!! THANKS!!! IT works now :DDDDDDDDDDDDDDDD *so happy* :))))))) ^^' 
THANK U!!!

---

### Post by tswsl1989 on 2011-12-07
I found that winetricks dlls ie7, winetricks dlls winhttp and winetricks dlls wininet got the downloader going for me, the above tips didn't help (Ubuntu 11.10)

Hope that's useful

---

### Post by atyankov on 2011-12-26
> **tswsl1989 said:**
> I found that winetricks dlls ie7, winetricks dlls winhttp and winetricks dlls wininet got the downloader going for me, the above tips didn't help (Ubuntu 11.10)

Hope that's useful

Thank you, this worked for me!

---

### Post by thungsten on 2012-01-01
To run the MSDNAA-Downloader for Linux or Mac OS X without an existing Windows installation you can use Wine (with Winebottler for Mac). I tried Crossover but it didn't work.
Using Wine with Winebottler was not completely easy but rather simple.

[LIST=1]
[*]I downloaded and installed Winebottler from [http://winebottler.kronenberg.org/](http://winebottler.kronenberg.org/) 
[*]Started Wine and Winebottler
[*]I installed the predefined prefix "Internet Explorer 8" (I did not enable "Silent" and disabled the proposed "Update installation" of the IE explorer during the installation process) - a little bit strange was that at first the IE7 was installed, but after that IE8 was installed
[*]Then I changed the prefix via the Wine-Symbol in menu bar to the new installed IE prefix and
[*]started the MSDNAA-Downloader-EXE by double-click and selecting to run directly within the IE prefix
[*]In the MS downloader I selected where I wanted to store the download (I didn't want to save it in the virtual Wine directory C:\Temp) within the virtual drive Z which actually is root (e.g. Z:/Users/Shared)
[*]and replaced all forward slashes "/" by "\" backward slashes (else you get a error message that the directory is not "valid"; don't add a trailing slash!), e.g. Z:\Users\Shared
[*]Finally I clicked to start the download
[*]After the download was complete the downloader extracted an ISO out of the SDC file
[*]That ISO can be burned on a CD/DVD
[/LIST]

That's it.

I tried the very same with crossover but it didn't work and I always got "Error_8" saying "A valid Directory must be specified" (with or without "/").
No Crossover needed, no crossover bottles, no selection of DLLs, no additional Active X-Installations and whatsoever. Not that complex but it took some time to find it - hope this helps others to skip the cumbersome trial & error&#8230;
For me that worked perfectly with Apple MacBook Pro under Mac OS X 10.7 Lion so I guess it will work with any PC and UNIX derivate/LINUX.

Using Wine is even better: no demo, trial software or registration needed!

Regards

JT

---

