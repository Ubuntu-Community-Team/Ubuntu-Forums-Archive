---
title: "Dapper Mouse/KVM Issues"
date: 2006-06-02
forum: General Help
---

### Post by flatline on 2006-06-02
Ok, so I just posted this in the beginners forum, but I thought this might actually be the better location for my plea.  First off let me say that I am pleased with Dapper thus far, but if I don't find a solution to this problem soon I may kill my computer.  Here is my problem:

It started with Breezy, and I was hoping doing a dist-upgrade to Dapper would fix it... but no dice.  I have scoured the forums for a solution, and there are many, many posts on this topic. But none of them are concise or helpful. Most are like "Well, my KVM works. So bollocks to yours."

Can an experienced Ubuntite give me an answer to this? I saw several posts that were [Locked] from development, so I couldn't find out the latest status. Is this something that is not going to work? I have this KVM and I'm not exactly thrilled over the prospect of having to drop $50-60 for a new one.

I've checked these posts (and others) and tried and nothing has worked:
[http://www.ubuntuforums.org/showthread.php?t=6550&highlight=mouse+kvm](http://www.ubuntuforums.org/showthread.php?t=6550&highlight=mouse+kvm)
[http://ubuntuforums.org/showthread.php?t=142092&highlight=KVM+mouse](http://ubuntuforums.org/showthread.php?t=142092&highlight=KVM+mouse)
[http://ubuntuforums.org/showthread.php?t=156183&highlight=KVM+mouse](http://ubuntuforums.org/showthread.php?t=156183&highlight=KVM+mouse)
[http://www.ubuntuforums.org/showthread.php?t=28643&highlight=kvm](http://www.ubuntuforums.org/showthread.php?t=28643&highlight=kvm)

This isn't a world-shattering problem, but the frustration it causes is ridiculous and seems so unnecessary. At this point, I am losing my mind - I would be willing to put a bounty up for a solution.




Here is my original post:

Ok, so I just installed Breezy **(Dapper now)**. First-time with Linux. I tried searching the forums, but everything seems to be referring to Hoary or Warty, and the fixes listed did not work for me. Here is my issue:

[LIST]
[*]I just got the new 2-port PS/2 KVM "Flip" from Belkin. If it matters, one end is my girlfriend's XP box, the other is my Ubuntu box.
[*]I'm using the USB mouse that came with the XP box with a USB-to-PS/2 converter.
[*]Whenever I switch to Ubuntu, the pointer goes bananas, randomly moving and clicking all the buttons whenever I move the mouse at all. If I unplug the mouse and plug it back into the KVM switch, after a second it recognizes it and all is well until the next time I try to switch.
[/LIST]


Searching the forums, I tried a fix from 4.10, by adding a file to /etc/modprobe.d that included the line: "**options psmouse proto=imps**".

Another thread in the forums from 5.04 suggested I modify /etc/modules to include the line "**psmouse proto=exps**".

Neither of these solutions fixed my problem. I understand this may be a kernel thing, or it may be an issue with using the USB-to-PS/2 mouse in a KVM switch. Whatever it is, it's driving me up a wall. Does anyone out there have any prognosis on this? Will getting a USB keyboard and a USB KVM switch save me?

Thanks in advance,

Matt

---

### Post by dglock on 2006-06-02
Belkin is known for having problems with a usb mouse, have you tried a regular ps2 mouse? 

 I am using a belkin kvm but not with a usb mouse  or keyboard. 

  I also use a miniview kvm that does support wireless usb mouse and keyboard as well as having sound jacks.

  You may have to go back to a ps2 mouse or get a better switch.

don

---

### Post by Geekboy on 2006-06-03
It really seems like Ubuntu does not like PS/2 KVMs.  I have an 8 port and always had problems with Ubuntu.

I also had the problem with the USB to PS/2 converter.  It just would not work for me.

 So I broke down and bought an optical PS/2 mouse at Target for aound $10.  I also had to add "psmouse proto=exps" to my /etc/modules for it to work.  Once I did that everything was fine.  If you have an old PS/2 mouse try that.

My last problem is that the mouse won't work if I boot up and have my Ubuntu PC selected on my KVM.  I have to leave my KVM switched on another PC and wait till I get to Ubuntu's logon screen.  Then I can switch over and everything works fine.  I suspect that this is a problem with Ubuntu and a PS/2 optical as I do not have this issue with a standard PS/2 mouse.

---

### Post by Peepsalot on 2006-06-12
I have a KVM problem with my logitech mx3100 wireless keyboard/mouse combo.  

The mouse does not go completely crazy, but I lose functionality of my mousewheel after a switch, and so far I don't know a way to bring it back without rebooting.

I tried the "psmouse proto=exps" solution to no avail

---

### Post by bearberg on 2006-06-18
[QUOTE=Geekboy]It really seems like Ubuntu does not like PS/2 KVMs.  I have an 8 port and always had problems with Ubuntu.

I also had the problem with the USB to PS/2 converter.  It just would not work for me.

 So I broke down and bought an optical PS/2 mouse at Target for aound $10.  I also had to add "psmouse proto=exps" to my /etc/modules for it to work.  Once I did that everything was fine.  If you have an old PS/2 mouse try that.

My last problem is that the mouse won't work if I boot up and have my Ubuntu PC selected on my KVM.  I have to leave my KVM switched on another PC and wait till I get to Ubuntu's logon screen.  Then I can switch over and everything works fine.  I suspect that this is a problem with Ubuntu and a PS/2 optical as I do not have this issue with a standard PS/2 mouse.[/QUOTE]

Being a complete rookie to Linux in general (note join date), could you tell me where to find the /etc/modules, and anything else relevant to adding that value?

Thanks!

---

### Post by nix4me on 2006-06-18
I have alot of experience in this topic.  I have 2 kvms (Belkin and GWC) that have this problem.  There is 1000's of posts on the web about kvms and linux.  Linux blames the kvms and the kvms blame linux.

The only solution I have found is to buy the I/OGear kvms.  I have had one now for 2 years and it has worked flawlessly.

I know this is not what you want to hear, but its the only solution that has worked for me.

nix4me

---

### Post by Peepsalot on 2006-06-18
[QUOTE=bearberg]Being a complete rookie to Linux in general (note join date), could you tell me where to find the /etc/modules, and anything else relevant to adding that value?

Thanks![/QUOTE]
/etc/modules is a file path.
In linux "/" is the root of your file system.  
so /etc is a directory(or folder if you prefer) at the root of your filesystem, and modules is a text file inside that directory.  It can be confusing sometimes to a newbie since text files in linux rarely use a file extension such as ".txt", ".cfg", or ".ini" that you would normally find in windows.

So... you'll need to open /etc/modules in a text editor, and paste that line into it.

This file has special permissions set on it to help avoid accidental editing of it.  So you will have to edit this file as a superuser (one that has administrative permissions)
From gnome, run the following command ```
gksudo gedit /etc/modules
```
*gksudo* tells Linux to run the following command as a superuser.  It will ask for your password.  *gedit* is the gnome text editor, and */etc/modules* tells gedit which file to open.  Paste the line of code in to gedit and save the file.

If that solution works for you, then congratulations.  Unfortunately it did not work for me when I tried it.

---

### Post by Peepsalot on 2006-06-30
I just want to know, is there anything that can be done to "reset" the mouse, short of restarting the whole system([which by the way, doesn't work in linux either](http://www.ubuntuforums.org/showthread.php?t=188376)).  Is there some script that can be made I can make, a process to restart, anything?

As much as I want to like Ubuntu, it has been making me miserable.

---

### Post by jp-newtolinux on 2006-06-30
Another Belkin KVM owner here.
All is well if I boot to ubuntu.  Upon first switch...no more KVM

Linux can offer access to Windows files, MP3s, RA files and Flash files but somehow a KVM fix is beyond grasp?

...Still an advocate.

---

### Post by nix4me on 2006-07-01
Again, all kvms are not the same.  Your only choice is to go buy a kvm that is compatible.

I had the same problems several years ago.  My i have 2 kvms in a box that never worked correctly.

My IOGear kvm has been working for several years with no problems.

I know you don't want to hear that, but its the only solution that I am aware of.

nix4me

---

### Post by Peepsalot on 2006-07-01
OK I give in.  Which exact model do you have, nix4me?  Please tell me it doesn't cost $200

---

### Post by nix4me on 2006-07-01
I have probably one of the cheapest 2 port kvms made.  Its an IOGear gcs62.  Its a little yellow guy with integrated cables.

The 2 kvms that I have which dont work are a Belkin and a GWC, of course I haven't tried them in at least 3 years.

nix4me

---

### Post by Peepsalot on 2006-07-02
Went to Fry's Electronics, found that exact model, and picked it up for 29.99.  My mousewheel is back baby!  Thanks for the help.

Also, this is a bit unrelated, but I found a nice way to setup the sound(since this switch does not have audio inputs/outputs) is to have the line-out of one computer connect to the line-in of a "master" computer, and the speakers connect to the line-out of that same master computer.  So you can hear sounds from either computer at the same time.  The only drawback is that the master computer has to be on in order to hear any sound.

---

### Post by mdhankins on 2006-07-20
I am having this exact same problem on a Shuttle SB83G5 (p4-3.4ghz, Intel 915 chipset).  Strangely enough, both OpenSuse 10.1 and Fedora FC5 are able to handle the KVM fine.  The mouse will freak out for a second and then recover.  

If Suse and Fedora can handle the Belkin KVM, why can't Ubuntu????    Any help the community can provide on this would be very much appreciated.  

Thanks,

MH

---

### Post by j_alapeno on 2006-08-03
Have to say this whole Belkin and Linux don't mix line of argument smacks of magic and voodoo.  

My Belkin OmniPort has worked fine with Windows 98/ME(yeah well not much else worked ;) )/2000/XP, and Red Hat 7/8/9.

I see other users posting that Belkin KVMs work with Fedora and Suse (or at least were made to work after a /etc/modprobe.d or /etc/modlues edit).

I've tried the edits, they don't work.

The modprobe -r/-a psmouse tricks do work, but it takes a while to open a terminal session when the mouse has a fit of the heebeegeebees ;) 

Has anyone got their Belkin KVM to work ?

Please don't tell me to buy a different brand, that doesn't really help. Thanks

---

### Post by j_alapeno on 2006-08-03
:mrgreen: Dapper & Belkin OmniPort KVM working fine & dandy !!!!!

I Googled around other Debian/Belkin KVM entries on other forums/blogs.

What appears to fix it.

Edit /etc/modules 

ensure it has the following:

```

mousedev
psmouse proto=**PS/2**

```

Edit /etc/modprobe.d/options

ensure it hase the following:

```

options psmouse proto=**PS/2**

```

Don't know if both are really necessary but I'm not changing anything now ! :-D

EDIT: couple of hours / reboots and it's fine.  Mousewheel doesn't work, but then I never use it anyway ;)

---

### Post by Delerious on 2006-08-03
Thanks a ton for this info j_alapeno :P I just started using ubuntu on my work machine and am also going to use it on a box with remote capablities at home. I use a KVM on my workstation here at work on a belkin and had the problems with the mouse going spastic, this fixed it though :P ty again.

---

### Post by j_alapeno on 2006-08-04
De nada ;)

---

### Post by robos on 2006-08-05
Hi
Maybe try this on the linux command line. When the system starts, press "Esc" to enter the grub screen. There go to the entry of ubuntu and press "e" there. Go to the kernel line and press "e" again. Now, move to the end of the whole line and add this at the end:
i8042.nomux=yes
press "Enter" to add this to the line and press "b" now to boot the new kernel "construct" :) (This is all temporary, next reboot will be like before)
This might help.
Cheers
Robos

---

