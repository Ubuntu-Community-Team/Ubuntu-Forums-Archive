---
title: "Help with Grub..."
date: 2009-12-12
forum: General Help
---

### Post by wwkuter on 2009-12-12
Hi everyone,
 
A while ago, when I was booting my laptop, I accidentally selected the recovery mode in the grub OS menu. Since I had some issue with grub, so instead of selecting boot normally, I curiously selected one of the options that says "grub" in it (which was really stupid, I don't know why I did that...:(). After that, everytime I restart my computer, it will directly go to the grub command line instead of the grub menu. Now have to type commands to boot into the system I want. I tried to recover grub with setup (hd0), but that doesn't really help. How can I get the OS selection menu back?
 
Thanks in advance.

---

### Post by ranch hand on 2009-12-12
What version of grub are you running.  If in doubt run;
```

grub-install -v

```
which sill tell what grub you have.

If you are on some thing older than 9.10 you are using grub-legacy.

How did you try to recover grub?  This is what needs done and it should straighten you right out.

---

### Post by wwkuter on 2009-12-12
Thank you for the reply. I'm using Ubuntu 9.10.
 
Actually, I'm also having trouble to boot into Ubuntu. I can only boot into Windows by using the following command:
```

root (hd0,1)
chainloader +1
boot

```
If I replace (hd0,1) with the location of Ubuntu, it will give an error saying kernel must be loaded before booting, I've tried several sources but they didn't really help. Now I can only get into Ubuntu by using a Live CD. What would you suggest me to do at this point?

---

### Post by ranch hand on 2009-12-12
Was this a clean install or an upgrade.  If you upgraded you should be using grub-legacy and if a clean install it will be grub2.

If this is an upgrade run the command I gave you before.  The 2 grubs do not play well together.

---

### Post by wwkuter on 2009-12-12
I booted with live CD and used your command.  It showed GNU GRUB 0.97.

---

### Post by john newbuntu on 2009-12-12
At the grub prompt, type ls
grub>ls

This might show something like: (hd0), (hd0,1), (hd0,2) etc
Next, determine the partition where the /boot directory of linux resides.  You can do this by examining each and every entry in the above result. So for example:

grub>ls -l (hd0,2)/
will check the second partition
grub>ls -l (hd0,3)/
will check the 3rd and so on.

Once you know the partition that has the /boot directory, set that as the root.  Lets say (hd0,5) is where /boot is (This corresponds to /dev/sda5):
grub>set root=(hd0,5)

Then type these at the grub prompt:
grub>linux /vmlinuz root=/dev/sda5 ro quiet splash
grub>initrd /initrd.img
grub>boot

Once you get in this way, please issue the command in a terminal:
sudo update-grub2

---

### Post by wwkuter on 2009-12-12
Thanks for your response.  But at the grub prompt, most of the commands you've mentioned are not being recognized....

---

### Post by ranch hand on 2009-12-12
This is great.

You need to boot from a LiveCD of some OS NOT using grub2.  The 9.10 CD will not do.  9.04 or before will be great.

Pull the terminal up and run;
```

sudo grub

```
This will give you a grub prompt like you saw before "grub>".

These commands need run in this order;
```

grub> find /boot/grub/stage1
This will give you a list of all instances of active grub in this form "(hdx,y)" where x isthe drive and y the partition.  In your case I assume there will only be one.
grub> root (hdx,y)
Just copy from previous result.
grub> setup (hdx)
Same as above with out the partition designation.
grub> quit

```
Reboot you should be fixed.

If not we have another option.

---

### Post by wwkuter on 2009-12-12
Thanks for the help.  But before I posted on the forum, I've tried that method with a 9.04 Live CD, and it didn't fix the problem....  What else can I do...

---

### Post by ranch hand on 2009-12-12
Well, I would say that your grub-legacy is corrupted.  This is probably due to having too much of grub2 mixed with it.

What I would recommend is to chroot into your system from the live CD and remove "grub" and "grub-common".  Then install "grub-pc" and "grub-common".  Yes there is a command to "upgrade to grub2".  Don't do it.  You will have the same problems with grub2 as you do now.

The grub-common you install will basically be the same as what you remove, without some stupid files left over from grub-legacy.  It works with either grub but is really built for grub2.

When you install it will run "update-grub".  This should pick up all your OS'.  There are times it miss' MS installs.  Do not worry about it if this is your case.

When you boot into Ubuntu pull up the terminal and run;
```

sudo update-grub

```
and it will, 95% of the time, pick up anything it missed.

Grub-legacy is no longer supported by the grub folks, this is important to understand.

Grub2 is very different.  Read the link in my sig and take a close look at the second link I provide in my post.  A great, in depth, guide to grub2 by drs305.  In his sig there are some other How tos that you might want to look at to.

---

### Post by wwkuter on 2009-12-12
Aghh, everything is going against me now.

I chroot into my OS, and removed grub and grub-common. However, when I try to install grub-pc and grub-common, it's giving me error saying that it's unable to resolve the address of all the package sources, even though I can browse those websites through a browser...:( What should I do now..................?

---

### Post by ranch hand on 2009-12-12
Just use;
```

apt-get update

and then

apt-get install grub-pc grub-common

```
That should do it.

---

### Post by wwkuter on 2009-12-12
That won't work. apt-get update will give me a lot of error.

I've downloaded the files manually and put under /mnt.

Now during the installation of grub-pc, I received the following message:

The following Linux command line was extracted from /etc/default/grub or the 'kopt' parameter in GRUB Legacy's menu.lst. Please verify that it is correct. and modify it if necessary.

Linux command line:
*an empty line*

What should I type there?

---

### Post by ranch hand on 2009-12-12
I don't think you need to type anything there.  I think you need to hit enter.

However, I would like to know the errors that apt returned.  I suspect that when you chrooted in you left something unmounted.

I a fairly new to chrooting and know this is common.  I had to learn to do that in the last "testing" cycle.  9.10-testing had some real rough spots.  So far 10.04 is not to bad but it is early days.

You would be a lot better off to correct those problem and use apt.  The reason I say this is that you will probably run into problems installing.

You may as well give it a whack seeing as you are well into it.  I hope it works.

---

### Post by wwkuter on 2009-12-12
Yes! It worked!! Thank you so much!

The errors that I'm getting are that it is unable to resolve all the addresses. I think it's probably because when I do chroot, the internet for the system I mounted is not working properly...especially when I'm using wireless...

Now just another question, after booting into Ubuntu, I opened a terminal, and typed "sudo update-grub", and it successfully found my Windows OS. However, after I reboot the computer, there's no Windows in the menu. Instead, on top, there's a chainload to GRUB 2 option, and it also says use some upgrade command after verifying that grub 2 works. Could you explain what's going on and what I should do next?

Thank you very much for spending the time helping me. I sincerely appreciate it.

---

### Post by ranch hand on 2009-12-12
You have not gotten all of grub-legacy off your box.

That is the chainload crap.  You are still using grub0.97 and it thinks you want to chainload to grub1.97 to try it.  I have no idea why they didn't just have the upgrade wipe grub-legacy and install grub2.  It has caused no end of problems.  I have several upgrades myself.  I never had trouble.  I installed grub2 before upgrading.

That comes from fooling with grub2 since Karmic Alpha2 when grub2 made its firs appearance.  In the testing forum we tried to convince the forum mods to put a sticky in the ABT forum or make a temp forum just for grub2 because we new it was going to be a wreck.

Now that you are in your system, without rebooting before you are done, I would go to synaptic and remove "grub" "grub-pc" and "grub-common".  Then, immediately, install "grub-pc" and "grub-common".

You will probably need to run "sudo update-grub" again.  When you finish with that run "sudo grub-mkconfig".  This will output your /boot/grub/grub.cfg in the terminal (expand to full screen so you can see it right).

That way you can check what will be on the menu screen right then and do something different if needed.

EDIT;
Sorry for the rant.  I am a very tired grumpy geezer.

---

### Post by wwkuter on 2009-12-12
Thanks again!

It fixed all the chainload things, but Windows is still not in menu.lst even though it's in grub-mkconfig. I guess I will just have to add it manually.

---

### Post by wwkuter on 2009-12-12
Hmm, this is weird.

From the other post you provided, I see that everything from grub.cfg should be the stuff I see during boot. However, that's not the case for me...............I have Windows listed in grub.cfg, but it's not shown during boot.........

---

### Post by wwkuter on 2009-12-12
I commented some lines out in menu.lst, and they did not show up during startup....so does this mean the computer is still using grub 1? I've completely removed it before I installed grub 2......how is this possible......:(

---

### Post by ranch hand on 2009-12-13
Run update-grub again and see if that helps.

If not run;
```

gksudo gedit /etc/grub.d/40_custom

```
This will pull up a wonderful file that is intended for making custom menus.

Use this type of entry for your Ubuntu;
```

echo "Adding PhatDebian on sda7" >&2 
cat << EOF
menuentry "PhatDebian on sda7" {
        set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 so quiet splash
        initrd /initrd.img
}
EOF

```
Remember that grub2 counts the drives the same way grub-legacy did, starting with 0.  The partition is not counted that way any more but the counting starts with 1 just like gparted does.  In the entry above if it were in grub legacy the root would be (hd0,6).

The above entry is a "symbolic" menuentry.  It will never need updated.  It boots to the newest kernel on the defined partition.  I love them.

Your MS menu entry needs to be just as you see it in your grub.cfg with the addition of the stuff above and below the menuentry above.

The stuff between the " marks you can edit all you want.  

Be sure that the { } s are in the right place.

Also, before you start, go to preferences in gedit and change it so that line wrapping is NOT allowed.  I also like the lines numbered and the current line highlighted.  That is up to you.  The ling wrapping thing is manditory for working with grub2 files.

When you finish save the file as "06_custom".  This will put it at the top of your menu.  If you want, you can then cange the permissions of 10_linux, 20_memtest86, 30_os-prober and 40_custom so that they are not executable.  They will then not show up at all in your grub.cfg file.  I like keeping 10_Linux because it gives you the standard generated menuentry for your OS and recovery mode.

I do not have my test platform mounted right now or I could show you an interesting menu.  This is the menu of my sdb internal drive just PhatDebian (Lenny respin running 2.6.30 kernel with ext4 support so it can see my ext4 partitions, if you like Debian Lenny check out PhatDebian).
> 
echo "Adding KinkyFR on sda9" >&2 
cat << EOF
menuentry "KinkyFR on sda9" {
        set root=(hd0,9)
        linux /vmlinuz root=/dev/sda9 so quiet splash
        initrd /initrd.img
}
EOF

echo "Adding PhatDebian on sda7" >&2 
cat << EOF
menuentry "PhatDebian on sda7" {
        set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 so quiet splash
        initrd /initrd.img
}
EOF
### END /etc/grub.d/06_custom ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set 4f2770a4-0ffc-4fea-967d-92151b4f69a7
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=4f2770a4-0ffc-4fea-967d-92151b4f69a7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set 4f2770a4-0ffc-4fea-967d-92151b4f69a7
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=4f2770a4-0ffc-4fea-967d-92151b4f69a7 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,9)
    search --no-floppy --fs-uuid --set 4f2770a4-0ffc-4fea-967d-92151b4f69a7
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=4f2770a4-0ffc-4fea-967d-92151b4f69a7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}

