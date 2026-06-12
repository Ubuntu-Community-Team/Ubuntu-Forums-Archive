---
title: "NVIDIA drivers kill graphical interface?"
date: 2010-08-22
forum: General Help
---

### Post by captainjamestcake on 2010-08-22
Hi all, can I say what a lovely forum you have here.

I'm quite new to ubuntu and I don't speak the language yet (sorry), I'm also new to this forum, is it okay to just post a request for help?  Normally I can find all the info I need with a google search but I don't even know where to start with this one.

I seem to have killed the entire installation and I'm not sure what to do.  I'm not even sure what information to provide.

I'm running 10.4 LTS on a pretty standard laptop, 
i3-330M CPU, 
nvidia geforce GT 325M (I mention this because I think it's part of the problem).
I just re-installed clean from the live CD (I also have a windows partition), everything worked fine.  Then I downloaded and installed all updates the system suggested and I also used the proprietary drivers gizmo to DL and activate the nvidia package.  When I restarted the system the OS would not start, recovery mode will not start either.  

I get my grub screen as usual, select Ubuntu, it moves to a blank screen with blinking curser as usual, then goes completely grey and appears to hang.

I think the graphical interface is not initialising.  I'm assuming it's either a problem with the nvidia driver directly or the nvidia driver has done something to xserver that prevents it from starting.

It might also be one of the updates, or I did think perhaps it was just the updates taking effect on restart, I left it hanging on the grey screen for an hour and still nothing, it couldn't take longer than that could it?

I can dismount grub to a command prompt but it doesn't seem to understand normal commands. 

Any help would be very much appreciated, thank you.

---

### Post by captainjamestcake on 2010-08-22
'Ello, new to forum, etc.

Reposting this from half an hour ago, I had no replies, is that okay?  



 

Original post here...

I'm quite new to ubuntu and I don't speak the language yet (sorry), I'm also new to this forum, is it okay to just post a request for help? Normally I can find all the info I need with a google search but I don't even know where to start with this one.

I seem to have killed the entire installation and I'm not sure what to do. I'm not even sure what information to provide.

I'm running 10.4 LTS on a pretty standard laptop, 
i3-330M CPU, 
nvidia geforce GT 325M (I mention this because I think it's part of the problem).
I just re-installed clean from the live CD (I also have a windows partition), everything worked fine. Then I downloaded and installed all updates the system suggested and I also used the proprietary drivers gizmo to DL and activate the nvidia package. When I restarted the system the OS would not start, recovery mode will not start either. 

I get my grub screen as usual, select Ubuntu, it moves to a blank screen with blinking curser as usual, then goes completely grey and appears to hang.

I think the graphical interface is not initialising. I'm assuming it's either a problem with the nvidia driver directly or the nvidia driver has done something to xserver that prevents it from starting.

It might also be one of the updates, or I did think perhaps it was just the updates taking effect on restart, I left it hanging on the grey screen for an hour and still nothing, it couldn't take longer than that could it?

I can dismount grub to a command prompt but it doesn't seem to understand normal commands. 

Any help would be very much appreciated, thank you.

---

### Post by captainjamestcake on 2010-08-22
Okay, I get it now, each new reply bumps the message to the top.  I don't use a lot of forums...
How do I delete this repost?

---

### Post by dougalkerr on 2010-08-22
As you can see it is often pot luck if someone picks up on your post. Sometimes it just gets missed if the forum is very busy.
My own post from earlier has not been answered but, it is not important.

So just to let you know you have been read. I'll come back to you in a mo, just off to put the kettle on.

---

### Post by captainjamestcake on 2010-08-22
Thank you Dougal, you are a gentleman, I might just see what I can find in the kitchen in the interim ;)

---

### Post by Swagman on 2010-08-22
To get back to the standard, but working desktop just run the recovery option in grub.

Sorry, I can't help you further than that

---

### Post by captainjamestcake on 2010-08-22
Thanks, but where is the recovery option in grub?  Do I need to dismount to a command line?  If so what do I type to access recovery?
Sorry, I am new to this.

---

### Post by dougalkerr on 2010-08-22
Just getting some info for you that might hopefully help.

---

### Post by dougalkerr on 2010-08-22
Here is something to look at, copy and paste the URL below into your browser address bar and hit go;

[http://www.linuxquestions.org/questions/slackware-14/nvidia-drivers-causing-x-lockup-297427/](http://www.linuxquestions.org/questions/slackware-14/nvidia-drivers-causing-x-lockup-297427/)

Video drivers and Linux... well they don't always go hand in hand.

NVidia have some help on their website but, the problem sounds like the same old story of manufacturers' drivers not being quite 'Universal' enough.

The latest releases of Linux (Ubuntu in particular) are a lot better for driver compatibility than they have ever been but, as you have found out there are still some problems. Although it seems like the thing to do is to install drivers as they become available, the Linux people will tell you, wait and let the various Linux distro developers produce the drivers via updates in general (not separately as new graphics drivers available).

You need to be able to get back to your desktop by resetting the 'X' system graphics set-up.

I can't remember the command for doing this but, somewhere within the NVidia instructions for installing their drivers for Linux there is mention of what to do to reset the driver for 'X' if the new driver fails.

A simple way yo get round this for me is to reinstall Ubuntu as it doesn't take long and it ensures that the original driver set-up is all okay again.

When you get your system back to normal - don't install any new graphics drivers as they appear until you know how to get your 'X' system back when you need to.

It is something like 'cp xconfig.backup xconfig' typed at the command line but, this is not complete so don't just use this line.

Reinstall Ubuntu first because you need to have a working 'X' system before you have a good backup copy of the 'X' config file to work from.

I'll come back to you again in a few minutes after I have another look around.

---

### Post by techunit on 2010-08-22
I think to avoid problems you should install Ubuntu again.

---

### Post by lykeion on 2010-08-22
> **captainjamestcake said:**
> Thanks, but where is the recovery option in grub?  Do I need to dismount to a command line?  If so what do I type to access recovery?
Sorry, I am new to this.

In the grub menu there should be a line similar to this:

Ubuntu, kernel 2.6.32-24-generic **(recovery mode)**

Use arrow keys to select it, then in recovery menu there should be a line like this:

xfix   Try to fix X server

---

### Post by captainjamestcake on 2010-08-22
Thanks folks,
Ideally I'd like to recover my system because I have an unbelievably slow connection at the mo and it takes me all day to re-install my software.
But I've always liked the clean re-install option.

I think what I need is a method to access a command prompt from grub so I can restart xserver (if this is indeed the problem).

Any ideas...?

Thanks also for the info Dougal, I've had a look through, I think I'll stay away from the NVIDIA instructions, I've been there before with a different system and it's not a happy place.  As you say, it's prob'ly best to re-install and use the linux driver set.

---

### Post by no2498 on 2010-08-22
recovery option

as ubuntu starts up click esc key

that is on some ubuntu not all

some use the  shift esc keys


hope this helps you

---

### Post by captainjamestcake on 2010-08-22
Thanks Lykeion... but see original post, the recovery mode option has the same problem as the normal one.  I thought there might be another... hidden recovery mode us noobs don't know about ;)

---

### Post by captainjamestcake on 2010-08-22
Thanks 2498, I'll just go and try that...

---

### Post by lykeion on 2010-08-22
Do you get the grub menu (like in this pic)?

[http://adamsiembida.com/images/ubuntu/grubmenu/dirtygrub.gif](http://adamsiembida.com/images/ubuntu/grubmenu/dirtygrub.gif)

try select the second choice

---

### Post by captainjamestcake on 2010-08-22
Lykeion, thanks for your help!

I get the grub menu, all seems fine, I can select either normal or recovery mode of either of two kernel versions (10.4.32.21 and 10.4.32.24 I think) but all four options lead to the same problem.  

When I updated, the kernel was also updated (giving me the new 10.4.32.24 options), could that have anything to do with it?

---

### Post by dougalkerr on 2010-08-22
Here we are;

[http://ubuntuforums.org/showthread.php?t=571385](http://ubuntuforums.org/showthread.php?t=571385)

Someone else had the same problem.
You copy the xorg.conf file from the LiveCD by opening gedit text editor.

Best to do this by opening Terminal so you are in command line and type 'sudo gedit...' you will have to put the full path to the file off the LiveCD after 'sudo gedit' then copy all the text and open the xorg.conf file on your hard drive and highlight all text and paste the first lot on top of this. Save the file from your hard drive as the same name and close everything and reboot... fingers crossed.

---

### Post by josend on 2010-08-22
I´ve had the same problem, and havent found a solution yet, if i find one i´ll let u know! and u if u find it first, please let me know! thank u

---

### Post by captainjamestcake on 2010-08-22
Will do!

---

### Post by captainjamestcake on 2010-08-22
Brilliant!  Thanks Dougal, I'll just go and give that a try...

I'll let you know how it goes.

---

### Post by josend on 2010-08-22
and? did u solve the problem?

---

### Post by captainjamestcake on 2010-08-22
No joy.

I replaced the xorg.conf file with one I downloaded, I couldn't find any way to browse the live CD to take the file from there, but I still have the same problem.

So I'm off to re-install...

Thanks everyone for all the help, I've learned some new things, which is always good.

I like it here... I'll be back!

Thanks again!

---

### Post by Sef on 2010-08-22
Merged duplicate threads.

---

### Post by stanley82 on 2011-03-23
copy xorg.conf sounds good but how?  I'm fine till it changes from a primative boot screed VGA then it blows it.  I have the same problem trying to re-install from the live CD/DVD.  I fail to understand that.  In grub c gives me a limited terminal, cd is not found so that's too limited for me.  Selecting a recover from grub again lost after leaving basic vga.  Maybe I should get a new hard drive or did the Nivida 8500gt get any firmware changed?  This forum looks to be a good place for help.  Regards Ian.

---

