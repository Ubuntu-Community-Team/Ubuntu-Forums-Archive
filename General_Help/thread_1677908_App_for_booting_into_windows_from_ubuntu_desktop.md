---
title: "App for booting into windows from ubuntu desktop?"
date: 2011-01-29
forum: General Help
---

### Post by gunnarflax on 2011-01-29
Is there an application for booting into windows with just a click directly from the desktop in ubuntu without having to reboot and make a choice in GRUB? From what I've heard, the laptops from dell that ships with a ubuntu netbook edition has a choice in the power menu for booting into windows. Is there a similar program available to the public? I mean, iReboot does the same for windows so there must be something?

Thank you!

---

### Post by RJ12 on 2011-01-29
You can use the grub-reboot command. If you know what number your windows entry is on your grub list (the numbering starts with 0 though, so 1 is 0, 2 is 1) you can make a little script on your desktop with this in it

```
#!/bin/bash
gksu grub-reboot X 
gksu reboot
```

X is the entry number (remember, starts from 0)

---

### Post by gunnarflax on 2011-01-29
But there is no application that already does that for me? I mean with a nice little button on the menu panel :) Or is it hard to program a button on a panel to run that bash-script?

---

### Post by Darkness Des on 2011-01-29
You can actually right click on the panel, add a launcher, and point it to that BASH script.

---

### Post by mark bower on 2011-01-29
This seems it might be very handy.  On my PC boot I get the following 5 lines:

Ubuntu Linux
Ubuntu (recovery mode)
Mem Test (memtest 86+)
Mem Test (memtest 86+, serial consol 115200)
Windows XP . .

Two questions:
1) Am I correct that "X" in the script would be 4 in my case to boot XP, based on Ubuntu Linux starting at 0 ?
2) How might I and would there be any problem eliminating all but the Ubuntu Linux and Windows XP menu options?

mark bower

---

### Post by JKyleOKC on 2011-01-29
Yes, the number would be 4 if you don't change the grub menu.

It's relatively easy to change the menu, but it can give you real problems if you delete the "recovery" entry from it. Without that entry, if something messes up your configuration so that a normal boot does not work, you would have to load up a LiveCD and go through lots of hoops to get things working again. With the entry, you simply select it and it gives you a menu of the things that will be most likely to fix it.

However cutting out the two "memtest" entries ought not cause you any problem.

You can do this by getting the grub-customizer package (search the forums for "grub-customizer" to find out more about it). Another way involves editing several grub configuration files, but the customizer is much easier to use.

If you do get rid of the memtest entries, the number would change to 2, of course.

---

### Post by mark bower on 2011-01-29
perfect - thank you. not really necessary, but was thinking "cosmetically" would be neater to have fewer entries in the menu.

i will create the script later tonite to try out.  i did the lines individually in the terminal and only got back to the Grub menu.  that is, either the first or second line required my passwd, and after the 2nd line, the system booted to original menu.  appears the lines must be written as a script, cannot be executed line by line in the terminal?

off to dinner -

mark bower

---

### Post by mark bower on 2011-01-29
the script did not work for me.

when executed, it asks for my root passwd in a pop-up.  after making that entry (& return), it reboots to the Grub menu, not Win XP.

is there something missing in the script and how is asking for passwd avoided?

mark bower

---

### Post by JKyleOKC on 2011-01-29
According to the man page for grub-reboot, it just sets the default entry for the next reboot (only). Thus the reboot command would still display the grub menu after the reboot, but the WinXP entry would be highlighted so you only had to hit the Enter key to go into Windows.

If you never want to see the grub menu at all, you could edit the /etc/default/grub file's TIMEOUT value to 0. The system should then boot directly into the default entry without showing the menu. As for having to enter your password when the script runs, you have a couple of options: you could add a line to your /etc/sudoers file to allow your user name to run "reboot" with no password, or you could chmod the reboot program to replace the "x" values with "s" (which makes the file execute with owner permissions for everyone). If you need additional help with these changes just let us know; since you're writing scripts you probably know how to make the changes...

---

### Post by wojox on 2011-01-29
Try this [how-to-reboot-in-windows-from-ubuntu]("http://www.webupd8.org/2010/10/how-to-reboot-in-windows-from-ubuntu.html")