Kinky refers to Kinky Kitten, this is the OS known to most as Karmic Koala.  I generally refer to Lucid Lynx as Lounge Lizard.  The guys that name these thing are not FUN.

And no, there is no Win JerryLewis Pro allowed in this house.  My box is clean.

---

### Post by wwkuter on 2009-12-13
Thanks for the help. 

Well, I've just did exactly what you said, but it didn't fix the problem. I just want to know if it's normal that the computer is still loading menu.lst instead of grub.cfg even though I have completely removed grub 1? grub.cfg already has everything I need, but for some reason it never gets loaded when I reboot the computer. I'm certain that the computer is still loading menu.lst because I commented out a few lines in menu.lst, and those lines did not show up in the boot menu, so that means grub2 is never started...I'm really confused now...

---

### Post by wwkuter on 2009-12-13
Never mind, problem fixed....

My linux-geek friend just told me that I have to do a "sudo grub-install /dev/sda", and that fixed all the problems......

---

### Post by ranch hand on 2009-12-13
Oh the devil and all his helpers,  I told you I was tired.

Sorry.

Good work getting it going.

I think you will like grub2 a bunch.  In spite of all your troubles, it really is more flexible than grub-legacy.

---

### Post by wwkuter on 2009-12-13
Haha, thanks a bunch for the help you've provided! I've sure learned a lot from all these troubles...;)

---

