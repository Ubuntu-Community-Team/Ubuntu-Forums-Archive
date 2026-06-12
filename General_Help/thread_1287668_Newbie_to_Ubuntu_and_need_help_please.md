---
title: "Newbie to Ubuntu and need help please"
date: 2009-10-10
forum: General Help
---

### Post by crash2win64 on 2009-10-10
Hey I recently installed Ubuntu 9.04 a couple weeks ago and didn't have many problems till the other day here. Finally got my internet hooked up from AT&T(nightmare :mad: ) and did the updates and had to reboot the computer for my updates to take effect. Well rebooted and now it won't load the desktop. It gets to where its loading and the screen gets a funky look to it and freezes up. I am at a loss as what to do here to fix this. I tried some of the menu options when grub loads up and you hit escape. But ya I'm lost
Any help would be greatly appreciated

Thanks

---

### Post by nikhilbhardwaj on 2009-10-10
press ctrl+alt+F1
when you get stuck
can you access the tty1 console ??

---

### Post by ZaHACKieL on 2009-10-10
What video card do you have? Maybe you upgraded the kernel and when you do that you sometimes have to reinstall the video drivers.

I have an ATI Radeon and everytime I upgrade the kernel I have to first boot from a former kernel, reinstall the drivers and boot back again from the new kernel.

So, let me know about your video stuff.

ZL

---

### Post by crash2win64 on 2009-10-10
Well I dunno what the tty1 console even is? Like I said total noob. Sorry
I'm not even really sure with the command line stuff either I'm tryin to figure things out and been reading a little here.

As far as my system goes its pretty basic. I think MSI board with onboard video and sound. At least I think anyways. I'll see what it says when I try a reboot here in a min. So nothin too fancy

---

### Post by CharlesA on 2009-10-10
tty1 is just the first command-line console. You access it from Ctrl+Alt+F1.

I'd suggest resetting the x.org config: [http://ubuntuforums.org/showthread.php?t=396556](http://ubuntuforums.org/showthread.php?t=396556)

---

### Post by crash2win64 on 2009-10-10
Yea but I can't into the GUI at all it freezes right there at the load up screen. I'm kinda wondering if reinstalling the OS would help this out? But the other thing is would I lose all my files I have on here already or would it just install over the old system without having to format??? This is a PIA kinda lol

---

### Post by dchurch24 on 2009-10-10
Wooah there - no need to do anything drastic.

Can you (as the others have asked) get to a command prompt?

Can you type on something that looks a bit like DOS?

If so, then it's probably recoverable.

---

### Post by crash2win64 on 2009-10-10
Ok when loading up and you hit the escape button during Grub load up I can get to a prompt with 5 selections 2 normal 9.04, 2 recovery 9.04, and I think a mem test. When you go into one of the recovery choices theres a bunch more selections after a little load up and you can enter a command prompt with or without networking. 

What would I need to do when I get to the command prompt then???

---

### Post by ZaHACKieL on 2009-10-11
> **crash2win64 said:**
> Ok when loading up and you hit the escape button during Grub load up I can get to a prompt with 5 selections 2 normal 9.04, 2 recovery 9.04, and I think a mem test. When you go into one of the recovery choices theres a bunch more selections after a little load up and you can enter a command prompt with or without networking. 

What would I need to do when I get to the command prompt then???

How many kernels you see you can choose from?

ZL

p.s. or maybe if you can upload a screenshot ot something..

---

### Post by noelvh on 2009-10-11
To test this when you see grub flash by on boot up press the ECC key. This will bring up the grub boot loader menu. When you system gets a new kernel grub keeps the old one just in case you need it. Another option is to use the recover option for the current kernel and reset the x server (video settings). So to sum this up when you hit the power button get ready to hit the ESC key. This can be fast if you have a fast pc. Now you will have a menu with kernel versions plus a recover entry for each kernel version. The top kernel is the current version, so if you want to fix the current one use the second item down from the top. I have not been it to that for a very long time but look for any thing that has an X in it. What that will do is reset you video settings. If you want to see if you system is messed select the third option in the grub menu. This will be the last kernel use used before the update was done.

I am a forever noob and I hope this helps you.

Noel

---

### Post by crash2win64 on 2009-10-12
Ok. I did try the repair video settings in the recovery menu of both kernels the new and the old and it does the same thing either way. I don't have a clue how to do a screenshot really to  be able to show you exactly. I think this happened because of the updates I did and I know I picked some other option that was like the untested ones? I dunno exactly but kicking myself now for it... Somebody was trying to tell me I have to enter a command prompt and enter some code or something to be able to fix that so I guess thats what I'm gonna try now... Another thing would it really be that hard to just reinstall ubuntu over itself to fix this? The install doesn't take that long and the only thing that concerns me is if it'll make me lose whats on my HD if I have to reformat it. So do you have to format to do the install each time?

---

