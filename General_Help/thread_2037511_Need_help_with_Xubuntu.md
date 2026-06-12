---
title: "Need help with Xubuntu"
date: 2012-08-04
forum: General Help
---

### Post by adrianrn on 2012-08-04
Hy! I decided to give Xubuntu a try but there's stuff I can't figure out. 
1- I can't make the flashplayer work neither in chrome/chromium/mozilla
2- I don't know how to install my video drivers and other drivers I need(don't know if I need them)
3- I don't know how to optimize xubuntu and what other stuff I need instaled
I'm running an AMD Barton 2600+, 512 RAM, ATI 9600 Radeon, 20 Gb HDD
Thanks!

I just noticed that the flash works if I play a video but when i try to play another i get an error saying that the flash couldn't be loaded

---

### Post by Dylan1473 on 2012-08-04
1) Not sure what's up with flash.
2) I'm pretty sure Ubuntu comes with some basic open source video drivers by default. Do you plan on gaming or any other graphically intensive activities? Also, Xubuntu probably asked you whether you wanted to install some proprietary stuff, I believe including proprietary graphics drivers, when you first installed it - did you choose to do this? This is probably how you got Flash if you're using the proprietary Adobe Flash Player. If not that could be why you're having problems.
3) Xubuntu is a full featured desktop environment with all the basic stuff (window manager, file manager etc.) as well as some typical applications like a web browser and office suite and such. What do you mean by optimizing it - what do you plan to use your computer for?

---

### Post by adrianrn on 2012-08-04
I really need to make the flash work :(
The sound works but I don't remember if it ask me to install proprietary stuff. I'm useing my computer for chatting, surfing the internet, movies and music.. but if I can't make the flash work I think I'll have to give up useing linux. Thanks for the fast reply

---

### Post by ajgreeny on 2012-08-04
I am not sure about your flash problem either, but I assume you have the most recent available version 11.2.202.  On my machine with an ATI 9200SE graphic card, that version refuses to work in any way at all, and I have to downgrade to flash 11.1.102-63, which is available from [Flash 11.1.102.63]("http://ubuntuforums.org/showthread.php?t=1953796") .

Install that version according to the instructions given in the thread and it may work properly with all flash videos.

There will be no drivers needed for graphic card as that ATI 9600 will work only with the open source radeon driver that you already have.  The only other possible driver you might need is for wireless, but if that either works already, or you do not have wireless hardware on the machine, there will again be nothing to do.

Any other optimization is really dependent upon what you mean by that phrase.  There are hundreds of things you can do to change the look of Xubuntu with different docks, themes etc etc, and if you put icons on the desktop you can do things like getting rid of the rectangular box around the icon text with a simple **.gtkrc-2.0** file in your home folder.  Here's my version attached which you can save in you home, but change to the proper name once saved, not forgetting the **.** at the start.

You will see there are a lot of commented out lines in this file.  These are either information, or lines that I do not want used in the configuration, but I have left them in place so you can see how much it is possible to change the look of the desktop with a single relatively simple configuration file.

---

### Post by Dylan1473 on 2012-08-04
Well, flash-wise, you could check to see if you have the proprietary Adobe Flash installed. You could also try installing the proprietary graphics drivers if you haven't already but I'm pretty sure the open source ones should be able to handle Flash. You might be able to find Adobe Flash through the software center just by typing "flash" (no quotes) in the search box. If nothing shows up, please open a terminal and type

```
gksudo gedit /etc/sources.list
```then post the contents of that file here, you might not have the right repository enabled.

You may also be able to install the proprietary ati radeon drivers through the software center, it's called fglrx. Also, you might be able to install them by going to the System menu (in the top right) then Administration, then Additional Drivers (as per [this guide]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")) if it's still done that way. That's how I did it in 11.10, I assume it works in the same way for 12.04. Failing that it can be done through the terminal or using files off their website but this might be a bit more complicated.

Oh, also, before you install the fglrx drivers open a terminal and type

```
fglrx info
```and post the output, maybe you already have them installed and working properly.

EDIT: ajgreeny is probably right about the proprietary drivers not working with that card, I forgot that not all cards were supported.

I'd also concur about customizing Xubuntu. It was my favourite desktop environment for a long time for that very reason before I switched to Enlightenment, and there are still a couple features I miss. I still use it when Enlightenment crashes.

---

### Post by adrianrn on 2012-08-06
Dylan1473 I downgraded and still nothing. Also checked the software center and I have Adobe Flash installed.
About the additional drivers nothing shows up if I do the "System menu (in the top right) then Administration, then Additional Drivers" method.
"fglrx" command not found. Any other ideas? Thanks

ajgreeny how should I save the file you attached in your message and where exactly? Thanks

P.S I can't even use [www.bet365.com](www.bet365.com) so I can't use any sites with flash :(

---

### Post by Dylan1473 on 2012-08-06
Yeah, sorry, I should've clarified when I edited my post. I suspect ajgreeny is correct; the proprietary Radeon drivers might not be available for your card. I forgot that they did not support all of them.

If Adobe flash is there and you've attempted to downgrade as well, there are a couple of open-source flash alternatives you could try. Ordinarily they wouldn't be an improvement over the proprietary drivers (they're still in development) but if flash just flat out refuses to work you may as well give it a shot. The two big ones are known as Gnash and Lightspark. You can install either with

```
sudo apt-get install gnash
```or

```
sudo apt-get install lightspark
```You might need to uninstall Adobe Flash before using those or at least disable the browser plugin. You might also need to download the plugins for those players, but I'd think it'd be handled automatically. If not, just type

```
sudo apt-get install browser-plugin-gnash
```or
```
sudo apt-get install browser-plugin-lightspark
```Alternatively, I believe Google Chrome (I'm not sure if Chromium does this as well, note that there is a distinction so it might not work on Chromium) has its own flash plugin. So, using the Google Chrome browser might work as well.

EDIT: I think you maybe already said changing browsers didn't work. I'll leave that in there just in case. Also, dumb question, but you *do* have the flash plugin enabled in your browser right?

---

### Post by adrianrn on 2012-08-06
I've tried chrome first then mozilla and then chromium. Chrome comes with it's own flash but still not working. Flash is enabled of course.
I'm trying the 2 options you gave me and I'll let you know if it works. Thanks!

EDIT: It works!! I tried gnash and now it works. Thank you very much!
Any tips about customization? I'd like to learn to actually do stuff in linux..

---

