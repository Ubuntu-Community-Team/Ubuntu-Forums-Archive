---
title: "Many issues"
date: 2011-02-01
forum: General Help
---

### Post by No1Daemon on 2011-02-01
Hi all

I am new to Ubuntu. I am having many many issues and I think they are due to the version I have. I am using Ubuntu 10.0.4 LTS. Is this a beta version or something? I installed this version because it came as a live cd coupled with emc2 for cnc machining.

I cannot get anything to work correctly.

I tried to install Mozilla thunderbird using the application manager and it is very slow. It takes forever for the menus to open. or emails and is virtually unusable.

I tried to use the startup manager and it killed my grub bootloader so I needed to reinstall.
I couldnt successfully use the grub2 console prompt to log back into linux even though I ollwed several tutorials for this.

I tried to install the flash player plugin and it kept telling me still to install it before I could watch flash videos even though I had installed it 3 or 4 times.

I just tried to install evolution mail and it cannot log into my gmail account.

I tried to install swift dove which is a faster version of thunderbird and it says it is starting but then never does.

I am reasonably sure I should hang in there as I have heard Ubuntu is very good as an os.

Someone please tell me these things aren't standard for Ubuntu and perhaps I have a dodgy install or something.

I have loaded all the updates or it from the update manager, what else can I try?
I do not expect anyone to answr all these issues, however I do require email so I would like to sort that one out first.

Thanks
Steve

---

### Post by Moloch85 on 2011-02-01
Normally Ubuntu is a really fast and stable system, maybe you downloaded the wrong Ubuntu version or maybe you have quite a old hardware or some incompatibility, anyway we need some additional information to guess what kind of problems you have.

A good starting point is doing a system test. You can find it following System -> Administration -> System Test

To answer your first question: LTS stands for "Long Time Support", which means that the 10.04 repositories will be active for 3 years, from april 2010 to april 2013.

I hope you'll solve your problems with ubuntu soon.

---

### Post by No1Daemon on 2011-02-02
Hi Moloch85

Thanks for the quick reply.

I did the system testing and all came back okay. I am using an older laptop, an IBM R50 but it seems to be up to the job.
I did have one hangup when it was testing screen cycles but everything else went fine.

You don't want me to paste the system report between code tags do you?

Thanks for your time
Steve

---

### Post by inso_741 on 2011-02-02
Stick to one email client for now and give details like how you set it up and what exactly is not working

---

### Post by No1Daemon on 2011-02-02
Okay

The one with the most problems is Thunderbird.

I set it up by selecting it from the software center.

I chose all the defaults and I set up one account which was a gmail one that is synchronized to my 2 local ones so I can transfer all my details and contacts etc. I chose all the defaults for setting that up which from memory was imap instead of pop.

The settings do work because it retrieves emails but it takes well over a minute to display each message as they are clicked on.

Steve

---

### Post by Don Barzini on 2011-02-02
> **No1Daemon said:**
> I am using an older laptop, an IBM R50 but it seems to be up to the job.

That laptop is about 7 years old I think. It probably also has 512 MB of RAM. Is that correct?

If so, a machine like that wouldn't be all that "peppy" with the GNOME version of Ubuntu. Some of the slowdown might be because the operating system could be doing a lot of swapping.

In a terminal window type the command **Free** and post the output.

You might also consider using a lighter desktop release like Lubuntu.

---

### Post by No1Daemon on 2011-02-02
> **Don Barzini said:**
>  It probably also has 512 MB of RAM. Is that correct?


It has been upgraded to 1.2gb
> 

In a terminal window type the command **Free** and post the output.

            total       used       free     shared    buffers     cached
Mem:       1284864     552104     732760          0      33956     215648
-/+ buffers/cache:     302500     982364
Swap:       977528          0     977528

---

### Post by Don Barzini on 2011-02-02
Your memory situation doesn't seem to be the problem. It hasn't even touched swap.

I can tell you it is not the fault of 10.04 LTS. That's what I use and very rarely if ever have any problems.

Are local applications as problematic and slow as network related stuff?

---

### Post by No1Daemon on 2011-02-02
Mozilla runs fine, a little slow at times but mostly fast as you would expect.
The other day I  tried to install seamonkey(whatever that is) and it behaved the same as TB.

I found while googling some threads where people seem to be having this same issue and it is possibly the sotware searching for plugins each time it starts which causes the lag in the messages.

The solutions suggested just says plugin.scan.plid.all = false but I do not know how to change this. I have gone into the settings(about:blank) the same as you have in mozilla but this setting is not in there.

May be a red herring but this does seem to be an issue for other users as well.

---

### Post by Don Barzini on 2011-02-02
> **No1Daemon said:**
> The solutions suggested just says plugin.scan.plid.all = false but I do not know how to change this. I have gone into the settings(about:blank) the same as you have in mozilla but this setting is not in there.

May be a red herring but this does seem to be an issue for other users as well.

I also use Thunderbird to pull mail down from a POP server. It works fine... but I don't use any plugins with it.

Have you tried renaming your **.thunderbird** folder in your home directory ... then running Thunderbird and setting up the account again?

---

### Post by JOHNNYG713 on 2011-02-02
> **No1Daemon said:**
> Hi all

I am new to Ubuntu. I am having many many issues and I think they are due to the version I have. I am using Ubuntu 10.0.4 LTS. Is this a beta version or something? I installed this version because it came as a live cd coupled with **emc2 for cnc machining.**


 I might ask where did you get your ISO from ?? I have never seen buntu coupled with anything !! BUT If you need this program I am sure it is available in synaptic !, I would just install Ubuntu and add That app ! 10.04 LTS is one of the BEST most stable releases in a LONG time ! and very reliable !  In the past I have found, that if something doesnt work right, a reinstall of another burn usually takes care of it ! cdimage has the most reliable and up to date ISO's Ubuntu is FAR superior to windows and I am no "FanBoy" It is just plane fact !  I hope you get your issues worked out and continue to enjoy Ubuntu !! ):P

