---
title: "Thinking about switching to Ubuntu- would like some advice"
date: 2009-11-03
forum: General Help
---

### Post by Ruiizu1990 on 2009-11-03
Hi,
I've been a Windows user for as long as I've been using computers. 
However, for a while now, I've been thinking about switching to Ubuntu. I'm tired of the crashes, and having to fork out stupid money for new versions of Windows. I need to know- Is Ubuntu right for me?
I use my computer for mostly web browsing, music, photos etc, but I also run graphic applications such as Photoshop. 
 
Few questions
1. I'm currently using Vista 64 bit, OEM edition. I want to remove Vista completely, but keep all my programmes, like Firefox, anti-virus etc. Is this possible? I need some advice on how to do this.

2. Does Ubuntu use less RAM and system resources than Vista?

3. Is there anything else I need to know about Ubuntu before I install it?

Sorry if this is posted in the wrong place- I'm still a noob here.
Thanks for reading
~Ruiizu1990

---

### Post by SpitfireSMS on 2009-11-03
1. I'm currently using Vista 64 bit, OEM edition. I want to remove Vista completely, but keep all my programmes, like Firefox, anti-virus etc. Is this possible? I need some advice on how to do this.

This is not even possible when upgrading from windows version to windows version, and its absolutely not going to be possible to bring them over to Ubuntu. It is, however, VERY easy to install everything you need.
Photoshop is a Windows program, and wont run on Linux really. You can get Photoshop working through Wine(a Windows emulator) but I think it only supports up to CS2. Ubuntu does come with a free alternative to photoshop, called GIMP. Ubuntu also comes with Firefox preinstalled, it is the default browser. You wont need an anti-virus becuase Ubuntu is not going to get a virus.


2. Does Ubuntu use less RAM and system resources than Vista?

Excuse the french, but HELL yes. I couldnt run Vista on my laptop because it only has 2GB, but Ubuntu FLIES with 2GB

3. Is there anything else I need to know about Ubuntu before I install it?


It seems that you need to get your head wrapped around the idea that Ubuntu will be entirely different. Your programs, .exe type things your used to will not run(or not run well), and many things will be very different.




My advice: Download and burn a Live-CD. You can then boot into Ubuntu without changing anything on your computer, and give yourself a chance to play around with it a little. If you like it, you can install it and have full functionality

---

### Post by jimmy the saint on 2009-11-03
First Question:  Firefox comes already installed.  You don't need antivirus, but if you want some, clamAV is free and can easily be installed from the repositories, also it is free.  If you aren't overly attached to Photoshop, The Gimp provides much of the same function and if you figured out photoshop, you shouldn't have too much trouble figuring out the gimp.

Second Question:  Ubuntu uses far less resources than Vista.  You can get Ubuntu running on a machine with 512MB of ram.  Good luck with vista on a machine like that.  

Third Question:  BACK UP YOUR IMPORTANT DATA BEFORE YOU EVEN THINK ABOUT CONSIDERING DREAMING ABOUT DOING ANYTHING!!  Other than that, download the iso and burn the CD.  This will give you a LiveCD that you can put in your Drive and boot from.  You can play with Ubuntu till your hearts content without even needing to install it!  Just remember that any changes you make will be lost when you shut down the machine.  Definitley try the LiveCD first to see if you like it, and to make sure that you don't hit any hardware bugs.  Better to know these things before an installation!

> Excuse the french, but HELL yes. I couldnt run Vista on my laptop because it only has 2GB, but Ubuntu FLIES with 2GB
I failed French, but I am pretty sure that isn't French.

---

### Post by a cup of tea on 2009-11-03
If you want to keep your bookmarks and such in Firefox, you could try backing up your Firefox profile to bring it with you (see [http://support.mozilla.com/en-US/kb/Backing+up+your+information](http://support.mozilla.com/en-US/kb/Backing+up+your+information) ).

I haven't actually tried doing that. I use an extension called Xmarks that saves all my bookmarks and syncs them between computers.

You aren't going to save Firefox itself onto a disk to bring it with you to Ubuntu, but you can bring your settings and bookmarks.

---

### Post by dasunst3r on 2009-11-03
You should also try out Ubuntu using a LiveCD.  It boots into something that closely resembles a default installation, although it will be a bit slow (since it runs on CD) and you won't get 3D acceleration (can't install graphics drivers).

What other programs are you using besides Firefox, Photoshop, etc.?

---

### Post by nvikram on 2009-11-03
The Ubuntu Migration Assistant may be able to help you move over some documents during the install process. I have never tried this feature out myself, so I can't testify in it's usefulness. I think that GIMP is pretty easy to get used to. If you want to get into the feel of things I would suggest you try windows versions of the same open source software. You can find almost all the things in ubuntu for windows as well. It's just a simple google away.

---

### Post by QIII on 2009-11-03
Careful on the advice about memory.

Some people are shocked because they think that they have found that *nix systems are using more memory.  

Linux uses memory differently.  What may seem like more memory "used" can, in fact, be memory that has been "deallocated" for use by a particular application, but the OS still keeps it on hand to quickly dole it out again when requested...

"Unused memory is wasted memory."

My OpenSolaris machine starts up grabbing 75% of my memory.  It's not gone.  Grandma Solaris is just handing out the cookies.

---

### Post by ranch hand on 2009-11-03
You have to realize that linux is based on unix, an old, secure OS.  It is not related, in any way to any MS system.  Your programs ore not compatible.  Linux has its own programs that will not run on MS.

Get the liveCD for 9.04 (9.10 is a little raw yet) and try it on your box, use it, see what you think.  There are other Linux OS' out there, try them the same way.  See what YOU like.

One think you could do before jumping in the deep end is get a small external HDD and install on it and use it at speed ( the live CD is slow).

---

### Post by wildweathel on 2009-11-04
> **Ruiizu1990 said:**
> Hi,
I use my computer for mostly web browsing, music, photos etc, but I also run graphic applications such as Photoshop. 

Photoshop is gonna be the only difficulty.  GIMP is not as powerful as Photoshop, at least not yet.  If you doodle, it may not be a huge deal.  If you're a professional photographer who must have Photoshop, you'll have to keep a Windows or OS X install for that.

> 
Few questions
1. I'm currently using Vista 64 bit, OEM edition. I want to remove Vista completely, but keep all my programmes, like Firefox, anti-virus etc. Is this possible? I need some advice on how to do this.
Do you have a re-install disk?  If so, you can reinstall Vista inside Ubuntu.  For example, I have Karmic Koala as my main operating system and Windows XP installed using an application called Virtualbox.

Linux anti-virus is primarily used on e-mail servers to remove Windows viruses.  The Unix security philosophy is very different, and you don't need anti-virus or anti-virus subscriptions for your personal computer.   You do other things to stay safe, like not installing untrusted programs and keeping your computer up to date.  (Our patches are released as soon as they're ready, Microsoft has one "patch tuesday" a month.)

