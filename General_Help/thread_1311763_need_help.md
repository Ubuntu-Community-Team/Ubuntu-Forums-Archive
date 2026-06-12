---
title: "need help"
date: 2009-11-02
forum: General Help
---

### Post by dr1986 on 2009-11-02
im no computer buff but i read an article in the paper which reccommended this OS sayin it was fast,reliable da da da now im not disputing this for 1 second but i think im way way way out my depth i thought it would be simple and easy to use and i didnt stop to think i shd check evrything out before fully installing ubuntu but me being me went ahead and jumped straight in now i wish i hadnt is there neway to get windows back on my computer without paying for it???? in desperate need of help plz!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Giblet5 on 2009-11-02
Not unless your PC came with a "Recovery" CD.

If it didn't, check the manufacturer's web. There is usually a way to download recovery disk images. You can burn those to blank media if you have a CD/DVD burner.

If it did come with "Recovery" disks, boot from the first one and follow the directions.

---

### Post by dr1986 on 2009-11-02
al go hav a look cheers for now i didnt mean 2 sound like a p**** sorry

---

### Post by coffeecat on 2009-11-02
Before you do anything, stop panicking and tell us exactly what you did, which Ubuntu CD you used, and what happens when you try to boot the computer up. The two most likely scenarios are:

That you accidentally told the installer to use the whole disc and you've lost Windows

OR

You've installed Ubuntu 9.10 and the installer has failed to put an entry for Windows on the grub boot menu. This seems to be happening to some people. If this is the case, you won't have lost Windows and the fix will be fairly straightforward.

---

### Post by dr1986 on 2009-11-02
i fully installed ubuntu and lost windows!

---

### Post by dr1986 on 2009-11-02
i dont have a recovery disc and i cant find the recovery program on my computer either

---

### Post by P4man on 2009-11-02
If you told the ubuntu installer to use the entire harddisk, then yes it would obviously wipe windows. The default option is a side by side install though, should give you dual boot with a boot menu to chose windows or ubuntu.

If you did lose windows (and want it back) you'll need to reinstall it from the cd that came with the computer or when you bought windows. If you have a oem machine the serial number for windows is usually on a sticker on the bottom or rear of the PC.

---

### Post by coffeecat on 2009-11-02
> **P4man said:**
> The default option is a side by side install though, should give you dual boot with a boot menu to chose windows or ubuntu.

Indeed.

@dr1986, are you sure you've lost Windows? You haven't told us why you think this. Check my last post again. There's a bug which causes the Windows entry in the grub menu to be missing in some installs of 9.10. That doesn't mean that Windows is missing.

---

### Post by dr1986 on 2009-11-02
i didnt choose the side by side option i wiped windows off! i have searched the smart restore program and its not on my computer either!

---

### Post by P4man on 2009-11-02
> **dr1986 said:**
> i didnt choose the side by side option i wiped windows off! i have searched the smart restore program and its not on my computer either!

Lets see if it is really gone. Go to applications > accessories > terminal.
In that "dos box" type this command:
```

sudo fdisk -l
```

(that is SUDO FDISK -L in lowercase)
Type your password when asked, dont worry if nothing appears on the screen, just type it and press enter. Then post the output of that command here (select it with your mouse and copy paste it)

---

### Post by dr1986 on 2009-11-02
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa226c290

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19109   153493011   83  Linux
/dev/sda2           19110       19457     2795310    5  Extended
/dev/sda5           19110       19457     2795278+  82  Linux swap / Solaris
david@family-laptop:~$

---

### Post by t0p on 2009-11-02
> **dr1986 said:**
> i dont have a recovery disc and i cant find the recovery program on my computer either

Assuming that you *have* got rid of Windows and are not just suffering from the bug mentioned above: it sounds like you will have to contact the manufacturer or reseller who sold you your computer and ask them about obtaining a recovery disk or installation cd.  If you go to the manufacturer/reseller's web site, there might be something there about how to download or otherwise obtain a recovery disk.