---

### Post by vat with tux on 2011-01-29
i have installed ubuntu 10.04 inside windows using wubi installer. So will this script work for me?

---

### Post by mark bower on 2011-01-30
o.k. i had assumed that i could execute the script, then computer would soft shut down and reboot in XP.  no, from what i now understand, the menu will again be presented, but XP can be set to be the default (one time).  

@ JKyleOKC
i am going to go for your suggestion of setting the permissions to "s", in which case the pop-up will be avoided and move straight to the menu.  haven't ever changed to an "s", only to rw and x.  i'll read a little, and if a problem, i'll be back.  

mark bower

---

### Post by mark bower on 2011-01-30
the best i could do for changing the script file permissions was to get them to -rwsrwsrwx.  using sudo, sudo su, i still could not get the other execute permission to "s", ie, chmod o+s.  when i run the script, it still gives me the pop-up in which i must enter my password.  

maybe a little more help on this.

mark bower

---

### Post by JKyleOKC on 2011-01-30
Did you run chmod using sudo?

I've seen instructions somewhere in the forums for making it possible to reboot without using the password, but can't recall just where...

The reboot program is located in /sbin and has both owner and group as root, at least on my system. It should be possible for chmod to do the trick: "sudo chmod o+s /sbin/reboot" seems correct. Perhaps changing the first two back to "x" would help. The man pages for setuid are somewhat less than clear to me...