Ubuntu *can* run Windows programs, but not very well.  It's usually best to find a substitute.  Sometimes the substitute is better, sometimes it's not, and sometimes (Firefox, for example) the same program runs on both.  Usually, they're fairly similar: web, photos, music will feel very familiar--the difference between Vista and Ubuntu is about as much as the difference between Vista and XP or OS X.

There are really three place- where Ubuntu falls short: very new and very old hardware may not be supported as well as on Windows, many "professional standard" programs (AutoCAD, Maya, Photoshop) don't have competitive equivalents, and Ubuntu doesn't support "un-free" media formats quite as well as Windows.

(Basically, some software can't ship on the CD.  So, you have to install it by opening the Software Center and searching for ubuntu restricted extras.  That gives you flash, mp3, most video formats, all in one download.)

> 
2. Does Ubuntu use less RAM and system resources than Vista?
Ubuntu will use all your RAM.  There's no point leaving it sitting there unused.  However, the answer is still "yes."  Ubuntu is faster than Vista on the same computer and will run well on a computer that can barely handle Vista.   My laptop can't run Aero Glass, but it has no problem running the Ubuntu equivalent.

> 
3. Is there anything else I need to know about Ubuntu before I install it?
Ubuntu is part of the greater "free software community."  The highest value in this community is a kind of curiosity, the willingness to take things apart, understand how they work and put them back together--so much so that "free" actually refers to the *free*dom to change and share, not *free *of charge.

There's a lot of free-of-charge help here, but it's kind of like a classic-motorcycle convention.  You'll have best luck if you approach with humility, an openness to understanding, a sense of humor, and a sense of responsibility.  Proprietary software you buy as a solution.  Money goes that way, working computer goes the other way.  Free software is more like keeping a garden or building a kit car.  Ubuntu's one of the easiest on the block to get running, supported by a diverse community of enthusiasts, hot-roddable in the extreme, but ultimately you're responsible for making it your own limited only by your own knowledge and patience.  Welcome to freedom.

If you're not drawn towards that particular ideal, that's quite alright.  Ubuntu tries to be, and largely succeeds in being, a functional and easy to use operating system (and more.  No commercial operating system ships with a complete office suite, ready to install thousands of free applications with a few clicks and a fast Internet connection).  If you choose, you can leave the kit unmodified and it will run great as is though maybe with some warts and rough edges that could just be polished up with an angle grinder and some paint...  Just be prepared to rub elbows with enthusiastic people, real chip-heads.   A touch of humility, some curiosity to understand *why* something is or isn't working, and a sense of humor will go a long way.

Right, enough philosophy.  I think the best way to try Ubuntu is to use Wubi. 

Wubi will take a Live CD image and install it to your Windows hard drive.  Then, you can reboot and run Ubuntu.  If you don't like it, it's as easy to uninstall as a well-written Windows app.  You'll need 5 GB of disk space and administrator access.

1) Get Bittorrent [http://www.bittorrent.com/](http://www.bittorrent.com/)
2) Download the 64-bit Live CD. [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent)  (It runs on Intel 64-bit processors, too)
3) Get [http://wubi-installer.org/](http://wubi-installer.org/)
4) Put ubuntu-9.10-desktop-amd64.iso in the same folder as wubi.exe
5) Run Wubi.  It'll ask some questions, then run the install. 
6) Have fun!

Further reading, if you're hungry for knowledge: 

[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html) -- The Ubuntu Pocket Guide absolutely love it.

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index) -- The Psychocats reference
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security) -- Explains why we don't have anti-virus.

