---
title: "stuck at loading screen"
date: 2011-04-17
forum: General Help
---

### Post by enimeizoo on 2011-04-17
Hello,
I have used ntfs-config to edit my fstab file in order to mount my windows partition (ntfs) on boot, but since then I'm getting stuck at loading screen randomly. It happens about one out of two times. 
This issue isn't totally new since I have already been stucked at loading a few times before, but not as often. It didn't happen more than once a month. 
So my question is :  how can I figure out more about this issue? What should I check?

I should mention that I did it on two computers, both toshiba. One has a very fresh and clean installation, the other one has a lot of stuff on it, so I'm pretty sure it comes from loading the ntfs partition at boot. 

Any help is welcome, and of course I'll provide any info you might need from both computer, just tell me what you need to know.

---

### Post by mastablasta on 2011-04-17
you can check the logs.


i think dmesg command should give you some information on what happens during boot. you will probably somehow need to dump the output. when it gets stuck can you go to command line?

BTW why do you need to mount it on boot?

---

### Post by enimeizoo on 2011-04-17
Thanks for your reply. I need to mount it to display my windows desktop in a folder view for kde desktop. But if it isn't mounted at login, I have to mount it manually, or have a progream like dolphin to mount it for me. So, if there is any other way to have it working, I'll take it. The fstab thing looked the simplest to me.
I tried the dmesg command, but it seems the info I get is only from the last boot. So I would have to get a terminal when the computer is stucked to have any clue about what is going on, rigth? 

By the way, the loading screen I'm talking about is the one before the login screen.

Well, I just tried to reboot a few times, but it worked... So I'm just going to wait for it to happen and bump here with the news... Again, thanks for helping!

---

