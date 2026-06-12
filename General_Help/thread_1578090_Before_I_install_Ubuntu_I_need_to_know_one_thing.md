---
title: "Before I install Ubuntu I need to know one thing:"
date: 2010-09-19
forum: General Help
---

### Post by ryefield on 2010-09-19
I am supposed to kiss all my apps and programs goodbye? will any of the programs I use with my XP work on Ubuntu? where and how would I get programs like BSplayer, YourUninstaller, Painshop Pro, Daemontools, Winrar, Ccleaner etc.. that work on Linux? 
and even if I do get them, say I'm running a dual boot system with ubuntu and XP side by side, wouldn't that force me to have every programe installed twice (one for XP one for Linux)? thats a huge waste of HD innit? 

I just tried out Ubuntu and it is awesome, but if I can kiss away all the programs I know while using it, what is it good for? just for using Firefox?

---

### Post by inameiname on 2010-09-19
Not all Windows apps will work with Ubuntu, and Linux in general. Guess it depends on what you want, and if you can live with equivalents. Of course, there are also many Windows apps that do have Linux versions out there, but I don't think those that you mention do.

Basically, if you are set in your ways as to use those specific apps, and won't like alternatives, stick with Windows. Maybe the maintainers will someday make Linux versions, but that's a long shot. But if you are open to trying equivalents, which in my opinion do just what the others do, and often more, then try out Ubuntu. Seems though most folks who complain about this tend to favor those apps they are used to over everything else.

Oh, and sadly, yes, you will have to both the Windows installations and the Linux installations on your hard drive if you are dual booting. It'd be that way too if you had say Windows XP and Windows 7 on two different partitions too. They don't work together, or as one, but work like you have two computers and two separate operating systems. The only real sharing between the two is being able to view the partition's contents and copy/paste or read or whatever.

To get equivalents, there is a much easier way than just searching the net. You can check out the Ubuntu Software Center, which has a listing of many all in one place, for easy installation. It's something that Windows lacks. Here are some that I know that I like: Bleachbit is an equivalent to CCleaner, VLC or SMPlayer works as an equivalent to BSplayer. I'm not sure of an exact equivalent to YourUninstaller, but I know there are a few for Linux. Personally, since the terminal is great for installing and removing packages, the 'purge' command works great for removing it all. Actually, you can do this with Ubuntu-Tweak as well. An equivalent to Winrar is installed as default, which you can 'sudo apt-get install rar unrar zip unzip' in the terminal to get it to work with zip and rar files. 

Finally, one option you can also use for many Windows apps is that a lot will work under Wine, in Linux. That means, thats you can actually natively run those very Windows apps that you can't do without, natively in Ubuntu. But, the catch is not all Windows apps will work, AND often, not as well as a Linux equivalent would in Ubuntu.

---

### Post by Ahava591 on 2010-09-19
> **ryefield said:**
> I am supposed to kiss all my apps and programs goodbye? will any of the programs I use with my XP work on Ubuntu? where and how would I get programs like BSplayer, YourUninstaller, Painshop Pro, Daemontools, Winrar, Ccleaner etc.. that work on Linux? 
and even if I do get them, say I'm running a dual boot system with ubuntu and XP side by side, wouldn't that force me to have every programe installed twice (one for XP one for Linux)? thats a huge waste of HD innit? 

