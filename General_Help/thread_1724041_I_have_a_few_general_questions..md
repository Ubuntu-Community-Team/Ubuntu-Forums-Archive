---
title: "I have a few general questions."
date: 2011-04-07
forum: General Help
---

### Post by Murdoc419 on 2011-04-07
I have decided to return to Ubuntu after my first (I guess you could say failed) attempt. I am a Computer Science student and I believe Ubuntu is the best environment to practice my skills. I really want to make sure I get everything set up how I would like this time around to avoid getting frustrated and resorting to Windoze. 

Anyway I have partitioned my hard drive through Wubi and installed Ubuntu alongside Windows 7 64 bit. The first problem I am having is that it seems I cannot make the partition for Ubuntu any larger than 10gb. I have a 320gb hard drive so I know there is plenty of space to create a larger partition. Is it something to do with using Wubi? I want to slowly make the transition from Windows to Ubuntu this time and slowly work into the OS until I feel 100% comfortable not having Windows. (Except on my old desktop, just in case) 

Second I was wondering about writing programs in Ubuntu. I just started my first programming class in college. We are learning how to code in C++. The teacher has us using Cygwin and Textpad to compile and write the code, respectively. I'm guessing that Cygwin won't work with Ubuntu but perhaps Textpad would. Or, are there other programs that will work with Ubuntu with similar functionality? Basically as long as I can write, compile, and execute the programs I am good to go. 

For my last question I need to explain what I plan to do during my switch to Ubuntu. Basically I am going to dual boot Windows and Ubuntu, trying different programs that I frequently use on Windows to see if there is a deal breaker somewhere. I don't believe there will be as I mostly use OSS on windows anyway and there is almost always an OSS alternative. But once I feel completely comfortable with Ubuntu I plan on removing the Windows partition. Is there any way for me to erase the Windows partition and then combine it with the Ubuntu partition. That way I do not have to reinstall Ubuntu and any other programs/apps I have installed. 

I appreciate any help with these questions. I must say it feels good to be coming back to Ubuntu!

Edit: Forgot to mention, not sure if it's important, I have tried to use Gparted to increase the size of the partition containing Ubuntu but it will not allow me to increase it's size beyond 10gb.

---

### Post by Murdoc419 on 2011-04-07
Bump

---

### Post by 1clue on 2011-04-07
Wubi:  Don't know anything about it, or for that matter about dual booting any modern operating system.

Disk:  Make sure your Windows partition is not taking up all but 10G.  10G is plenty for a basic system but if you're going to load it up you'll run out fast.  I would recommend some sort of Windows utility for resizing a windows partition.  Always use a tool for that OS to resize any partition or you'll get something messed up.

You might consider a windows partition, a Linux partition, a swap partition and a common partition to mount on both operating systems.

If your teacher is using Cygwin then that's basically an API into Linux anyway.  Cygwin is a RedHat product.  What compiler are they using?  If it's gnu then you're going to be in great shape.

Text editor:  Your teacher needs an editor.  You want something with syntax highlighting specific to c++.

There are lots of great programming editors in Linux.  I would recommend you start with Eclipse (which is a whole IDE), jedit, gedit, or any number of other editors out there.

Personally my preference is vim, but that has a really steep learning curve.  So does emacs, which is another great programming editor.  I've been using vi or vim for almost 20 years now, and if you know how to work it there aren't a lot of things a full-blown IDE gets you that can't be done in vim.  Same with emacs, but don't let this thread turn into a war between vim and emacs, the Internet is about half vim/emacs wars by volume of text.

Eclipse is a popular IDE on Windows, Mac, Linux and just about anything else too.  It runs in Java.

Seriously, if you absolutely positively need some sort of software that needs to be bullet proof, consider either having a VMware with Windows on it (can't use your OEM windows) or try wine, or try Crossover Office which is a commercially supported Wine by the same guys who make the free version.  If you're not specifically taking a class that requires obscure features of Microsoft software you are probably fine.

---

### Post by nerdy_kid on 2011-04-07
I don't think the admins like it if you bump your thread more often then once every 24 hours.


I really wouldn't recommend Wubi as anything permanent.  For one, I dont think you can easily resize the wubi partition (you _can_ do it, its just going to be a pain and I don't know how off the top of my head).  Also, the NTFS drivers that wubi uses to run gobble up a lot of CPU.  I would do a real dual boot, the install is really easy and straight forward.


