---
title: "Linux - what the hell?"
date: 2009-08-20
forum: General Help
---

### Post by mbuehl on 2009-08-20
I've been a computer guy for as long as I can remember. I've worked at a helpdesk supporting relatively complex windows issues for the better part of 5 years, and am going to begin soon the last 2 years of my college education in Software Engineering.

Now, Linux, I've heard about this crazy thing - and I've installed Ubuntu on my machine to start getting familiar with kernels, bashing things, ssh, etc etc, but I find myself at a sincere point of confusion because, as most people probably find, Linux confuses the everliving crap out of me. I went through a number of pages and forums/subforums on here looking for like a comprehensive walkthrough on how to learn, use, and possibly love my new linux install, but have come up empty handed. 

So, can anyone point me to the Linux for Dummies section? Is there one on this site? Off-site?

Thanks ahead of time.

---

### Post by lisati on 2009-08-20
For a general look, try here: [http://en.wikipedia.org/wiki/Linux](http://en.wikipedia.org/wiki/Linux)

For Ubuntu-specific stuff, try here: [https://help.ubuntu.com/9.04/newtoubuntu/C/index.html](https://help.ubuntu.com/9.04/newtoubuntu/C/index.html)

---

### Post by Nburnes on 2009-08-20
There is a very good sticker with an ubuntu beginner book thats free in pdf format.

---

### Post by mbuehl on 2009-08-20
Thanks for the links, I'll likely be on here asking a load of seemingly stupid questions until this all starts to make sense. 

And with that being said, I'm trying to set up my other monitor as an extension of my main one. This worked easily and wonderfully in Windows, but for whatever reason it's not wanting to work at all with Linux. It ... sorta? worked before I activated the (im gonna call it a driver) for my accelerated graphics card. By sorta worked, I mean I couldn't move windows on to the second screen via dragging, they seemed to "catch" on an invisible wall! 

So I activated this thing, it asked me to reboot, and now when I go to the display options I am prompted saying that the built-in peice of software to control the graphics settings probably isn't gonna work all that great with the new one (by the way, it's an nVidia card, 9600 or somesuch), and that I should use the software provided by nVidia. Well, I load that up, and it wants me to save a file after changing it to enable both monitors, but when I attempt to save said file, I receive an error - Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

I was lead, by the program. to believe I have to save the settings and then restart the X server.

Help?

---

### Post by wojox on 2009-08-20
Open the terminal:
```
gksudo nvidia-settings
```

That will open it as root so you can save it.

---

### Post by Megrimn on 2009-08-20
here is one: [http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)

the other thing I would suggest is to try using your linux install for everyday tasks, such as email, music, internet, printing, typing, etc. 

Also, there are many programming apps in the repositories.  'Add/Remove...' under the 'Applications' menu on the desktop displays the applications and software available.  There is other software you can add that aren't available in the repos.  One example was the driver for my printer.  I had to go to the cannon website for that.  

Even though it is redundant, and not always on the forums, I usually use google to find the answers to any problems I have, as do many people on the Ubuntu forums.  Many times it will actually pull a thread from these forums on the first go that would have taken hours to find here otherwise.  

And remember always, that the only stupid question was the one that was never asked.

---

### Post by mbuehl on 2009-08-20
> **wojox said:**
> Open the terminal:
```
gksudo nvidia-settings
```That will open it as root so you can save it.

Excellent- I understand the use of this line. What's the significance of the 'gk' preceeding the sudo?

And also, how do I restart this X server?

---

### Post by wojox on 2009-08-20
Just reboot after. gk opens a gui from the terminal.

---

### Post by Gen2ly on 2009-08-20
> **mbuehl said:**
> ...What's the significance of the 'gk' preceeding the sudo?

And also, how do I restart this X server?

gk it short for gtk, gtk is short for gimp toolkit, which is the underlying toolkit for Gnome (Ubuntu's Desktop).  Phew... probably more than you wanted to know, eh?  Basically it's a graphical front-end to sudo.  You can restart X by restarting the Gnome login manager (gdm).  For Ubuntu I'm pretty sure its:

```
sudo /etc/init.d/gdm restart
```

---

### Post by kpkeerthi on 2009-08-20
> **mbuehl said:**
> I've been a computer guy for as long as I can remember. I've worked at a helpdesk supporting relatively complex windows issues for the better part of 5 years, and am going to begin soon the last 2 years of my college education in Software Engineering.

Now, Linux, I've heard about this crazy thing - and I've installed Ubuntu on my machine to start getting familiar with kernels, bashing things, ssh, etc etc, but I find myself at a sincere point of confusion because, as most people probably find, Linux confuses the everliving crap out of me. I went through a number of pages and forums/subforums on here looking for like a comprehensive walkthrough on how to learn, use, and possibly love my new linux install, but have come up empty handed. 

So, can anyone point me to the Linux for Dummies section? Is there one on this site? Off-site?

Thanks ahead of time.
Read this: [http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

---

### Post by scouser73 on 2009-08-20
Take a look at the - [[COLOR="Red"]**Free Ubuntu e-books**[/COLOR]]("http://www.ubuntugeek.com/free-ubuntu-linux-e-books.html")

---

### Post by mbuehl on 2009-08-20
> **Gen2ly said:**
> gk it short for gtk, gtk is short for gimp toolkit, which is the underlying toolkit for Gnome (Ubuntu's Desktop).  Phew... probably more than you wanted to know, eh?  Basically it's a graphical front-end to sudo.  You can restart X by restarting the Gnome login manager (gdm).  For Ubuntu I'm pretty sure its:

```
sudo /etc/init.d/gdm restart
```

not at all, thanks a lot!

---

### Post by tgeer43 on 2009-08-20
In fact, just logging out then back in will restart X.

And hang in there - once you get used to it, Ubuntu/Linux is the best thing since sliced bread. And learning it is more than half the fun. With your background you don't sound like someone who would be intimidated by a little ole operating system. :wink:

One of the primary reasons that I switched to Linux (besides Windows being an overpriced total piece of crapware) is that after 20 years I had become totally bored with my computer. Linux has breathed new life into it (and me) and I don't see myself getting bored any time soon. There's always something new to learn!

tgeer

---

### Post by mbuehl on 2009-08-20
> **tgeer43 said:**
> In fact, just logging out then back in will restart X.

And hang in there - once you get used to it, Ubuntu/Linux is the best thing since sliced bread. And learning it is more than half the fun. With your background you don't sound like someone who would be intimidated by a little ole operating system. :wink:

One of the primary reasons that I switched to Linux (besides Windows being an overpriced total piece of crapware) is that after 20 years I had become totally bored with my computer. Linux has breathed new life into it (and me) and I don't see myself getting bored any time soon. There's always something new to learn!

tgeer

It's definitely interesting so far, I've gotten it mostly up and going, this graphics thing was bugging me though, I've had 2 screens for so long it was really, really strange not having it around. Took me a while to get it configured correctly, but it's going well, now!

My ultimate goal, and it may be a long shot, is to try and get my civilization 4 game going on here. Then I wont need windows anymore. 

Is there something like the "Device Manager" with windows? Or am I to assume that all of my hardware is working without any additional configuration/drivers?

Thanks all for your help thusfar!

---

### Post by MaxIBoy on 2009-08-20
You can install "gnome-device-manager" using this command:
```
sudo apt-get install gnome-device-manager
```"apt-get install" will retrieve the package off the Internet and install it for you. 

gnome-device-manager doesn't actually let you change anything, but it does *list* all your hardware, which makes it very useful. 


-----------------




The main thing to keep in mind is that it makes sense, it's not just a bunch of arbitrarily-named garbage thrown together in the middle of an epileptic fit (though it may seem so at first.) There is method to it. You just need to be inquisitive, you'll figure it out. 

This is an excellent tutorial to the Command Line Interface (CLI.)
[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

Most tasks can be accomplished graphically, but most of the time people give you help on the Internet, it will be by asking you to copy/paste console commands. It's easier than saying "click here, then scroll down and click there, etc. etc. etc." It helps if you know how the issue is actually being fixed. So if you want to learn more about the system by learning from the people who give you help, you should learn the CLI. It's actually quite easy, and far more efficient than a great many tasks. And if you someday break your graphics somehow, you can recover without reinstalling, which is a nice plus. Heck, in a pinch, you can even finish that homework assignment (or whatever it is you usually write) without needing to fix your graphics!

---

### Post by sloggerkhan on 2009-08-20
In the repos is some sort of system profiler, but I don't think it's all that useful.
If you want, likewise there are all sorts of temperature/cpu/hd/network/etc monitors available if you want to configure them.

Generally, though, if anything major didn't work you'd notice.

One gotcha to make sure of, though:
lots of times it may seem like audio features don't work, when it's really just that defaults leave a lot of switches off. If you, for example, are finding audio in doesn't work, right click on your volume control, open volume control, click on preferences, check every box, then configure the settings for all of the newly available options. Very likely it will then work.

Likewise, get the latest nvidia driver with the latest m and sm player for a better HD playback experience. [https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer) and [https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer).

---

### Post by mcduck on 2009-08-20
> **mbuehl said:**
> Excellent- I understand the use of this line. What's the significance of the 'gk' preceeding the sudo?

And also, how do I restart this X server?

"sudo" is a terminal program for running programs as another user (unless you specify a user, it assumes you try to run the command as root).

"gksudo" is is similar program, made to handle graphical applications correctly.

While you can launch graphical applications with sudo as well, you shouldn't , since it doesn't load root's settings for graphical applications correctly. So it's using your normla user account's settings and configuration files, but with root's permissions. In some cases this can result to your configuration files ownerships changing to root. And that will cause problems.. :)

So use "sudo" for command-line programs, and "gksudo" for graphical programs. 

(in addition, to open a root session in terminal, you should use "sudo -i", and if you use KDE instead of Gnome as your desktop, then "kdesu" instead of "gksudo")


***

Anyway, welcome to Linux. :) Things will probably be quite confusing for a while, but just try to forget how things were done in Windows, and don't worry too much about anything. All the pieces will start to come together in their own time, remember how long it took you to get all the Windows knowledge you now have...

---

### Post by Wim Sturkenboom on 2009-08-20
For more generic Linux documentation, see [The Linux Documentation Project](http://www.tldp.org/)

> **tgeer43 said:**
> One of the primary reasons that I switched to Linux (besides Windows being an overpriced total piece of crapware) is that **after 20 years I had become totally bored with my computer**. Linux has breathed new life into it (and me) and I don't see myself getting bored any time soon. There's always something new to learn!That was the same for me.

The other reason for switching was that it also gives me peace of mind knowing that our main PC is not (yet) that much at risk when my girlfriend accidently opens some attachment with a virus. I must admit that she's quite carefull and usually waits till I'm home if she does not trust it. And she feels good when she realizes that she did beat the *******.

---

### Post by Bonster on 2009-08-20
Pocket Guide [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by tgeer43 on 2009-08-20
> My ultimate goal, and it may be a long shot, is to try and get my civilization 4 game going on here. Then I wont need windows anymore.A worth goal indeed (not running Windows anymore). Running Civilization IV in Wine under Linux is very doable. Have a look here:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2514](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2514)

And although there are about a zillion Windows forums, try finding a single one with the level of support and comaraderie that you find right here.

tgeer

---

### Post by CatKiller on 2009-08-20
> **mbuehl said:**
> I've been a computer guy for as long as I can remember. I've worked at a helpdesk supporting relatively complex windows issues for the better part of 5 years, and am going to begin soon the last 2 years of my college education in Software Engineering.

You might think that this would mean that you'd find it easiest to use Linux. It doesn't. You guys have it the hardest.

All that time that you thought you were learning how to use "computers," you were largely just learning to use "Windows." To effectively use Linux a Windows power-user needs to unlearn all kinds of Windows habits, which can be quite frustrating; nothing works in the "only" way that it should. To make the mental switch you need to be both open to expanding your horizons, and quite inquisitive. It helps to have a reasonable amount of time to just play, and these forums are a good safety net in case your experimentation breaks something that you can't fix.

A handy example of the kinds of habits that make the Windows power user's Linux approach difficult is the way that you install software. As far as they are concerned, finding some random application on some random website and downloading an executable to double-click to install must be the only way, right? And then they have to remember to go back to that website periodically to see if there's a new version available. Ubuntu doesn't use anything so primitive; downloading something from some website is just about the last method that you'd want to use. Most things that you'd want to install are just a tick in a box away through the package manager, and all updates to all software installed through the package manager happen automatically.

You seem like you're taking the right approach. I wish you good fortune in your continued use of Linux.

---

### Post by mbuehl on 2009-08-21
Unlearning my windows tricks has been, thusfar, the most aggravating thing. I know what seems like an endless amount of windows related shortcuts, fixes, etc - and now none of them work (example, i had like... 4 different firefox instances running, and i needed to get to my desktop, so i mashed windows-D about 6 times before I realized it wasn't going to work.)

I wish I had the freetime that'll probably be needed to immerse myself in this and really try to grasp the inner-workings of Linux, hah. I'm definitely not giving up on it!

Also, I had to dig through 16 pages of threads on these forums before I found mine... which was posted last night. That's crazy amounts of activity! I can already tell that the best part about this whole thing is going to be the community.

Cheers, friends - here's hoping I'm answering some questions around here some day!

-m

---

### Post by CatKiller on 2009-08-21
> **mbuehl said:**
> (example, i had like... 4 different firefox instances running, and i needed to get to my desktop, so i mashed windows-D about 6 times before I realized it wasn't going to work.)

You can set up Win-D to Show Desktop. Even better is to mouse-scroll on a bare patch of Desktop to get to a different workspace.

> Also, I had to dig through 16 pages of threads on these forums before I found mine... which was posted last night.

Search &#8594; Find All Your Posts

or, if you've got your preferences set up to subscribe to each thread you post in, 

User CP

But, yeah, there is a lot of activity here. No one can read every thread.

---

### Post by 3rdalbum on 2009-08-21
> **mbuehl said:**
> (example, i had like... 4 different firefox instances running, and i needed to get to my desktop, so i mashed windows-D about 6 times before I realized it wasn't going to work.)

Not only that, but you forgot that you had at least one clean desktop to go to :-)   Use the virtual desktops feature as much as you can. Once you've gotten used to it, it's absolutely indispensable.

Another shortcut for "show desktop" is to use Compiz's "Scale" plugin - I have mine set to the top-right corner of the screen. Scoot your mouse into the top-right corner of the screen, and when Compiz displays all your windows, just click on the desktop.

---

### Post by mal on 2009-08-21
Some more useful tutorial information:

[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

Have fun.

Mal

---

### Post by JKyleOKC on 2009-08-21
> **mbuehl said:**
> Also, I had to dig through 16 pages of threads on these forums before I found mine... which was posted last night. That's crazy amounts of activity! I can already tell that the best part about this whole thing is going to be the community.

Cheers, friends - here's hoping I'm answering some questions around here some day!

-mTo avoid such lengthy searches you can pull down the "Quick Links" menu from the top of the forum's main menu page, scroll down near the bottom of the resulting menu, and select "Subscribed Threads" which will take you to a page that lists all of the threads you have participated in.

It took me months to stumble across this feature of the forum, but it makes it simple to get back to a discussion after a few hours of activity have pushed it many pages down the list. When you post to any thread, you are automagically subscribed to that thread. If you want, you can delete your subscription from that list, or change how you are notified of thread activity -- but you don't have to do this unless you want to.

Hope this helps! And welcome to the wonderful wacky world of Linux and especially *buntu (from one who got started on mainframes, long before Microsoft came into existence)...

---

### Post by change_mode on 2009-08-21
If at some point you want to start learning about the command line, have a look at this site.

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by lykwydchykyn on 2009-08-21
Learning the internals of Linux was the best thing I ever did for my IT career.  Even if you don't work somewhere where they use Linux, knowing about it teaches you a lot about operating systems in general.  Kind of like the way learning a foreign language teaches you a lot about languages, and you end up understanding your native tongue a little better because of it.

Take your time with it and enjoy it, and don't try to make Linux act like Windows just because that's what you're used to.  Learn it for what it is.

---

### Post by exutable on 2009-08-21
As you can see the best part about Linux is probably the community that follows it :).  I can't think of any other OS, that has the communities Linux does.  IMO there is no "windows" forum that has so many experts compiled in one place.


Dane

---