I just tried out Ubuntu and it is awesome, but if I can kiss away all the programs I know while using it, what is it good for? just for using Firefox?

  Wonders never cease.  You apparently have tried Ubuntu, I would guess as a live disk, and yet you didn't look to find where you could easily, quickly download software without using the command-line?  To get your software, use the Ubuntu Software Center or Synaptic if you want a little more information about what you're doing. The command-line is an option as well, if you will only take the time to learn it.  You're not likely to find those exact programs you use in Windoze; instead you will find (usually,) free and open-source software which receives more frequent and thorough updates from a larger, generally more knowledgeable and kind community than said counterparts. -What can be said about the Ubuntu Software Center is that it is, I believe, largely composed of software which is deliberately designed to look, if not function under the hood, like software from companies like Apple and Microsoft.   The learning curve is very rarely steep, if it exists at all.  If you are dual-booting and using software analogues for a given task within each operating system such that you have a one-to-one correspondence between the number of programs per task for each OS, then why are you dual-booting? Windows seems to be the waste of storage space. In other words, if you find what you need within Ubuntu, why are you going to keep XP at all?  You will demonstrate a wizardly skill in computing if you fail to find software for Linux which can do the same things as Windows-only software.   The one exception I can immediately think of is the GIMP, ('stands for &quot;GNU Image Manipulation Program,&quot;) which, I have been told, is inferior to something like Adobe Photoshop. I don't work with graphics and so I cannot tell you this is the absolute truth. However, it is repeated often enough among knowledgeable people that I am inclined to believe it isn't that great.      Now, I hope you actually do more research now. I recommend you run your live disk again and spend at least two hours with Ubuntu trying out programs. Read books. Read online. -If you still can't fathom Ubuntu being used for more than Firefox, I'm afraid you're a lost cause.   Good luck, I sincerely hope I see you around here more often, (perhaps as a permanent Linux user,) and please ask any questions you may have after being unable to find the answer for yourself.

---

### Post by srs5694 on 2010-09-19
For the most part, Linux uses different programs than Windows. I'm only passingly familiar with most of the programs you mentioned, so I can't really say much about them; however, judging by their names and quick Google searches, it seems that YourUninstaller and perhaps CCleaner are superfluous in Linux. Most Linux distributions, including Ubuntu, include package management tools that blow away anything in Windows, so unless you explicitly bypass those package managers, there's no need for third-party tools to manage program installation or uninstallation.

Yes, installing Linux in a dual-boot configuration means you'll be expending disk space on two or more programs that perform similar tasks in your two OSes. That's the price of running two or more OSes on one computer. With modern hard disks, the price isn't that high; Ubuntu installs in about 2-15 GB of disk space, depending on how much stuff you install, whereas modern disks are well in excess of 100 GB. If devoting 20-50 GB to Linux (including space for user files) is a challenge, IMHO it's time to upgrade your hard disk -- whether or not you want to try Linux!