You don't need cygwin, all the code that compiles on cygwin will compile natively on Ubuntu afaik.


As long as you doing a true dual boot of Windows+Ubuntu, erasing Windows should be as easy as popping a LiveCD/LiveUSB into the pc, deleting the windows partition and resizing the Ubuntu one.

Gparted won't let you resize your wubi partition past 10GBs cause the whole filesystem is a file on your Windows drive.  Once you set the size when you installed Ubuntu via wubi you can't easily resize it.

---

### Post by Murdoc419 on 2011-04-07
First sorry about the bump. I was getting desperate. 

To 1clue: 
Not sure if I followed you right on this so without saying anything to look ignorant I will just say that when we installed Cygwin she had us also include the g++ packages and optionally the emacs and xemacs packages. (I believe those are the correct names). I will give Eclipse a try, right now we are just compiling g++. Simple programs like the starter HelloWorld program, etc. I doubt that we need any programs that require features of Microsoft. Some kids in my class are doing everything on their Macs so I believe I should be fine with Ubuntu. Now VMware, is that like a virtual box? I will give that a try if all else fails. But from your description I think Eclipse will work out for me. Thanks

To nerdy_kid:
I will try a true Dual boot, especially considering I'm not sure if I am ready to completely get rid of Windows as much as I would like to. I can set up a dual boot by mounting the iso image to a usb flash drive and booting from it correct? When I boot from the flash drive will it give me the option to erase the current partition I have for Ubuntu or will I have to do that beforehand? If so how do I do that. I am still a bit of a noob when it comes to some of the more technical stuff. 

By the way I actually tried to download the iso image of Ubuntu and install it that way but my download stalled with 0 seconds remaining and never finished. I was using Google Chrome, was that my problem or something else? I will try to download it using Firefox this time though. Thanks for the help and any more help is still greatly appreciated.

---

### Post by irv on 2011-04-07
First you need to do this right. I have been using Win7 and Ubuntu 10.10 since they both came out. I heard about Wubi, so I tried it and it's not what you want. First boot with the Ubuntu live CD and install it from the CD. This way you can run it along side Win7. When you go to install it make sure you pick to run along side Win7 and **_do not_** use the whole drive or you will loose you Windows. Ubuntu will pick the size it needs and leave enough drive space for Windows. As time go on you can use gparted from Ubuntu to delete the Windows partition and expand the partition on Ubuntu. You can not do this in Wubi.
Before you do anything make a backup of all your data and important files in case something goes wrong.
That takes care of your first question. I will leave the others to someone else.

---

### Post by nerdy_kid on 2011-04-07
for the usb question:  Ubuntu comes with this nice little app called "startup disc creator". All you have to do is download the .iso, pop the flash drive in and start up this app.  It will install Ubuntu to the flash drive, then you reboot and select usb device from your boot menu.  When you are installing Ubuntu, just select "install side by side with Windows".  It will give you a slider to drag that will tell it how much space to give Ubuntu.  I'd say give it at least 20GBs.

To erase the Wubi "partition":  just go to add remove programs in Windows and uninstall Ubuntu.  Do this after the above step.

I would just give the .iso another try.

Yeah, afaik all you will need to do to compile your apps is boot up Ubuntu and open a terminal.  Everything should already be installed.  gcc and g++ are installed by default.  The commands that your friends are using to compile the apps on their macs should work as well on Ubuntu.

If you are writing really simple apps, I would recommend Kate from the software repos (type "sudo apt-get install kate" from terminal without quotes to install it).  It is a very nice text editing app with syntax highlighting for a whole bunch of languages, C/C++ included.  It has integrated terminal also.  Its a pretty simple app, unlike IDEs.

VMWare is basically VirtualBox, for most extents and purposes.  I would grab VirtualBox though ([http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)) but that is my opinion.

---

### Post by 1clue on 2011-04-07
Your teacher needs a really good apple on his/her desk.  You're using open source software, and if you show up with a real Linux laptop you will be ahead of everyone else.  Back when I was in college that just couldn't happen.

Install Ubuntu + the g++ compiler + Eclipse and you're good.  Since your teacher recommends emacs, that is another good thing to try.  In spite of its terminal-based nature, emacs is an extremely powerful text editor designed for programmers and with decades of continuous improvement.  Vim is the same idea with a dramatically different structure.  But if you're a point-and-click person you will probably prefer Eclipse or one of the gui editors.

Installing:

