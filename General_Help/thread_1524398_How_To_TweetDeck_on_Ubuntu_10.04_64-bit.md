---
title: "How To: TweetDeck on Ubuntu 10.04 64-bit"
date: 2010-07-05
forum: General Help
---

### Post by dckirba on 2010-07-05
Installing TweetDeck is not that complicated, but if you have a 64-bit install of Lucid Lynx, you'll face a little hurdle in the form of Adobe Air.

You see, Adobe Air only has a 32-bit version and you can't just install the .deb file found on the website and wait for everything to work fine.

All the information to install Adobe Air and TweetDeck on a 64-bit machine is freely available on the net. I didn't find all the information in one place so that's the reason for this howto. It's my first howto, so I'm looking forward to your feedback so I can make it as perfect as possible.

Most of this information is taken from [OMG! Ubuntu's guide on installing Adobe Air for Ubuntu 64-bit]("http://www.omgubuntu.co.uk/2010/01/how-to-install-adobe-air-ubuntu-64bit.html"). In fact, there are just two steps that are different.

There are two things that need to be done:

[LIST=1]
[*]Install Adobe Air
[*]Install TweetDeck
[/LIST]

[SIZE="5"][COLOR="SeaGreen"]Installing Adobe Air[/COLOR][/SIZE]

So first, you'll need to install Adobe Air. Follow these steps in order and all should work well.

[LIST]
[*]Get Adobe Air from [here]("http://airdownload.adobe.com/air/lin/download/latest/AdobeAIRInstaller.bin")
[/LIST]

[INDENT]This will download the .bin version of the Adobe Air Installer. Make sure you don't get the .deb because that causes a few problems down the line (The package manager will tell you that TweetDeck has broken dependecies and you'll have to remove it). Just remember where you downloaded the file for now.[/INDENT]

[LIST]
[*]Download and install 'Getlibs' [from]("http://frozenfox.freehostia.com/cappy/getlibs-all.deb") here.
[/LIST]

[INDENT]Getlibs helps install 32-bit libraries in a 64-bit environment. Save the .deb file and double-click to install it.[/INDENT]

[LIST]
[*]Install the dependencies for Adobe Air.
[/LIST]

[INDENT]Just copy and paste the following into a terminal (Applications>Accessories>Terminal) and press enter
```
sudo apt-get install lib32asound2 lib32gcc1 lib32ncurses5 lib32stdc++6 lib32z1 libc6 libc6-i386 lib32nss-mdns
```[/INDENT]

[LIST]
[*]Once that step is finished, copy and paste each of the following commands into a terminal ***one at a time***.
[/LIST]

[INDENT]If you have a slow internet connection, it may seem like nothing is happening, but be patient and everything should install correctly.

```
sudo getlibs -l libnss3.so.1d
```
```
sudo getlibs -l libnssutil3.so.1d
```
```
sudo getlibs -l libsmime3.so.1d
```
```
sudo getlibs -l libssl3.so.1d
```
```
sudo getlibs -l libnspr4.so.0d
```
```
sudo getlibs -l libplc4.so.0d
```
```
sudo getlibs -l libplds4.so.0d
```
```
sudo getlibs -l libgnome-keyring.so
```
```
sudo getlibs -l libgnome-keyring.so.0
```
```
sudo getlibs -l libgnome-keyring.so.0.1.1
```[/INDENT]

[LIST]
[*]Remember the Adobe Air .bin file you downloaded in the first step? Move it to your home folder.
[/LIST]

[LIST]
[*]Open a terminal and type the following:
[/LIST]
	[INDENT]```
chmod +x AdobeAIRInstaller.bin
```[/INDENT]
[INDENT]Hit enter and then type (or paste) this into the terminal and press enter.[/INDENT]
	[INDENT]```
sudo ./AdobeAIRInstaller.bin
```[/INDENT]

[INDENT]Follow the on-screen instructions and you're almost done[/INDENT]