Alternatively, you could forget Windows and just carry on with Ubuntu.  You might be bewildered right now at the difference between Ubuntu and Windows; but this isn't unusual.  You just need to learn how to do things in the new OS.  There's a lot of helpful info, guides etc at [help.ubuntu.com]("http://help.ubuntu.com") and [wiki.ubuntu.com]("http://wiki.ubuntu.com"), plus you will find many links to good guides in the sigs of various forum members.  And of course you can ask for help here - this community is extremely friendly and helpful.

So welcome to Ubuntu!  I hope you'll stick around.

---

### Post by P4man on 2009-11-02
Looks like you didnt do a side by side install. Windows is gone.
Not much we can do about that. Either stick with ubuntu or get a windows cd. If you own a legal windows licence, you should be able to order a cd from your PC vendor for a small fee.

---

### Post by dr1986 on 2009-11-02
bewildered is right i tried to download itunes and there was some kinda error occurred then i tried to download adobe flash player 10 and couldnt do tht either

---

### Post by coffeecat on 2009-11-02
> **dr1986 said:**
> bewildered is right i tried to download itunes and there was some kinda error occurred then i tried to download adobe flash player 10 and couldnt do tht either

Whoa! Hold it right there! :) Read t0p's post again about how helpful this community and forum is and then tell us what software you want to install. Installing software in Ubuntu is **much** easier than in Windows, but **do not download anything from the internet**, the way you do in Windows. You can do everything from the package manager or the 'Software Centre' if you're using 9.10.

I've got to go to bed now, so I'll leave others to tell you what to use as an iTunes replacement and how to get Adobe flash, and all the other multimedia goodies you'll be needing.

Good luck!

---

### Post by x C0MMAND0 x on 2009-11-02
Did you install a 32bit or 64bit version of Ubuntu?  I would recommend Banshee as a media player.

---

### Post by dr1986 on 2009-11-02
so if i cant use itunes wot will i use and how will i update my iphone software? also how do i solve the problem with with my flash player?

---

### Post by dr1986 on 2009-11-02
not sure if if it was 32 or 64 bit but its the 9.10 version

---

### Post by blur xc on 2009-11-02
> **dr1986 said:**
> bewildered is right i tried to download itunes and there was some kinda error occurred then i tried to download adobe flash player 10 and couldnt do tht either

First- regarding your original post- "easy" is very relative...  Ubuntu is not hard, but there is a good learning curve.

2nd- all (almost all) applications for Linux in general is distributed through an "app store", called repositories.  Check your Applications menu and select "Add/Remove Programs".  it's not as pretty as Apple's app store, but all the apps are free.  Do a bit of googling, read the links, help, etc., and you'll get the hang of it.  I've been at it a few months now and I can't imagine going back to the windows way of installing software.  

the hard part, imo, is finding what software packages are worth installing...  

Give it a fair effort.  You might be surprised.

Be prepared though, the Linux community in general is less than tolerant of computer illiterate users.  They tend to try to nudge you into understanding a bit of how the OS works, and the help they give may be a bit hard to understand at first.  Don't fear the command line, it's by far the most powerful way to interact w/ your OS, and the easiest way to diagnose a problem.  It's just the least intuitive way to do anything...  It's also true of windows.  I have had windows tech support give me command line instructions too.

In the mean time, download and read this pdf- [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

BM

---

### Post by dr1986 on 2009-11-02
when i try to install anything it says it cant find the adobe plug-in i've tried downloading adobe and cant this is the message i get: 
 E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by P4man on 2009-11-02
> **dr1986 said:**
> when i try to install anything it says it cant find the adobe plug-in i've tried downloading adobe and cant this is the message i get: 
 E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

we are off to a good start :)
I dont know how you tried installing it initially, but that probably messed it up.

Try this in a terminal to remove your previous attempts:
```

**sudo** dpkg --purge --force-all adobe-flashplugin
```

copy paste that to avoid typos: You can paste in terminal with shift + control +v  or middle mouse button.