Just for future reference, I HATE dual boot.  I will always slant my recommendations to avoid that if at all possible.  It's technically fine, lots of people do it, but you can never run both operating systems at the same time, and if either system touches the boot block in the wrong way the other OS is smoked.

The thing I call dual boot is two operating systems on the same drive with the same boot loader.  Technically one of my alternatives is also dual boot, but it's only slightly less evil because you still can't use both operating systems.

Dual boot alternatives:

Probably the easiest is to pull the hard disk out of your laptop and slip in another (probably bigger given the way tech and prices works) drive with the same form factor, install Linux on that and go from there.  No matter what, if you mess up your Ubuntu you can either scrape the drive completely without worrying or you can pop in Windows and go from there.  Some Windows laptops facilitate a real fast drive swap, that is a good way to go.

If you buy the second drive as an external, then the other drive can be a usb external drive.

Another alternative is VMware or similar.  VMware is cross platform for the host (the computer running VMware instead of the computer running ON VMware, which is the guest).  You can either get VMware Server for Windows, or for Linux.

In VMware for Windows, you would stop trying to partition your drive.  Get VMware Server for Windows, run it, create a new virtual machine for Ubuntu or Debian and then install Ubuntu on it.  From personal experience if you have enough RAM on your laptop you won't have a problem.  I would call that 3+ G RAM, more is better.

In VMware for Ubuntu, you do it the other way.  You still need lots of RAM, but you install Ubuntu on the entire system and then create a VMware from inside Ubuntu, and install Windows on it.  This will only work if you have a complete, non-OEM version of Windows that did NOT come with the computer.  If you bought Windows separately then you're good.

Now, the deal about VMware (or kvm or virtualbox or whatever) is that whatever your host is, that's what you always have running.  Then you have the other sometimes operating system on the VM.  You can set it up so that the VM comes up when you boot the host operating system, but you don't have to.

The good news is that with a VM, you can run both operating systems simultaneously which is incredibly better than dual boot as long as your system has the nuts for it.

The other good news is that with a VM, if your less-used system is the VM, you can just delete the file or burn it to a backup if you don't want to use it anymore.

---

### Post by Murdoc419 on 2011-04-07
Ok I have installed Ubuntu to my flash drive. Not sure what was up with the download earlier, I just reset my router and modem and it downloaded much quicker as well. I would really love to use Virtual Box instead of doing a dual boot. I have 4GB of RAM on my laptop but I'm not sure how my other hardware is for this. I have an Intel Pentium Dual Core 2.2Ghz processor and just a simple on-board GPU. Not sure if the GPU matters much though. The main problem is that I did not buy Win7 separately, it was pre-installed and didn't even come with disks. All I have to install Windows is a few disks I created with the Sony Vaio Care tools on my laptop. I believe that would wipe the hard drive and install Windows which is obviously not what I want. Though I don't plan on using Windows much at all once I get better acquainted with Ubuntu so I may try to find a cheap copy of XP or something. As  broke college student I simply don't have the money to go buy an OS that I don't plan on using much. 

One question I have regarding that is how it affects the performance of your PC. I enjoy playing online games (well basically just WoW, which seems to run great on Ubuntu) and this option would not be desirable if it hinders my performance.

Also I'm not sure which software I should use for programming. Kate sounds very similar to using Textpad and Cygwin together so I'm leaning towards that. What would be the major differences? Between Kate and Eclipse that is.

Thanks again for all the help. I imagine us ex Windows users must get annoying with all of our questions but it's great there are people here to help us or many windows users would be stuck with that inferior OS.

---

### Post by 1clue on 2011-04-07
I will never get tired of helping programmers or potential programmers install Linux.  Every one of them is a potential coder for open source.  This sort of support that we're giving you is actually a contribution to the open source community.

Google Windows student discount.  Sometimes you can get a Windows version for $30 or so if you're a student.  I'm a developer, so I can get a similar license for testing and development (the only reason I have anything on Windows) for around $30 as well.  Make sure you read the terms of use, they're not that complicated anymore.  If you can live inside those then Microsoft will be happy to deal with you.  With all the hot versions of Windows out there, they are thrilled to give you a legitimate license for a small amount of money instead of not getting anything at all.  If you have to talk to the guy at Microsoft, just flat out tell them it's a VMware or similar, they do not care and it explains why your CPU changes every time you upgrade VMware.

Keep in mind that every actually running VM that you create from that disk is a separate license.  These licenses are cheap, be honest.