[LIST]
[*]Adobe Air should be installed in the /opt directory in your File System. You now need to copy a file from there and paste it into the /usr/lib32 directory. The easiest way (for me) to do this was:
[/LIST]

[INDENT][LIST=1]
[*]Open a terminal and type ```
sudo nautilus
```
[*]Navigate to **opt>Adobe Air>Versions>1.0>Resources** and look for the file named *[COLOR="DarkRed"]libadobecertstore.so[/COLOR]*
[*]Right-click and select copy from the context menu (or select the file and press Ctrl-C)
[*]Now navigate to **usr>lib32** and paste the file in this directory
[/LIST][/INDENT]

[LIST]
[*]Final step to install Adobe Air:
[/LIST]
[INDENT]In the Terminal type the following command and press enter[/INDENT]
[INDENT]```
sudo ldconfig
```[/INDENT]

That's it for the first step. You now have Adobe Air installed.

[SIZE="5"][COLOR="SeaGreen"]Installing TweetDeck[/COLOR][/SIZE]
[LIST]
[*]Go to [TweetDeck's desktop download page here]("http://www.tweetdeck.com/desktop/") and click on the **Install TweetDeck** button. Now just follow the on screen prompts and you should be done.
[/LIST]

**[COLOR="SeaGreen"]Note[/COLOR]**: When the TweetDeck download asks you to save or open the file, you could choose to save the file especially if you have a slow internet connection. That way if something isn't working right, you can save yourself some time by just double-clicking the .air file to install TweetDeck next time.

---

### Post by Brejcha on 2010-07-15
[INDENT]```
sudo ./AdobeAirInstaller.bin
```[/INDENT]

Just letting you know that the above code is wrong. 

It should be sudo ./AdobeAIRInstaller.bin 

Just need to have the AIR in CAPS!

---

### Post by dckirba on 2010-07-16
My bad! You're absolutely right. I've edited the information. Thanks for pointing it out.

Cheers,
David

---

### Post by sammyboy405 on 2010-07-30
Hands down the Best tutorial on Setting this up.  Ive read many tutorials and this is bar none the best yet.

Ive been though several others and Air apps just never seemed to work right. They where laggy and crashed alot.

and I can Honestly say, everything is stable thus far.



thanks alot for this tutorial.

---

### Post by edkirin on 2010-08-07
@dckirba

I followed your steps exactly for installing Adobe Air. Everything was done without any error reported. When I start the AdeobeAIRInstaller (sudo ./AdobeAIRInstaller.bin) installer opens a dialog with agreement. After clicking the "I agree button", the following error is reported:

[IMG]http://img717.imageshack.us/img717/5690/airs.png[/IMG]

Any clue? I'm running Kubuntu 10.04 64-bit. Everything else works on my computer without any problems.

Thanks for your help.

---

### Post by edkirin on 2010-08-07
Ok, I solved the problem by running installer using **kdesu** instead sudo.

---

### Post by dckirba on 2010-08-08
@edkirin: Glad it worked. I'll edit the instructions to reflect KDE as well. 

@sammyboy405: Glad you found it useful :)

Cheers,
David K

---

### Post by carosalamanca on 2010-08-09
I have already use the advice, and i could install tweetdeck at last.

Thank u, i'm not an system administrator,i'm a dummy at ubuntu and was so clear to follow the steps.

:)

---

### Post by lodder on 2010-08-13
Thx for the how to but had to run with 
```
gksudo ./AdobeAIRInstaller.bin
```

Otherwise everything went perfect.

---