Next lets set up some extra software sources. Go to system  > administration > software sources and select the restricted and multiverse repositories.  Click Ok and let it reload the list.

Next lets install flash as well as a bunch of codecs and stuff youll need. Go to ubuntu software center and search for "ubuntu restricted extras" Install it.

---

### Post by t0p on 2009-11-02
> **dr1986 said:**
> when i try to install anything it says it cant find the adobe plug-in i've tried downloading adobe and cant this is the message i get: 
 E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Go to **System > Administration > Software Sources** and make sure you check the boxes for Canonical supported Open Source software (main), Community maintained Open Source software (universe), proprietary drivers for devices (rstricted), and Software restricted by copyright or legal issues (multiverse).  Then you need to reload to get all the lists of software downloaded to your computer: you may be offered a chance to hit "Reload", or you may have to open a terminal (**Applications > Accessories > Terminal**) and type in the command

```
sudo apt-get update
```You'll be prompted for your password.  Type in your user password (the letters won't show on the screen; don't worry, that's normal) and hit Enter.  Lists of software will download to your computer.

Once that's done, you should be able to install what you want.  You can install the Adobe flash plugin by typing into the terminal

```
sudo apt-get install flashplugin-nonfree
```Alternatively, you can install the flash plugin, plus java, the codecs for mp3s, and a lot of other stuff needed for media by typing

```
sudo apt-get install ubuntu-restricted-extras
```Give that all a go.  If you need help with anything else, start another thread.  We're all happy to help if we can!  :)

---

### Post by dr1986 on 2009-11-02
only have the restricted and multiverse selected? then is it the revert button i click?

---

### Post by P4man on 2009-11-02
> **dr1986 said:**
> only have the restricted and multiverse selected? then is it the revert button i click?

No Keep the the first two as well (main and universe)
then click close (it will prompt you to reload the sources list)
revert means undo.

---

### Post by P4man on 2009-11-02
btw dont worry if you get errors about keys not being verified. The ubuntu key server is down at the moment, but you can ignore those messages.

Im off for tonight but I trust others will help you further should you need help.

---

### Post by Unitux on 2009-11-02
> **dr1986 said:**
> i fully installed ubuntu and lost windows!

cool. :D

---

### Post by dr1986 on 2009-11-02
still get tht message!!

---

### Post by scout4536 on 2009-11-02
Post #22 is how I did it, and now Flash works just fine.  I was afraid of switching to Ubuntu last month, but when I did, I don't regret it at all.  I am now an official Ubuntu user and will never go back to windows.  Sure learning the basics was a little steep, but once you catch on it's not hard at all.  Terminal is my friend.

---

### Post by dr1986 on 2009-11-02
i tried evrything post #22 suggested and still the same problem

---

### Post by scout4536 on 2009-11-02
Under Software Sources what all do you have checked?

ie....(main) (universe) (restricted) (multiverse)

and under the Other Software tab--I have both Canonical websites checked.

Then click close and revert then try post #22

---

### Post by wildweathel on 2009-11-02
Just a reminder, you don't want to download software from the web to install.  

I'm going to assume you're running the freshly-released version of Ubuntu: 9.10, more commonly known as "Karmic Koala," or just "Karmic."  Easiest way to check which version you have is (System -> Administration -> Software Sources -> Updates)  Look at the Ubuntu Updates checkboxes.  Karmic will have ones labeled "karmic-security," "karmic-updates," etc.   Other versions will have a different codename like jaunty or intrepid or hardy.

When you're looking for something, try the software center first (Applications -> Ubuntu Software Center).  Type "flash", click Adobe Flash Plugin, try to install from there.  Does it still give an error, or does that work?

If you need help, these forums are a great place to look.  Also, you can try the freenode #ubuntu channel for real-time help.  So, here's a quick how-to of setting that up.

There's an envelope icon in the right of the top menubar.  Click, then "Empathy" to start the chat/IM client.  It won't pop up a window to start.  Click, then "Empathy" again, then Edit -> Accounts.  