This isn't school. (Yay!  I hated school...)  No one's going to fail you for not reading them.  If you prefer to just jump in and try, feel free to go ahead.

Finally, when you do have questions, this document is a quick overview of how to ask them in a way that most helps other people help you.  Unfortunately, the first paragraph was written in frustration over users writing really bad questions.  You're not asking bad questions, I'm just providing this as some things to keep in mind.

[http://www.gerv.net/hacking/how-to-ask-good-questions/](http://www.gerv.net/hacking/how-to-ask-good-questions/)

Thanks for your interest in Ubuntu.  I hope you enjoy it as much as I do.

---

### Post by ad_267 on 2009-11-04
I haven't read all of the other posts so sorry if this has been said already, but [SIZE="4"]Try it First![/SIZE]

Don't install a completely new operating system over Vista. Use the live CD or install using Wubi first to check that you actually want to switch.

---

### Post by Bonster on 2009-11-04
My mom only started using the computer for a few months.

Shes doing exactly what u want to do now loL =)
All she use it for is email, surfing, photoshop cs2 thru wine.

So yes you are the perfect person for linux in my opinion.

Hope that helps

P.S She uses Linux Mint, think you should try that since thats better for newbies in my opinion

---

### Post by rmccutchan on 2009-11-04
I am a new user of about 2 months and I wish I could add something to the previous posts, but they have given some great information.

My experience on the hardware side:  I bought a used dell with a pentium 4 and 1 gig of ram, installed Ubuntu,  and upgraded to 2 gigs of ram.  I didn't need to waste my money on ram.  I do digital photography and edit large photographs and have NEVER needed 2 gigs of ram.  One day, before I installed the extra ram, I tried to max out the ram and opened a bunch of applications on 4 desktops (open office, gimp, raw therapee, firefox, and I have wobbly windows and rotating desktops turned on) and had them all performing some kind of action, and only used 80% of the ram.  I already ordered and paid for the extra ram, so I kinda felt obligated, and installed it anyway.   Having said that, the processor was running at 100% during this test.

I must admit, I was a little nervous about wiping out windows, but as someone said before, Ubuntu really is easy to get to know.

---

### Post by rmccutchan on 2009-11-04
I forgot to mention that the people here on this forum are very knowledgeable and EXTREMELY helpful if you run into a jam and need some advice.

---

### Post by Ruiizu1990 on 2009-11-04
> This is not even possible when upgrading from windows version to windows version, and its absolutely not going to be possible to bring them over to Ubuntu. It is, however, VERY easy to install everything you need.
It's ok, i'll just back up my data on an external drive. I just wanted to know.


> What other programs are you using besides Firefox, Photoshop
I occasionally use WinRAR and DVDVideosoft. That's about it. Besides anti virus and anti malware programmes, which another poster stated were redundant with Ubuntu. 

> Photoshop is gonna be the only difficulty. GIMP is not as powerful as Photoshop, at least not yet. If you doodle, it may not be a huge deal. If you're a professional photographer who must have Photoshop, you'll have to keep a Windows or OS X install for that.
It's no biggie if I can't use Photoshop. I wouldn't call myself a photographer, I use Photoshop for drawing. What about Corel Painter? 

Another thing- In Vista I used Windows Media Player to organize music. What alternatives can I use in Ubuntu?

I'm gonna give the live CD a try.
Thanks to everyone who wrote back. Your comments have given me a lot to think about :)

---

### Post by 3rdalbum on 2009-11-04
DVDvideosoft is a company - they make about 14 different programs. I think you'll be able to get alternatives to all their stuff on Linux.

RAR archives are handled fine in Linux.

There are about a hundred and twenty different music players for Linux; the most common are Rhythmbox (preinstalled), Amarok, Banshee, Exaile, Songbird, and Listen. You're well served in this area :-)

I think you'll be a fine candidate for Linux. Good luck and have fun, and don't forget to ask for advice if you run into problems :-)

---

### Post by seenthelite on 2009-11-04
Lots of great advice but you can have the best of both worlds by keeping Vista and some of your programs you may prefer and dual booting with Ubuntu your computer is capable of doing that with ease, you will find you use Ubuntu the most  but Vista is still there if needed.

---

### Post by P4man on 2009-11-04
@wildweathel

Thats a great post you wrote there. I agreed with every single word. Right up to the end where you blow it by recommending a wubi install lol (=installation from inside windows) . Wubi gives too many problems IMHO and if the OP eventually wants to move to linux permanently he'll have to start from scratch. I would strongly recommend a regular side-by-side install. Its not much harder to do, and will give much more flexibility.

I do agree with everyone else though. Dont just go  and wipe windows until you are familiar enough with linux and happy with how it works for you. Try before you "buy".

---

### Post by 3rdalbum on 2009-11-04
I agree with P4man; don't use Wubi, it has several limitations that make it rather fragile and kinda impractical.

---

### Post by Ruiizu1990 on 2009-11-04
Ok, I've ordered a disc from Ubuntu.com and I'm planning to play around with the live install. I can't wait to try it out!

Another question- If I decide to install Ubuntu, will all my files (and Vista) be wiped from the Hard drive? I heard that somewhere before and I just wanted to clarify whether it's true or not.

---