Performance:  Normal apps run about the same speed.  Graphics apps run slow, because there is no direct access to the video card.  So running newer games on a VM sucks, but not running them on the bare metal.

The whole point of VMware, the thing that makes it worth trying at all, is that any given computer generally spends most of its time sitting there doing nothing.  This is even more true with workstations than servers.  Chances are, whatever you do on the VM will happen when the main OS is idle and vice versa.  Modern CPUs including yours are designed with hardware features which are meant to work with virtual machines.  There is almost no noticeable delay, and in fact sometimes it seems that Windows apps run faster from a VM than they do on the bare metal, and I can't explain it.

Games:  If your game doesn't work on Ubuntu, look at wine or crossover office.  Crossover basically gives you a license to DLLs that make Windows apps work really well.

Editors:  It sounds like your teacher is trying to expose you to a couple different editors.  Textpad is a generic programming editor.  Works fine, but there are others.  One thing you will do continually as a programmer is download every editor you have ever heard of, and try it out.  Get used to it.  I bet you anything your teacher probably will not care unless it slows you down.

Get the cheat sheet for any editors you download, print them out with the name of the editor on the top of the sheet, and pull that sheet out every time you open the editor.  Learn the hot keys for at least the basic operations, and use them.

---

### Post by Murdoc419 on 2011-04-07
> **1clue said:**
> I will never get tired of helping programmers or potential programmers install Linux.  Every one of them is a potential coder for open source.  This sort of support that we're giving you is actually a contribution to the open source community. 

I never thought of it like that, that is a great point. 

I just checked and I can get a student discount for Windows 7 bringing the price down to $30. So I will most likely be doing that. Would you happen to know if you can download that onto DVDs and use those discs to then install windows in a Virtual Box? As far as my concerns of performance issues, I meant more like will it affect the performance of processes running in Ubuntu while I do not have Windows loaded. I'm not completely sure how a VM works, I am just assuming that Windows would be like any other app on my PC that I could run and close as I need it. So basically could I just have it closed not allowing it to suck up my resources.

As far as the editors, I will install both Kate and Eclipse and play around with them this weekend. Hopefully I'll be somewhat friendly with one or the other by the time I go back to class. Now to further my rep as a noob... these cheat sheets your speaking of is there by chance a domain that would have all of them available? I'm assuming cheat sheet means just a list of all the commands and keyboard shortcuts which may actually be on the developers website. I'm just making a lot of assumptions here aren't I? ;-)

---

### Post by 1clue on 2011-04-07
Windows:
You may be able to get it with a download but you don't want to.  You Want That Disc.  The last time I checked it was like $5 extra.  No book, no box, just a disc.

You will have two strategies which are reasonable if you get the student edition:
[LIST=1]
[*]Make a current backup of your OEM windows which can then be restored when/if you decide to go back or sell the laptop.
[*]Install the student edition Windows right on the hardware if you decide to go back to Windows.  This does not work if you sell it to a non-student.
[/LIST]

VMware:
There are lots of different VMware apps.  Some of them take over your hardware and some of them cost money.  You don't want either of those.  VMware Server is free and it's a service you can start and stop.  It's very low-impact.  You also want VMware Server Console, which is the GUI part of it.  You use that to create new machines, start, stop or alter settings from the host side.

Keep in mind that there may be other virtualization systems that work fine for you too, but they all basically work the same.

As long as you stay away from the systems that take over your entire computer, then they're either an application or a service which runs on your host.  Each VM is in a directory on the host, and it represents the settings, the hard disks and whatever else.  The virtualization software maps the real devices to a virtual device, which is just a map between the guest OS calls and the host OS driver.  Sometimes you assign a specific device to the guest which makes it "busy" for the host, and sometimes the driver shares the device between different guests in some fashion.

So with VMware Server for example, you can shut it down and your computer is literally no different than if you didn't have it.

If you're going to be a programmer in today's world, you WILL learn about virtualization in a big way.  Just as well dive in.  You will also learn testing frameworks and those will be tied to the VMs.

Editors:
Cheat sheets are either available right in the app, or on the web site of the vendor, or on Google.  I have never heard of a single site with all the cheat sheets, and most of them would certainly be outdated if you did find one.

Editor research is now in your job description.  Every programmer needs to do their own research, and from the perspective of the source code usually an editor is an editor is an editor.  It's all about programmer productivity.

---