Add -> Add new "IRC" account -> 
Network: FreeNode
Nickname: *Pick something, preferably fairly short.  If you choose one that's already claimed, you'll get a message from NickServ when you first log in.  If that happens, no big deal, just go back to the preferences and change it.  Once you're logged in, you can permanently claim your nickname if you like.*
Password: *Leave this blank for now.*
Real Name: *You can fill this in if you like, but you don't have to.  Other people can read it when you're online.*
Quit Message: *Some people say it's polite to leave this blank.  Not everyone does, though.*

Now you can click connect.  If your name's taken, NickServ will send you a polite message about that, and you should try another nickname.  If not, you can register your name.  

To do that, Chat -> New Conversation and talk with NickServ.  He's not a real person, but a "bot," a chat computer program.  NickServ is the nickname bouncer.  He'll kick anyone who tries to use your nickname.  For more information, say "help" to him.  Then, "help register," finally "register *password e-mail*" to register your current nickname.  If you go back to Epiphany's account settings, you can save your password there, and Epiphany will automatically identify whenever you log in. 

Now that that's taken care of, you can join the #ubuntu with Channel -> Join -> "#ubuntu".  Feel free to just lurk, or if you have a question, go ahead and ask.

Sorry you lost Windows.  If you're having trouble feel free to a) try FreeNode or b) make a thread in the forum and then PM me to get my attention.  I'll look at anything you have trouble with--just post it in a public thread first so other people have a chance to help, too.

---

### Post by dr1986 on 2009-11-02
so far so gd got the flash sorted now i take it i cant run itunes at all?

---

### Post by themusicalduck on 2009-11-02
Nope, you can't run itunes. Unless you run it in a virtual machine, but if you don't have a copy of Windows on hand then you can't really install it into a virtual machine. You mentioned you have an iphone and I'm not sure how good iphone support is on Ubuntu.. I suspect it isn't perfect. But googling around should tell you how good it is.

However, if you only want music playing software, then you could try Amarok, Banshee or Songbird. I use Amarok, but Banshee seems to be pretty popular.

I also recommend downloading VLC for playing videos and things.