### Post by wildweathel on 2009-11-04
Wiped?  Not unless you want to.  The installer can re-size your Vista installation.  The only thing to be careful of is that Vista doesn't shut-down by default, but hibernates--it saves the current running programs to hard-disk so it can later start back up with all programs running.  If it wakes up and has less hard-disk space, it might become confused.  Be sure to "restart" or "shutdown" before installing Ubuntu.

[http://www.janleow.com/life/windows-vista-sleep-hibernate-shutdown-suspend.html](http://www.janleow.com/life/windows-vista-sleep-hibernate-shutdown-suspend.html)

There's a possibility that the installer will make a mistake.  So, if there are files you can't afford to lose, you should have backup copies of them.  It's not likely--the resizing software is well-tested and mature, but it's better to be safe.

---

### Post by grandtoubab on 2009-11-04
Read the official
[http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)

[http://www.ubuntu.com/getubuntu/releasenotes/910overview](http://www.ubuntu.com/getubuntu/releasenotes/910overview)

[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)

Beware of the dog:lolflag:
[https://bugs.launchpad.net/ubuntu/karmic/+bugs?field.searchtext=&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu/karmic/+bugs?field.searchtext=&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

---

### Post by seenthelite on 2009-11-04
[This is also worth considering]("http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm")

[http://apcmag.com/the_definitive_dua...stepbystep.htm]("http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm")

---

### Post by ranch hand on 2009-11-04
Ordering disks  is great, I did tht when I was on a dial up connection.

You can download the buggers and burn them to disk yourself too.

---

### Post by P4man on 2009-11-04
Burning  disks is great. I did that when I still had a functional dvd drive in my notebook.

You can burn the buggers to an USB stick yourself too though. Faster, cheaper, more convenient.

;)

---

### Post by rich97 on 2009-11-04
You can do what is called a "dual boot." This is **my** preferred method as occasionally I need to access 7 to run Photoshop CS4.

[B]Disclaimer: The following is reasonably advanced, DO NOT rush in head first if you don't at least have a basic knowledge of how a computer works, research first. For this reason I'm going to explain it as if I was talking to a stoned two year old as I don't know your level of experiance. :P

And perhaps more importantly, ALWAYS, ALWAYS,&#12288;ALWAYS back up your data![/B]

Basically you separate your hard drive into 2 parts, this is called *partitioning*. Each partition has to be *formatted* in a certain way to allow the operating system to run off it.

Ubuntu and Windows use 2 different "file systems". Ubuntu runs off the *EXT* file system specifically ext2, ext3 and ext4, ext4 will give you greater speed but I've had a few issues relating to sharing file between Windows and Ubuntu (Ubuntu can read Windows but not vice versa).&#12288;Windows uses the NTFS file system so when you need to identify which part of the hard drive windows is on you look for NTFS.

Boot up your LiveCD you receive in the post, do not install just yet! In the top left of the screen there will be an "Administration" menu, click on that and select "GParted". A new window opens up, lots of bars at the top are a diagram of how your hard drive is partitioned.

Select the NTFS partition then click on Partition > Resize/Move. Drag the arrow down to how ever large or small you want to leave windows. If you get it wrong it's quite easy to resize at a later date. More information on resizing with Gparted can be found [here]("http://gparted.sourceforge.net/larry/resize/resizing.htm"). Do not select apply yet.

On the diagram you should now have some free space. Go to Partition > New. Make it a primary partition, use the (preferably) ext4 file system or (alternatively) ext3 file system, leave some space for whats called "swap space", if you have a laptop and you want to be able to hibernate you should leave double of what your RAM is, finally, click OK. Don't apply yet.

Once again go to Partition > New and this time create a logical partition, set it as a "Swap" file system and make it fill the space you left spare in the previous step. Click OK.

Finally, click apply and wait for it to partition your hard drive.

When that is done, click on administration and select "Install Ubuntu" go though the Menus until you reach the partitioning bit. When you get there make sure you don't use whole drive look for an option to install on your new ext3/ext4 partition. If worst comes to worst select it from the advanced partitioning dialogue (sorry I can't remember it exactly).

Click next untill it starts installing. Wait for it to install (generally less then half hour on a decent machine). After install restart and you should see an option to boot into either Windows or Ubuntu. If you don't see Windows post a question in these forums using your new Ubuntu installation and with a bit of hacking someone should be able to get you sorted.

With all of this, don't rush, consider things carefully, it is easy to lose data during partitioning.

Congrats! If you did everything correctly and there were no funny issues you can now use both and don't have to worry about restoring your computer to it's normal state! If you don't like Ubuntu (and you will if you put in the effort when trouble arises) then you simply delete the Ubuntu partition and resize your windows back to normal!

One last time (say it with me): **ALWAYS REMEMBER TO BACK UP YOUR DATA!**

Hope that helps somewhat. ;)

---

### Post by madtownidiot on 2009-11-04
I just installed the 64bit version on my laptop (Hp Compaq 6910p) using a flash drive. everything works right from the beginning, it starts up and shuts down faster than a fresh install of windows XP, and it uses less memory (not that that's a problem with 4Gb), but definitely try it. I would recommend downloading unetbootin and installing the iso file on a flash drive to do the installation. it cuts down on the install time by at least 20 minutes. easiest way to install.. once you have downloaded the iso file.. start with the x86 version if you don't know which one to use.. then dowload unetbootin here:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
it's pretty easy to use. you need a 1GB or larger flash drive 
restart your computer and make sure to enable boot from usb

---

### Post by Ruiizu1990 on 2009-11-05
I'm still waiting on the disc to arrive, but thanks again to everyone who offered advice- love the community spirit here!

Is there anyone else who made the switch from Windows Vista to Ubuntu and can share their experiences (good or bad) with me?

Also, how long does it take for someone (on average) who has no prior knowledge of Ubuntu to learn how to use the system effienciently? I'm curious to know how long it took other users to get up and running.

---

### Post by muhannadfa on 2009-11-05
> **Ruiizu1990 said:**
> Hi,
I've been a Windows user for as long as I've been using computers. 
However, for a while now, I've been thinking about switching to Ubuntu. I'm tired of the crashes, and having to fork out stupid money for new versions of Windows. I need to know- Is Ubuntu right for me?
I use my computer for mostly web browsing, music, photos etc, but I also run graphic applications such as Photoshop. 
 
Few questions
1. I'm currently using Vista 64 bit, OEM edition. I want to remove Vista completely, but keep all my programmes, like Firefox, anti-virus etc. Is this possible? I need some advice on how to do this.

2. Does Ubuntu use less RAM and system resources than Vista?

3. Is there anything else I need to know about Ubuntu before I install it?

Sorry if this is posted in the wrong place- I'm still a noob here.
Thanks for reading
~Ruiizu1990

My advice to u to go windows 7, ubuntu doesnt't stand a chance in front of it :lolflag:

---

### Post by kixome on 2009-11-05
if you wan't a faster firefox, then message me

---

### Post by kixome on 2009-11-05
also yes, if not on extremely new HW then ubuntu 8.04 is right for you!

---

### Post by 3rdalbum on 2009-11-05
> Also, how long does it take for someone (on average) who has no prior knowledge of Ubuntu to learn how to use the system effienciently? I'm curious to know how long it took other users to get up and running.

It took me about 6 months to get to the stage where I felt I was an average Ubuntu user, but it may take you less as Ubuntu is easier these days. It also depends on what you decide you want to do with Ubuntu and how much you use it and play around.

---

### Post by kixome on 2009-11-05
took me a month, but i am a fast learner/shooter with a very long memory, and learn linux, not just ubuntu to be proficient!

---

### Post by P4man on 2009-11-05
> **Ruiizu1990 said:**
> I'm still waiting on the disc to arrive, but thanks again to everyone who offered advice- love the community spirit here!

Is there anyone else who made the switch from Windows Vista to Ubuntu and can share their experiences (good or bad) with me?

Also, how long does it take for someone (on average) who has no prior knowledge of Ubuntu to learn how to use the system effienciently? I'm curious to know how long it took other users to get up and running.

Every user and almost every machine is different so there is no telling. 

Some people get up and running pretty much instantly because all their hardware works out of the box and they are very happy with the default set of apps or what they find in the software centre. 

Others may never fully convert because of hardware compatibility issues, because they can't live without their latest windows games or they depend  too much on some specific (professional) software for which they cant find equal linux alternatives. 

For instance, I have yet to find an Adobe Premiere quality videoeditor. Latest versions of Kdenlive come close but isnt quite there yet. Others may stumble (or dual boot or run VMs) because there is no software for their iPhone (there is no linux iTunes). Finally some people just dont like it, or are unwilling to relearn their acquired skills.

FWIW, Ive used DOS since 3.3 and every windows and OS/2 version ever released. Ive booted various linux distro's a few times since 2000 but only found it worth pursuing in 2007. Took me 6 months or so of dual booting before I "flipped the switch" and used it as my main OS. But even today I still have windows on a dusty partition for an occasional game and I have 2 windows installation that run on virtual machines inside ubuntu mostly for professional / testing reasons.

Your mileage may not varry, it will varry. Find out :)

BTW, shipit.com takes a long time (4-10 weeks). Is there any reason you are not downloading ubuntu rather than waiting for the CD ?

---

### Post by Stolea on 2009-11-05
I have been Linuxing now for 2.5 years. Its a great platform to work from. Certainly a lot more stable than any Windoze offerings.
The only two things that force me to maintain a windoze system is Quickbooks business accounting and my Divico TV card that doesn't want to play nicely under Ubuntu.
I use vbox to run Quickbooks because I have not found anything in the Linux world that comes even anywhere near its functionality. And I really don't fancy setting up 2500 products all over again. I need Dreamweaver for my website and Photoshop for some of its advanced features.
But for all other tasks I use native Linux programs, a lot of which are better and faster than anything Windoze has to offer.
I won't go into the problems with the TV tuner because I suspect that part of the problem is my lack of understanding of some things.

The main thing to bear in mind: Ubuntu is free and has a great community support network. And there is no such thing as a trouble free OS, but Linux certainly goes a long way down that path.

---

### Post by rich97 on 2009-11-05
Well, it depends how much you want to learn. For word processing, Internet, browsing basic desktop customization then maybe a few hours. But this is the great thing about Linux, if you want to learn more there is a whole world of opportunity when it comes to learning the ins and outs of an operating system.

Windows has a closed architecture, if you want to dig deeper into the OS, change the look, optimize a certain setting, etc. you are restricted to hacks or what MS have provided for you. For most people, this is OK, they just want their applications to work.

For Linux users this isn't enough I want the power to make my computer my own. There are 1000s of ways you can modify your system to make it your own. If you don't like how a certain function works there are most likely at least 3 free alternatives. Being someone who is very concerned with design I was not happy at all with the look of 9.04, it was just... drab at least in my eyes, so what did I do? I replaced the default software that manages how my computer renders the desktop. Then I was able to install themes for that new software (called emerald) which I felt were much better.

To illustrate what you can do with enough fiddling check out this video [http://www.youtube.com/watch?v=_ImW0-MgR8I]("http://www.youtube.com/watch?v=_ImW0-MgR8I"). Of course, most of these effects may be pointless and even annoying but the point is they are there if you want them. Some people hate this, but thats OK they can just leave it and reduce thier desktop to a minimum working standard. Or if they feel Ubuntu is to fancy, well they can just pick a different distro.

Of course this isn't limited to how your desktop looks, the possibilities are endless.

In summary, learn however much you want to learn, as someone stated earlier the point of switching to and Linux based system is to have the freedom of choice that comes with it. There are some issues still bugging Linux (hardware and software compatibility mostly) but I have learned enough to work around those issues within a couple of hours. And at the end of the day if I can't find the software I want (a major rarity) I have a small windows install I have on here to go to.

Put in the effort and you will learn to love. ;)

---

### Post by ranch hand on 2009-11-05
@Ruiizu1990
> 
Is there anyone else who made the switch from Windows Vista to Ubuntu and can share their experiences (good or bad) with me?

I did.

Right about the same time I joined these forums.

My wife bought this box when our 10 year old box died of power supply going and taking the mother board with it.

Came with Vista Home Premium. We were excited. Then we got it up and running. Took me 3 days to realize that it had to go or I would have a stroke. Took my wife 3 weeks. My son suggested Ubuntu.

Then the trouble started. it was too much fun. I broke the OS (and had no idea how to fix it) 5 times in a week. The wife was a little pissed. Her idea, don't laugh, is that you should be able to USE your computer.

I dual booted this bugger. Hardy and Hardy. One for work, one for play. Nothing was doneto the work OS until it had been done to the play OS, including updates. I have not had that work install of Hardy down since.

If all my Ubuntus go down I can use Debian, if it goes down I can always use Mandriva. There is no way that MS will ever again pollute this box.

The specs for this box are in the sig (a good thing to do so folks trying to help know what you are running).  The old one was a P2 box with 350MHz and 128Mb ram.  This box was slower doing average things than the old one running 98.

Under Ubuntu this thing runs like a striped ape.

I bought a new HDD to put Ubuntu on and thought I would switch back if I got into trouble.  After about a month I decided that was a waste of a good drive and I wiped it.

If you want to become good at Ubuntu and Linux.  Use it and leave the MS crap alone.  Linux will boot from just about anywhere.  Get and external and put Mandriva (the only non-debian based OS I really like) on it.

You will find that Ubuntu is great.  9.10 is a little rough.  I am sure that 10.04 will be pretty smooth from the day of release.

To some up my experience, great.  Problems - yes.  But you can fix them.  Try that with Win JerryLewis Pro.  MS was trying to give me a stroke (I do not have blood pressure problems but that bugger main veins stick out).  Ubuntu and Linux in general is fun, even when it breaks.

---

### Post by 3rdalbum on 2009-11-05
> **kixome said:**
> also yes, if not on extremely new HW then ubuntu 8.04 is right for you!

I would disagree and say that you should really be using the latest version wherever possible. And especially not 8.04, it is very outdated.

---

### Post by rich97 on 2009-11-05
> **ranch hand said:**
> Then the trouble started. it was too much fun. I broke the OS (and had no idea how to fix it) 5 times in a week. The wife was a little pissed. Her idea, don't laugh, is that you should be able to USE your computer.

I know what you're talking about, peculiar things women are...:lolflag:

---

### Post by ranch hand on 2009-11-05
> **rich97 said:**
> I know what you're talking about, peculiar things women are...:lolflag:
But, even more FUN than Linux.

---

### Post by Rambar on 2009-11-05
> Is there anyone else who made the switch from Windows Vista to Ubuntu and can share their experiences (good or bad) with me? 			 		

 I switched from Vista and it was quite simple: I made a 20 gb partition for ubuntu and then made a dual boot. The only problem was that I did this with my external HD plugged in, and grub didnt load after reboot.  I removed it and restarted, and problem solved. After getting it running, the experience was very enjoyable. I just grabbed a book (Ubuntu pocket guide, its free) and learnt the essentials in a week. Also, the community is very friendly and helpful, and you can find the answers to most problems/questions here in the forum.

 The only thing I miss about Windows are some specific games (not really a problem). I still use it for university-related work as I haven't finished tweaking my computer for that. If you need specific windows apps for work, you can always use "VirtualBox", and run a Windows virtual machine under Linux. When I get mine working, it will mean a final "bye-bye" to Vista.


 I hope you enjoy learning Linux as much as I'm doing.

---

### Post by Ruiizu1990 on 2009-11-05
> My advice to u to go windows 7, ubuntu doesnt't stand a chance in front of it
Isn't this an Ubuntu forum...or are you being sarcastic? O_o

---

### Post by scouser73 on 2009-11-05
> **Ruiizu1990 said:**
> Hi,
I've been a Windows user for as long as I've been using computers. 
However, for a while now, I've been thinking about switching to Ubuntu. I'm tired of the crashes, and having to fork out stupid money for new versions of Windows. I need to know- Is Ubuntu right for me?
I use my computer for mostly web browsing, music, photos etc, but I also run graphic applications such as Photoshop. 
 
Few questions
1. I'm currently using Vista 64 bit, OEM edition. I want to remove Vista completely, but keep all my programmes, like Firefox, anti-virus etc. Is this possible? I need some advice on how to do this.

2. Does Ubuntu use less RAM and system resources than Vista?

3. Is there anything else I need to know about Ubuntu before I install it?

Sorry if this is posted in the wrong place- I'm still a noob here.
Thanks for reading
~Ruiizu1990

I would say that Ubuntu is definitely right for you.  

[[COLOR="Red"]**Ubuntu: System Requirements**[/COLOR]]("https://help.ubuntu.com/community/Installation/SystemRequirements")

Firstly Firefox comes preinstalled on Ubuntu so the only thing there would be to back up your bookmarks.

There are many applications for listening to music on Ubuntu, personally my favourite is Songbird.

For managing your photographs then you can use F Spot, which is the default photo manager in Ubuntu.

As for graphics applications in Ubuntu there is Gimp and Inkscape.  I'm sure that there are many others also.

For antivirus, you won't necessarily need a program as viruses for Linux are practically unheard of. [[COLOR="Red"]**Ubuntu Antivirus**[/COLOR]]("https://help.ubuntu.com/community/Antivirus")

If you need more help, then please visit the forums as many former Windows users will have asked the same questions that you are pondering over.

Good luck,

scouser73

---

### Post by dchurch24 on 2009-11-05
> **ranch hand said:**
> Linux has its own programs that will not run on MS.

From my experience with 64 bit Vista - so have Microsoft!

Seriously though, people have mentioned the Gimp in place of Photoshop. Photoshop was my only concern when moving to Linux from Windows.

I would now (3.5 years later) say that the Gimp IS as powerful, if not more so than Photoshop. It takes some getting used to when coming from Photoshop, but once used to it, you'll find ways of doing things that you used to do in PS, much quicker.

Now, I think that if there were no Gimp for Windows, I would have trouble going back to Windows simply because of the Gimp (and many, many, many other things).

There is also a plugin (?) called Gimpshop that gives you the 'look and feel' of Photoshop - I tried using this, but then decided to get used to the gimp as it was out of the box.

As for Video editing, I recommend OpenShot - it's the closest I've found to Premier or Vegas - it's not quite in the same league - YET! but it's getting there, and it's simple to use and powerful.

---

### Post by phillw on 2009-11-05
> 1. I'm currently using Vista 64 bit, OEM edition. I want to remove Vista completely, but keep all my programmes, like Firefox, anti-virus etc. Is this possible? I need some advice on how to do this.

Firefox can happily export all saved passwords & bookmarks from M$ into ubuntu (or from any other system, into any system)

[http://www.vpolink.com/showthread.php?t=537](http://www.vpolink.com/showthread.php?t=537)  may help you.

Bookmarks are handled by **Bookmarks --> Organise Bookmarks --> Export/Import** 
The password stuff is handled here ---> [https://addons.mozilla.org/en-US/firefox/addon/2848](https://addons.mozilla.org/en-US/firefox/addon/2848)

If you're currently using IE, then do an install of FF in windows and let it import all your stuff from IE

Phill.

---

### Post by phillw on 2009-11-05
> **dchurch24 said:**
> From my experience with 64 bit Vista - so have Microsoft!

Seriously though, people have mentioned the Gimp in place of Photoshop. Photoshop was my only concern when moving to Linux from Windows.

I would now (3.5 years later) say that the Gimp IS as powerful, if not more so than Photoshop. It takes some getting used to when coming from Photoshop, but once used to it, you'll find ways of doing things that you used to do in PS, much quicker.

Now, I think that if there were no Gimp for Windows, I would have trouble going back to Windows simply because of the Gimp (and many, many, many other things).

There is also a plugin (?) called Gimpshop that gives you the 'look and feel' of Photoshop - I tried using this, but then decided to get used to the gimp as it was out of the box.

As for Video editing, I recommend OpenShot - it's the closest I've found to Premier or Vegas - it's not quite in the same league - YET! but it's getting there, and it's simple to use and powerful.


---> Makes a note to add dchurch to buddies list for questions on GIMP  ):P

Phill.:popcorn:

---

### Post by P4man on 2009-11-05
> **phillw said:**
> Firefox can happily export all saved passwords & bookmarks from M$ into ubuntu (or from any other system, into any system)


An easier solution perhaps is installing the [xmarks]("http://www.xmarks.com/") plugin which will synch bookmarks and passwords for all your browsers (IE, FF, Chrome, Safari. Just no opera yet) on all your OS's. Its a great little tool if you dont mind putting that stuff in the cloud.

---

### Post by phillw on 2009-11-05
> **P4man said:**
> An easier solution perhaps is installing the [xmarks]("http://www.xmarks.com/") plugin which will synch bookmarks and passwords for all your browsers (IE, FF, Chrome, Safari. Just no opera yet) on all your OS's. Its a great little tool if you dont mind putting that stuff in the cloud.


KEWL !!!, although, I prefer to wear mine round my neck on my usb stick, along with other backups.

Thanks for that information.

Phill.

---

### Post by PratterFak on 2009-11-05
Skimming the thread, one thing I didn't see mentioned was dual boot. 

After a live-CD taste, I would recommend just installing Ubuntu along side of your Windows. This will give you a fall back for a while. The Ubuntu install CD will let you partition a piece of your drive for use of Ubuntu- you can use as much or as little as you want (I would say 20GB+ if you can spare it- that will give you more play room). It's very easy.

All the other questions seem answered. Good luck and have fun. Ubuntu is awesome!

---

### Post by Ruiizu1990 on 2009-11-05
> If you need more help, then please visit the forums as many former Windows users will have asked the same questions that you are pondering over.

Good luckDefinitely planning to stick around here, thanks! 

> If you're currently using IE, then do an install of FF in windows and let it import all your stuff from IE
I may be a Windows user at the moment, but even I wouldn't use IE *shudders*

> Seriously though, people have mentioned the Gimp in place of Photoshop. Photoshop was my only concern when moving to Linux from Windows.

I would now (3.5 years later) say that the Gimp IS as powerful, if not more so than Photoshop. It takes some getting used to when coming from Photoshop, but once used to it, you'll find ways of doing things that you used to do in PS, much quicker.

Now, I think that if there were no Gimp for Windows, I would have trouble going back to Windows simply because of the Gimp (and many, many, many other things).

There is also a plugin (?) called Gimpshop that gives you the 'look and feel' of Photoshop - I tried using this, but then decided to get used to the gimp as it was out of the box.

As for Video editing, I recommend OpenShot - it's the closest I've found to Premier or Vegas - it's not quite in the same league - YET! but it's getting there, and it's simple to use and powerful
I've used the Gimp before, I've no complaints with it. I don't even have the latest version of Photoshop (CS3) I still use Photoshop 7. Is the Gimp more powerful than 7, would you say? I was thinking about using Xara or Krita for image editing, since drawing on the computer is very important to me.

---

### Post by phillw on 2009-11-05
> **PratterFak said:**
> Skimming the thread, one thing I didn't see mentioned was dual boot. 

After a live-CD taste, I would recommend just installing Ubuntu along side of your Windows. This will give you a fall back for a while. The Ubuntu install CD will let you partition a piece of your drive for use of Ubuntu- you can use as much or as little as you want (I would say 20GB+ if you can spare it- that will give you more play room). It's very easy.

All the other questions seem answered. Good luck and have fun. Ubuntu is awesome!


I won't keep pointing people to my blog .... But.... It does cover stuff about backing up, dual boot, usb boot ... all the things that have happened since just before 9.10 went live, following how I got on. I hope people find it informative

Phill.

---

### Post by phillw on 2009-11-05
> **Ruiizu1990 said:**
> Definitely planning to stick around here, thanks! 


I may be a Windows user at the moment, but even I wouldn't use IE *shudders*


The parcel carrier's web-site for on-line processing of parcels that my Dad's company uses can only accept IE ... It is a BIG bone of contention as I really do NOT like having the works machine on IE. Said machine takes a while to boot, because I've put on multiple layers of safety on it.

The good news ? ... They're going to support FF in the near future - That'll be good, they are part of Royal Mail, the UK's postal service, so it will give FF another foot-hold in businesses :p

Phill.

---

### Post by QIII on 2009-11-05
> **Ruiizu1990 said:**
> Isn't this an Ubuntu forum...or are you being sarcastic? O_o

Check out his other posts.  If you are able to read the broken English, you will discern a troll with a tackle box full of flame bait.

Don't feed him.

From a purely OS perspective, the question of whether or not Windows 7 is better than Karmic is not worth debating.  What matters is what works best for any particular user.

Now, the business practices of those who make the various OSs...

---

### Post by Ruiizu1990 on 2009-11-07
Got another question, this one for you dual-booters out there-
My hard drive which contains the Windows partition is pretty full. I'm going to buy another SATA hard drive soon, is it possible to install Ubuntu on this separate drive?

Thanks!

---

### Post by phillw on 2009-11-07
> **Ruiizu1990 said:**
> Got another question, this one for you dual-booters out there-
My hard drive which contains the Windows partition is pretty full. I'm going to buy another SATA hard drive soon, is it possible to install Ubuntu on this separate drive?

Thanks!


head over this way -->>  [http://www.linuxquestions.org/questions/linux-newbie-8/how-to-install-ubuntu-on-second-sata-hard-drive-656268/](http://www.linuxquestions.org/questions/linux-newbie-8/how-to-install-ubuntu-on-second-sata-hard-drive-656268/)

Phill.

---

### Post by P4man on 2009-11-07
> **Ruiizu1990 said:**
> Got another question, this one for you dual-booters out there-
My hard drive which contains the Windows partition is pretty full. I'm going to buy another SATA hard drive soon, is it possible to install Ubuntu on this separate drive?

Thanks!

Of course :)

---