It *is* possible to run at least some Windows applications in Linux by using [Wine](http://www.winehq.org/) (which is included with Ubuntu). It doesn't work with 100% of programs, and it would be useless for some of the system utilities you mention, but it's useful for productivity programs (word processors, spreadsheets, etc.) and games. It's sometimes possible to run Windows programs from both Windows and Linux from the same location, thus saving a few kilobytes or megabytes of disk space; however, most of the bigger Windows applications insist on installing stuff in various locations, adding Registry entries, etc. This makes it much easier to install even these programs twice, since Wine maintains its own independent Registry and directory tree for Windows programs. I'll add this about Wine: If you need to run very many programs in Wine, IMHO it's probably better to stick with Windows. What's the point of booting Linux (or any other OS), only to run non-native programs? If you want some Unix-like tools, you might be better off using [Cygwin](http://www.cygwin.com) in Windows; this adds the most common Unix command-line tools to Windows, turning it into a moderately Unix-like environment with far better Windows compatibility than you can hope to get in Linux, since it remains Windows.

---

### Post by bodhi.zazen on 2010-09-19
In general you migrate to Linux apps.

The biggest problems are games, accounting software, and voice recognition. There are Linux apps in all these categories, these are the biggest areas of problem IMO. Photoshop to gimp can be difficult. WYSIWYG HTML editors also can be problematic.

What app do you need ?

See also:

[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

Many people have had the same sentiment, some stay with Windows for any variety of reasons. Personally, I thought the same thing, but I have not used Windows (outside of work, which is enslaved to the core) for many years and do not miss any Windows application, with the exception of Voice Recognition (Linux is very much behind the curve here, but improving).

---

### Post by techunit on 2010-09-20
I have to agree that every application has a counterpart for Linux, and in my experience most of those apps are unnecessary in Ubuntu anyway. Uninstaller, Cleaner, winrar, are all basic functions of ubuntu. PaintShop Pro is easily replaced with GIMP. If gimp isn't you cup o tea then look at wine, which will let you run Windows Apps in Ubuntu/Linux. The major problem with WINE for you is that ccleaner isn't going to do anything because the problems it solves are nonexistent in linux. I hope this makes sense to you. I hope this simplifies it is for you.

---

### Post by ryefield on 2010-09-20
u see, for the time being I'm surfing the web using Sierra Wireless 3G Netstick (compass-888). that means I'm using an external device which in turn uses its own XP based (i suppose) dirver. I've looked in their site, they don't have any Linux file for download, only Windows and OS-X (Mac). So I'm *ucked right? I'd love to at least use Ubuntu for internet, office and media (which covers 95% of my computer needs) but hey - if I can't have internet it pretty much useless innit? 

any thoughts? ideas? 

P.S
I will have normal cable connection in about a week. With XP, I went to horrid graft and trouble finding and installing all those bloody drivers and honestly, since I'm using this NetStick thingy, I still don't know if I got it all right. Would I be forced throught the same proccess with finding the correct and updated Unbutu drivers for every piece of my laptop hardware? 
I'm asking coz I bearly saw any discussion regarding drivers.. which is weird

---

### Post by srs5694 on 2010-09-20
First, be aware that the Windows drivers you get for many hardware devices are just recycled or slightly tweaked versions of more generic drivers. For instance, to pick some fictitious company names, CardMaker, BoardSeller, and StickBuilder may all manufacture products based on chips that are designed and manufactured by ChipCooker. ChipCooker makes Windows drivers available for its chips, and CardMaker, BoardSeller, and StickBuilder will package these drivers with their products and/or put them on their Web sites; but these end-user product manufacturers are likely to substitute their own names for the ChipCooker name in the drivers in order to make it look as if they did the work. They didn't. You might even be able to get a generic ChipCooker driver to work with all three products. Sooner or later, the drivers will work their way into Windows itself, so that the devices will be supported out-of-the-box with future versions of Windows. That could take years, though.

When you move to the Linux world, you'll find that ChipCooker might or might not bother writing Linux drivers. Either way, though, a driver is likely to exist, and that driver is likely to be included in the Linux kernel, which of course comes with all the Linux distributions. Thus, whether or not ChipCooker actually writes a Linux driver, there's no need for them to distribute it. Instead, you select the ChipCooker driver (whether you're using a CardMaker, BoardSeller, or StickBuilder product) and that's it. In fact, more often than not, the Linux distribution automatically detects that you need the ChipCooker driver, so you don't need to do anything explicit to get it working. Because Linux distributions tend to get updated pretty frequently (every 6 months for Ubuntu, counting both types of releases), hardware tends to get supported in the installers very quickly, compared to the Windows world.

That said, I don't know anything about your Sierra Netstick product specifically, although a quick Google did turn up [this page](http://sierrawireless.custhelp.com/app/answers/detail/a_id/500/session/L3NpZC9ld1MyUHNhaw%3D%3D) that suggests Linux drivers are available for it. On a more negative note, Linux support for WiFi devices in general is poorer than for many types of hardware. Also, brand-new hardware generally sometimes lacks good Linux support; unless a manufacturer explicitly supports Linux (as some do), it can take a while for hardware to get into the hands of interested Linux developers and for them to write drivers.

Ultimately, the best way to find out how well your laptop is supported in Ubuntu is to try it. You can learn a lot from a Live CD boot without even installing the OS, but for some devices you may need to do a full install and fiddle with drivers.

---

### Post by Ahava591 on 2010-09-20
Office and media, have been covered. OpenOffice.org and the various text editors, (probably office suites other than OO.org but that is the most popular,) will have you covered with office/school/work applications. You will be able to view/edit anything a Windows user sends you; you will be able to save anything you view/edit in a format that a Windows user can then use when you send it to them.

Music and video are pretty well supported; at the very worst, the program you are using for media will tell you when a particular file format is not supported, etc. You will then be told what packages you need to make it work; usually it is up to you to find out where to get those packages, (remember Synaptic? Synaptic is your friend...)


Let us suppose you are using an Nvidia 9800GT video card because at one point in your life you used Windows and played video games and needed a discrete GPU for that. Now, you are probably going to have an integrated graphics "card," as well that you won't even notice, maybe won't even know about it. Ubuntu will tell you when you need a driver to use that 9800GT, and with graphics cards at least, will actually download and install that driver for you. You'll see a window pop up, put in your password maybe once or twice, it will download and install automatically and then you will restart the computer. Voila, it's done. Now you can use the fancy graphics.
-If you choose not to do this, then Ubuntu is going to play nicely with your integrated chip and you won't even notice.


Now, if you would find all of this out with the live disk....you mentioned that you tried Ubuntu? Did you actually try to do the things you do with Windows, or did you just see if you liked the looks?

If you can access the Internet and use your network while running the live disk, with all of the hardware, (such as the USB NIC you mentioned,) that you have now and will have when you install Ubuntu, I cannot think of anything that would cause you to not be able to connect after installation.

---

### Post by mastablasta on 2010-09-20
> **bodhi.zazen said:**
> WYSIWYG HTML editors also can be problematic.
 

 
Actually compozer is quite good here, but for some reason the last version does not have the coloured code in the editor, so it is more difficult to read it and find th eones you need to fix or change.
 
From the programmes OP wrote i think he will have a problem wiht photoshop. but it all depends what he uses it for. I suggest installing GIMP on windows and see if it can replace photoshop for what he needs it. i mean photoshop is powerfull but maybe not every one needs so much power. GIMP is very good too, but not a substitution.

---

### Post by k33bz on 2010-09-20
for every windows program out there, there is usually at least 10 linux versions. I have been running linux for years, and the only thing I miss is the gaming. Games are much better in Windows I am sorry to say. But all the other programs, dont miss at all.

My wife has been running Linux for almost a year now, the only thing I have heard her complain about is the ability to use Instant Messengers with Audio and Video support, especially for yahoo.

---

### Post by ryefield on 2010-09-20
> **Ahava591 said:**
> 
Now, if you would find all of this out with the live disk....you mentioned that you tried Ubuntu? Did you actually try to do the things you do with Windows, or did you just see if you liked the looks?

If you can access the Internet and use your network while running the live disk, with all of the hardware, (such as the USB NIC you mentioned,) that you have now and will have when you install Ubuntu, I cannot think of anything that would cause you to not be able to connect after installation.

To be honest mate, my "experience" with Unbutu lasted around 6 minutes at best. I ran it from in ISO burnt on a DVD, and chose the "try without installation or any changes" option (as I was too scared to mess up my XP partition, which is currently the only patition I have on this computer).

So I knocked about few different screens like the background choser and few of the manues, and I LOVED it. Really, it is indeed brilliant. BUT, the I looked for the familiar XP "tray" and thought I found it on the upper right corner, but all that was there was the language bar, and few icons that told me that no network cable is connected and there's no wireless area available. bummer. 

well I figured out that with no connection to the ouside world, and with no programs to run, there's very little for me to see other than nicely designed desktop, and I booted back into XP. 

If the Netstick is supposed to be supported by default like you say, how do I operate it? that's the thing - I couldn't figure out how to start working with this pretty system!

Any tips?

Cheers

Johnny

---

### Post by k33bz on 2010-09-20
> **ryefield said:**
> To be honest mate, my "experience" with Unbutu lasted around 6 minutes at best. I ran it from in ISO burnt on a DVD, and chose the "try without installation or any changes" option (as I was too scared to mess up my XP partition, which is currently the only patition I have on this computer).

So I knocked about few different screens like the background choser and few of the manues, and I LOVED it. Really, it is indeed brilliant. BUT, the I looked for the familiar XP "tray" and thought I found it on the upper right corner, but all that was there was the language bar, and few icons that told me that no network cable is connected and there's no wireless area available. bummer. 

well I figured out that with no connection to the ouside world, and with no programs to run, there's very little for me to see other than nicely designed desktop, and I booted back into XP. 

If the Netstick is supposed to be supported by default like you say, how do I operate it? that's the thing - I couldn't figure out how to start working with this pretty system!

Any tips?

Cheers

Johnny

Tips start with information. Can you post the specs of your computer. Laptop, netbook, desktop? Also if you can tell us what wireless card you have?

---

### Post by Joacom on 2010-09-20
The applications you are requesting has a "clone" version on ubuntu, They have difrent names, and difrent devlopers but does the same as the Requested applications, you can also use Wine to emulate a windows enviroment to get Windows applications running in linux :) 

You can also make a multiboot so you can choose when starting the machine to Either start windows or ubuntu

Hope this answer was alittle help.

---

### Post by hawthornso23 on 2010-09-20
The best way to do it in my opinion is to get (build) a new box and just put ubuntu on it. That forces you to learn the ubuntu way to do things instead of always trying to do things the windows way and getting frustrated because ubuntu is different. You'll find that pretty much anything windows can do ubuntu can do better. Once you get used to it you'll never want to go back.

---

### Post by mastablasta on 2010-09-20
> **ryefield said:**
> 
If the Netstick is supposed to be supported by default like you say, how do I operate it? that's the thing - I couldn't figure out how to start working with this pretty system!
 

 
soem are wireless cards are supported out of the box, some need drivers to install (which is likely done by pluggin in the cable connection and then follow instructions from the System->Administration->Hardware drivers menu). 
 
then there is the third and nastiest version (but not so often these days) where you install XP drivers using a special wrapper.

---

### Post by robsoles on 2010-09-20
I couldn't find mention of virtualbox on either of the two pages of this thread so I thought I would mention it.

You don't need to spoil a good thing by dual booting (unless you have a real mean pig of a windows program) because the absolute majority of Windows programs will run quite happily in a [www.virtualbox.org](www.virtualbox.org) virtual machine of XP right under Ubuntu no probs.

Wine runs a fabulous of windows programs very well but certain programs won't and so I have a virtualbox running XP myself.

---

### Post by nothingspecial on 2010-09-20
You are going to have a frustrating time if you try and make ubuntu work like windows.

It doesn`t.

That`s the biggest step in the learning curve.

Sure, you can surf the net, watch videos, use an iPod etc, but the way that it is done is different.

To paraphrase a good analogy I read once somewhere....

It`s like driving a car and riding a motorbike. They both get you from A to B, but they do it differently. If you try putting a steering wheel on a bike, you're going to have a hard time riding it. Better to learn how to use the handlebars....

If you see what I mean.

---

### Post by k33bz on 2010-09-20
> **nothingspecial said:**
> You are going to have a frustrating time if you try and make ubuntu work like windows.

It doesn`t.

That`s the biggest step in the learning curve.

Sure, you can surf the net, watch videos, use an iPod etc, but the way that it is done is different.

To paraphrase a good analogy I read once somewhere....

It`s like driving a car and riding a motorbike. They both get you from A to B, but they do it differently. If you try putting a steering wheel on a bike, you're going to have a hard time riding it. Better to learn how to use the handlebars....

If you see what I mean.

I agree, please check the link in my signature

---

### Post by bodhi.zazen on 2010-09-20
> **mastablasta said:**
> Actually compozer is quite good here, but for some reason the last version does not have the coloured code in the editor, so it is more difficult to read it and find th eones you need to fix or change.
 
From the programmes OP wrote i think he will have a problem wiht photoshop. but it all depends what he uses it for. I suggest installing GIMP on windows and see if it can replace photoshop for what he needs it. i mean photoshop is powerfull but maybe not every one needs so much power. GIMP is very good too, but not a substitution.

Personally, I use bluefish , and check the code in firefox and chromium.

I personally like the look of kompozer , but if you look under the surface, the code is sloppy. (I assume you are talking about kompozer - [http://kompozer.net/](http://kompozer.net/))

---

### Post by pricetech on 2010-09-20
> **nothingspecial said:**
> To paraphrase a good analogy I read once somewhere....

It`s like driving a car and riding a motorbike. They both get you from A to B, but they do it differently. If you try putting a steering wheel on a bike, you're going to have a hard time riding it. Better to learn how to use the handlebars....

If you see what I mean.

I had a different analogy, but not necessarily a better one.

I think this is a clear cut case of using what works for you and being happy.

---

### Post by migs73 on 2010-09-20
+1 on the Virtual Box. I run Ubuntu with Vista (yeugh!! I only use it 'cos it came with my laptop)) in a VB for the three windows apps. I can't get to work/equivalents for in Ubuntu.

---

### Post by perspectoff on 2010-09-20
I personally like Ubuntu Guide and Kubuntu Guide, which have a good cross-section of equivalent programs.

Linux IM has integrated video and chat, these days.

All programs in all operating systems are a matter of trying out things and seeing if you like it.

The difference is that if you pay to explore (as you often must do in the Windows ecosystem), you go broke pretty quickly or learn to live without.

 [http://ubuntuguide.org](http://ubuntuguide.org)

 [http://kubuntuguide.org](http://kubuntuguide.org)

---