---

### Post by No1Daemon on 2011-02-02
> **Don Barzini said:**
> 
Have you tried renaming your **.thunderbird** folder in your home directory ... then running Thunderbird and setting up the account again?
I dont seem to have one. Its not in the home directory and I did a file search and couldn't find it either.
Perhaps the next reply may have some merit, I could get another iso and try a reinstall without the cnc software?

---

### Post by No1Daemon on 2011-02-02
> **JOHNNYG713 said:**
> I might ask where did you get your ISO from ?? I have never seen buntu coupled with anything !!):P
I got it from this link [http://linuxcnc.org/](http://linuxcnc.org/) second down on the left hand side.

I just assumed it was the same ubuntu 10.0.4 as would be available from other sources. Perhaps not

---

### Post by piquat on 2011-02-02
> **No1Daemon said:**
> It has been upgraded to 1.2gb
            

It had 2 256M modules and you pulled one and stuck in a 1GB.  Am I right?  I've got a T41, pretty close to the same specs, though a little bit worse, IIRC.  Same memory situation.  Mine does OK with Ubuntu.  I don't think this is hardware, unless you've got a broken piece of it....

---

### Post by Don Barzini on 2011-02-02
If you are using Mozilla Thunderbird and do not have a **.thunderbird** folder in your home directory.... that most certainly IS a problem.

---

### Post by No1Daemon on 2011-02-02
> **piquat said:**
> It had 2 256M modules and you pulled one and stuck in a 1GB. 
Correct.  I dont think it is hardware related at all. Nasa use these for a good reason I am sure.

---

### Post by No1Daemon on 2011-02-02
> **Don Barzini said:**
> If you are using Mozilla Thunderbird and do not have a **.thunderbird** folder in your home directory.... that most certainly IS a problem.
Nothing is as it should be with this install! Unless I have more than one home directory or it is hidden?

---

### Post by Moloch85 on 2011-02-02
It seems that you installed a customized Ubuntu system, i suggest you to try also to get support from the [http://www.linuxcnc.org/](http://www.linuxcnc.org/) forum, maybe some users have experienced problems similar to yours with this particular distribution.

---

### Post by Topsiho on 2011-02-02
I don't know why you are trying a version of Ubuntu that has been tampered with by a third party. It doesn't make any sense. You never know what that third party has done to it, even with the best of intentions.

If you want to give Ubuntu an honest try, you should download it from Ubuntu itself, or from a mirror, and check out the checksum. Please download the correct version, and burn it as an image, at slow speed if that is possible.

Ubuntu 10.04.1 (and NOT 10.0.4 or such thing) is, as someone said already, a really good version of Ubuntu, as it should be, as it's an enterprise version (LTS).

How good is the memory in your system. If you have problems with (the original) Ubuntu, then it is almost certainly hardware related. How is the "health" of your hard disk?

Another thing is that laptops give the most trouble, as the hardware often has been customized, which means: altered (for a certain version of Windows), and so Linux is not running well on it. That said, I have installed Ubuntu and other distro's without trouble on many laptops.


Topsiho

---

### Post by JKyleOKC on 2011-02-02
> **No1Daemon said:**
> Nothing is as it should be with this install! Unless I have more than one home directory or it is hidden?Yes, it IS hidden. In Linux systems, the leading "." on a filename hides the file. To view all hidden files at a command line prompt, type "ls -a" and to see them from the usual file manager window, click CTRL-H. You'll find that your home directory contains several dozen similar hidden files, most of which contain configuration data for various programs.

---

### Post by No1Daemon on 2011-02-02
> **Topsiho said:**
> I don't know why you are trying a version of Ubuntu that has been tampered with by a third party. 
It had little to do with not trying to give Ubuntu a decent try. I simply wanted to use linux cnc software because I heard it was powerful and found a distro with it included which happened to be Ubuntu 10.0.4.

To be honest there are so many Linux distros its hard to know where to start.

I am however downloading the recommended image and I will then install emc2 afterwards.
Will it install fine in a dual boot mode like this one did as a straight replacement?

Rhanks

---

### Post by No1Daemon on 2011-02-02
Hi again

I have downloaded and reinstalled the ubuntu 10.04 release from cdimage as recommended. The install went fine and I was able to reboot and the bootloader worked perfectly. I have not gotten to test thunderbird etc yet though as I followed the instructions on the EMC2 website to download and install the dependency packages etc for EMC2 and after the install finished and I rebooted it came up to a grub prompt like this grub>

Can someone explain to me simply how to recover the bootloader from here please.
I should point out I have tried to do stuff from the grub prompt. I tried using find /boot/grub and it said unknown command 'find'

I also tried following some instructions to boot into linux by going root (hd0,6) and then kernel /boot/vmlin etc etc but it returned kernel no such command.

So am I missing commands? or does it just return that when you do not enter it correctly?

---

### Post by No1Daemon on 2011-02-03
Okay. I have managed to solve my own install problem with emc2

I now have it installed and the dual boot manager working properly.(grub sucks)

Back to the original issue with Mozilla Thunderbird.
It is still slow and laggy. I have disabled global indexing in advanced options as suggested in one post and rebooted but that didn't solve the issue unfortunately.

Any other suggestions please?

Thanks
Steve

---