EDIT: From [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

Shutting Down From The Console Without A Password

Often people want to be able to shut their computers down without requiring a password to do so. This is particularly useful in media PCs where you want to be able to use the shutdown command in the media centre to shutdown the whole computer.

To do this you need to add some cmnd aliases as follows:

Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown, /sbin/halt, /sbin/reboot

You also need to add a user specification (at the end of the file after the "%admin ALL = (ALL) ALL" line so it takes effect - see above for details):

<your username> ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS

Obviously you need to replace "<your username>" with the username of the user who needs to be able to shutdown the pc without a password. You can use a user alias here as normal. 

(end of clip)

Read the whole page from which I took the clip. Making changes to the sudoers file without using the "visudo" editing capability can make it impossible to do configuration changes. The recommended editing technique will verify that the file is still in usable condition before writing it back to disk.

---

### Post by mark bower on 2011-01-30
oh oh

I do not use a passwd to boot or shutdown, so thks for your suggestions on this, but I will not need to use.  

No matter what I try(sudo or sudo su), I cannot get reboot to go to 777 with chmod.

I went back to your earlier post and started working on /etc/sudoers.  The owner and grp are indeed root.  Not sure why I went this direction, but I changed the mode to 777 and uncommented "%sudo ALL=NOPASSWD: ALL
I am now locked out, ie on the command line, I get as follows:

rocky@ray:~$ sudo su
sudo: /etc/sudoers is mode 0777, should be 0440
Segmentation fault

That is, I can no longer change to super user?  I tried to chmod the sudoers file back to 440, but I am not allowed.  Apparently I loss the privilege by having changed the mode on this file?

So, how might I restore my superuser privilege so that sudo su works?

mark bower
mark bower

---

### Post by JKyleOKC on 2011-01-30
That problem was what I attempted to warn you about in the last paragraph of my previous message! I didn't even consider that you might change the permissions on the sudoers file!

This is where the "recovery" option of the boot menu saves the day. Reboot into that mode and take the choice to boot as the root user. It will come up as command-line-only and the final character of the prompt will be "#" instead of "$" so that you know you are acting as root. Then chmod the sudoers file back to 0440, log out, and do a normal reboot. That ought to restore your privileges.

That line from which you removed the comment really ought not have any effect on matters; it just gives "sudo" capability to members of the group named "sudo" but in a default installation there aren't any, and I don't believe such a group even exists. Adding the line at the bottom of the file will prevent sudo from asking for the password to execute the reboot command in your script. The "alias" line it suggests is needed only if you want all three of its commands to be executable via sudo without passwords. If you're only interested in reboot, put its full path (/sbin/reboot) into that final line instead of the alias name.

Using the gui to do a reboot or shutdown avoids the need for sudo by going direct to the system call; it's "sudo" that asks for the password, not the actual command.

---

### Post by mark bower on 2011-01-30
Jim Kyle

Thanks so very much.  I followed your instructions and gained back superuser priviledges!  wheww!

In fact, the recovery mode took me to a GUI menu, where upon cursoring down, things went bonkers, never made it to the last line of about six.  So played the game of moving/pressing all the keyboard keys and the correct prompt appeared.  However, key strokes did not show, so again played the "keyboard game"(actually a couple of more times), and was able to effect what you stipulated - return sudoers to 0440.  Not that I plan to alter sudoers again, I am keeping your recovery instruction in my Ubuntu 'trouble shooting section" in my "knowledge 3-ring binder" for future reference - it saved the day.

I really appreciate all the time you have spent with me.  However, I believe I am a little intimidated now on trying to simplify the XP boot process out of Ubuntu -- and so for now -- will accept being satisfied with the unaltered system.  I go to XP for scanning (sometimes, mostly done via VueScan) and for TaxAct for taxes.  So I really don't use XP for a lot.

I came from DOS and QB programming (now using FB), so the command line itself is not a problem for me - but, as you can see, I took a liberty I should not have - messing with something a bit more complicated.  Anyhow, I will continue with the learning curve as I have completely converted to linux, on 4 computers here at the house.

Thanks ever so much again for hanging in with me and instructions to reset the system.

mark bower

---

### Post by JKyleOKC on 2011-01-30
> **mark bower said:**
> I believe I am a little intimidated now on trying to simplify the XP boot process out of Ubuntu -- and so for now -- will accept being satisfied with the unaltered system.  I go to XP for scanning (sometimes, mostly done via VueScan) and for TaxAct for taxes.  So I really don't use XP for a lot.

I came from DOS and QB programming (now using FB), so the command line itself is not a problem for me - but, as you can see, I took a liberty I should not have - messing with something a bit more complicated.  Anyhow, I will continue with the learning curve as I have completely converted to linux, on 4 computers here at the house.As you get a bit more familiar with the system, you might consider looking into VirtualBox as an alternate way of co-existing with Windows. VBox is a virtualization program, that creates "virtual machines" running inside of the real host system. A VM is just like an actual machine except that it's a bit slower (because all of its actions are really being interpreted) -- but disk accesses are often much faster because the virtual disk is actually working in RAM. For best results, the host system needs to have at least 2 GB of RAM and the CPU needs to be at least dual-core. My machines have those specs, and consequently I can run WinXP in a VM and it seems to be as fast as when it's running in an actual box.

The beauty of the VM is that you don't have to reboot to switch between systems. This box currently has six VMs installed, each for its own special purpose. Most of the time, none of them are running; they're all in "saved" state, which is similar to hibernation of a laptop. When I want to run my data recovery utilities, I launch the "DataSave" machine, do what needs doing, then return it to saved state. When it's time to publish my association's newsletter, I do the same with the "Publisher" VM. Similarly for Delphi development, Visual Basic development, and TurboTax operation.

Your history sounds much like mine. I began working with mainframes in 1966, from a time-sharing terminal at 110 baud, and got into the micro world with a TRS-80 Model 3 about 1980, well before IBM brought out the PC. Today most of my computing is done with Xubuntu, but my wife's machine is still Windows-only (not enough free space on it to install a dual boot) although she uses one of my Xubuntu systems to play MahJongg...

---

### Post by mark bower on 2011-01-30
@ Jim

Yes, using a virtual machine might be just the ticket for me, see discussions on it all the time - maybe consider for downstream if I can't completely cut loose from XP.  The PCs I would use XP on are at 2.8Ghz(not dual core), 2GB ram would be no problem.  These two computers have industrial motherboards with ISA as well as PCI; allows me to use legacy A/D boards(talk to outside world in voltages and such).

Interestingly, our family started on the Apple II in 1979 with a B&W TV for the monitor.  My son immediately got involved in changing code in basic games - I did not start learning basic until about 1987 or so.

Thanks for the VM suggestion.

mark bower

---