### Post by ptviperz on 2010-08-16
Anyone else having problems with Flash crashing after installing Air/Tweetdeck? :(

---

### Post by dscoggins on 2010-08-23
@dckirba

One of the best how-tos I have seen. Thanx! 

One thing I had to do before the install from Tweetdeck.com would work was to manually start the Adobe Air application. It did not start on it own from the install. Once Air was running, the install completed flawlessly!

---

### Post by cemilhilton on 2010-09-14
Actually I think I found the easiest way:

Go to:
[http://timesreader.nytimes.com/webapp/AppLogin.do](http://timesreader.nytimes.com/webapp/AppLogin.do)

Click on Launch Times Reader, it says it has to first install Adobe Air. Then you can go to Tweetdeck and install it. Worked for me in 10.04 and 10.10 beta.

---

### Post by ichramm on 2010-09-23
Done step by step, it works like a charm now.

Thanks!

---

### Post by dr_jb on 2010-09-24
I followed your instructions and that probably got me most of the way there.  But I was not able to install tweetdeck from the webpage.  It says "Installing" but nothing ever happens.  I was able to install it following the instructions [here]("http://www.gregkurts.com/2010/01/02/tweetdeck-on-ubuntu-64-bit/")

Specifically the following two lines worked:
# Download TweetDeck [here]("http://tweetdeck.com/go/download/tweetdeck")
# /opt/Adobe\ AIR/Versions/1.0/airappinstaller ~/Downloads/TweetDeck_0_33.4.air

---

### Post by harutake on 2010-10-31
it works like magic! :P

thanks..

---

### Post by gearond on 2010-12-03
THIS is the best, most accurate, non repository installation I've ever read, followed, and obviously, had instant success with.

You . . . are . . . the . . . man.

---

### Post by gearond on 2010-12-03
Do all the installation before the download part, Then,if you reload the adobe page in your browser, the button then works. 

> **dr_jb said:**
> I followed your instructions and that probably got me most of the way there.  But I was not able to install tweetdeck from the webpage.  It says "Installing" but nothing ever happens.  I was able to install it following the instructions [here]("http://www.gregkurts.com/2010/01/02/tweetdeck-on-ubuntu-64-bit/")

Specifically the following two lines worked:
# Download TweetDeck [here]("http://tweetdeck.com/go/download/tweetdeck")
# /opt/Adobe\ AIR/Versions/1.0/airappinstaller ~/Downloads/TweetDeck_0_33.4.air

---

### Post by altheablue on 2010-12-10
Thank you! This has been plaguing (sp?) me for weeks - I was actually struggling with Grooveshark, not Tweetdeck, but same issue. Thanks! :cheers:

---

### Post by 0l1 on 2010-12-12
Hey dckirba! Thank you very much for this useful guide. I searched a long time and it seems, as if it is the best and the last possibility for 64bit Ubuntu Maverick users sitting behind a proxy to use twitter since gwibber does not work properly.

Happy
0l1 :)

---

### Post by reuvenim on 2011-01-09
> **cemilhilton said:**
> Actually I think I found the easiest way:

Go to:
[http://timesreader.nytimes.com/webapp/AppLogin.do](http://timesreader.nytimes.com/webapp/AppLogin.do)

Click on Launch Times Reader, it says it has to first install Adobe Air. Then you can go to Tweetdeck and install it. Worked for me in 10.04 and 10.10 beta.

I have to say the above advice worked for me like a charm (64 bit Maverick). Simple and fast!

---

### Post by WarrenSH on 2011-01-09
[B][SIZE="4"]32 BIT is so easy to install ;) 

[/SIZE][/B]

Open the Terminal
Download the file from here using the wget command:
[http://airdownload.adobe.com/air/lin/download/1.5/AdobeAIRInstaller.bin](http://airdownload.adobe.com/air/lin/download/1.5/AdobeAIRInstaller.bin)
The name of the file is AdobeAIRInstaller.bin
Save the file in the Home folder (Places > Home Folder)
Run this command:
chmod +x AdobeAIRInstaller.bin
Now run this command:
sudo ./AdobeAIRInstaller.bin
The normal installer will open, install it. From now whenever you download a .air file, just double click it and it will be installed.

---