All of those programs are in the Ubuntu Software Center except for Songbird, which you could download from here: [http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

You'll probably need to top option, Jaunty 32 bits.

---

### Post by ikacer on 2009-11-02
> **dr1986 said:**
> so if i cant use itunes wot will i use and how will i update my iphone software?

Getting an iphone to work with Ubuntu is really, really complicated because Apple doesn't offer a Linux version of itunes. That said, there still are ways to use your iphone with Ubuntu. Here is a page on it:
[https://help.ubuntu.com/community/PortableDevices/iPhone]("https://help.ubuntu.com/community/PortableDevices/iPhone")

One glance at that page can show how complicated it is. ***I think if you are planning on keeping your iphone, then you should have Windows installed.***

If you still want to use Ubuntu, you can set up a dual-boot system. When you find your recovery disc, you can reinstall windows, then install Ubuntu and choose the option to install them side by side. Then when you turn on your computer it will give you the option which system you want to boot into.

In summary, I think you either need to go back to windows, or set up a dual-boot system (which is really easy to do), or else you won't be able to sync your iphone anymore.

Discliamer: I could be wrong about this as I don't have an iphone.

---

### Post by scout4536 on 2009-11-02
For iTunes, I use Songbird 1.2.0 with the iPod plugin, it syncs my ipod with my music library.  Although I still have not figured out how to add the album art on my iPod, the songbird version I have only puts the songs on it, but I do not know if songbird has a later version, I just use 1.2.0 cause I know it works well with what I want it to do.  You can also buy music using songbird, so iTunes is pretty useless to me now.  I have heard of running iTunes using the program called Wine, but I have yet to venture this far in Linux.  Of everything Windows has I have found an equal for in Ubuntu.  So it made my transition to Ubuntu that much better.  But yes installing software is a bit different, but once you get the hang of it, it's easy.

---

### Post by Steve60938 on 2009-11-02
I didn't read all of this but I can definitely identify with the "new ubuntu user" feeling. I'm still no where near even a novice level but I do know this. If its something your trying to do or install or fix someone else has tried it first. Google Google Google lets say you want to know how to install itunes in ubuntu go to [www.google.com](www.google.com) and type in "itunes in ubuntu" worst case senario you find out you can't do it. If you run into something you don't understand no problem just come here and ask like "what does sudo mean\do" ubuntu for me is very difficult. I was no good when dos was used with the big floppy discs either I'm no good in console but it is by far the fastest and most efficiant of the big three (windows,Macintosh,linux<--I've only used ubuntu) Its worth trying out. As far as your windows as long as you have your Cd code or can get it from whomever you bought the pc from You can, and I don't know how legal this is, Download a windows image and use your legal key when installing just make sure its the right windows...eg home or professional or x86\x64 .

---

### Post by P4man on 2009-11-03
Most people I know that migrated from windows to ubuntu spent at least 6 months dual booting their system, to give them time to learn the new OS, fix problems, find and learn alternatives to their known windows apps. I guess circumstances force you to fasttrack this a bit lol, but on the bright side, you already seem to have ubuntu installed and running properly (since you havent asked, I assume your network, wifi, videocard, sound etc are all working?), it takes many people a lot longer to get there. Some never get that far.

I would still suggest you try and obtain a windows cd that you can use with your licence/serial key. Its always good to have something to fall back on, and if nothing else, you can use the cd and windows licence to run windows *inside* ubuntu (using [virtualbox]("http://www.virtualbox.org/"), a virtual machine). That will enable you to run those few windows apps that you can not find ubuntu alternatives for (iTunes to name one).

In the meanwhile, try and enjoy the benefits you're currently getting. You just rid yourself of all known virus and worm threats. As long as you stick to  installing software from the repositories, you are immune to any malware (and even outside the repositories the risk is pretty much non existent), there is as good as no software to be found that costs money and there is some pretty damn nice software for you to play with.  You have full control over your machine and you can tweak and change and personalise beyond your wildest imagination.  

A few pointers:
Enable compiz, install compiz settings manager and get effects and tools such as these:
[http://www.youtube.com/watch?v=I0B8yNvaSxQ](http://www.youtube.com/watch?v=I0B8yNvaSxQ)
If you dont like the desktop environment offered by gnome (ubuntu) you can install another one called KDE (kubuntu) with just a few mouseclicks. KDE looks like this:
[http://www.youtube.com/watch?v=6FM0jYfp26M](http://www.youtube.com/watch?v=6FM0jYfp26M)
And is arguably more resemblant to windows. If you dont like it, no worries, remove it again or just chose which desktop manager (kde or gnome) you want when you log in. Perhaps your kids prefer KDE :)

---

### Post by coffeecat on 2009-11-03
**dr1986**, now that it's morning again here in the UK I can rejoin this thread and it's good to see how far you've got.

One thing you haven't mentioned which you might want is being able to play commercial encrypted DVDs. If you do want to play DVDs, it's quite easy.

First, did you install the package 'ubuntu-restricted-extras' as someone suggested? If you didn't, do it now. It contains the libdvdread library for reading DVDs and a load of necessary codecs.

Now go to [http://www.medibuntu.org/](http://www.medibuntu.org/) . Go to the Repository HowTo and follow the instructions to add the medibuntu repository. Then open System > Administration > Synaptic and use that to install the package libdvdcss2. Without libdvdcss2 you can't play commercial copy-protected DVDs. Or you could use Software Centre instead of Synaptic if you prefer. By the way, someone mentioned the Add/Remove application. That was in earlier versions of Ubuntu. In the 9.10 version you're using, Add/Remove has been replaced with Software Centre.

If you do all that, you should be able to play DVDs with the default Move Player app (Totem), but someone suggested you install VLC. I second that. VLC is an excellent all-round media player. What can you lose by installing it? After all, it's free! Welcome to the world of open-source. :)

---

