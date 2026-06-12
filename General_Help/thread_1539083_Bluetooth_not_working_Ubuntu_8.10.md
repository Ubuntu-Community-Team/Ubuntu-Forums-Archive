---
title: "Bluetooth not working Ubuntu 8.10"
date: 2010-07-26
forum: General Help
---

### Post by Mortesins93 on 2010-07-26
Hello,
I am trying to connect my cell phone through a Bluetooth dongle in Ubuntu 8.10 but when i try setting up a new device my cell phone is not seen. I tried reading some guides, i installed everything needed but still it doesn't work, some files are even missing (probably because they guides are for older versions of Ubuntu but i can't find a new guide on it) like ....I tried the following commands:
jessica@jessica-desktop:~$ sudo hcitool scanScanning ...
    00:16:75:15:14:81    Hill Billy
jessica@jessica-desktop:~$ sudo hidd --connect 00:16:75:15:14:81
Can't get device information: Success
jessica@jessica-desktop:~$
I guess they work but how come my device is still not seen in the Bluetooth applet? How can i send files? Why can't I connect to the computer using my phone?
Please help I don't want to depend on windows for this too.
Thanks in advance.

---

### Post by P4man on 2010-07-26
someone has to say it.. why not upgrade to the new LTS (ubuntu 10.04)? So many bluetooth isses have been fixed.

---

### Post by Mortesins93 on 2010-07-26
Ok, so I could do that but the computer is not that powerful it has a 2.5Ghz CPU and only 512Mb of RAM, how much slower would it run? How does the upgrade work, I insert the CD when i am already logged in or do I have to do a fresh install? Do I lose all my data on my partition (not very important I would still backup)? What about my applications do I have to install them again? 
The real problem is that it is not my computer so I want the installation to go perfect because the owner of the computer doesn't want to fix the problems on his own but just wants it to work. After all I only have that problem and I don't want to end up with an installation that has more problems than the previous one especially if they are vital (bluetooth thing is not a big deal after all). If it goes wrong then he would go back to Windows and that would be my failure, if you know what I mean. 
Another reason why I am not so confident i doing this is that I tried installing the 10.04 version of Xubuntu on my computer and the usb wouldn't work so I got back to Karmic because i could not solve the problem because my internet adapter is connected through USB. I hope this problem is only for the Xubuntu version.
I don't want to sound so negative but since it is not my computer I want to be careful.
Thanks for the suggestion and I hope you can answer my questions.

---

### Post by P4man on 2010-07-26
Maybe there is a real fix for this without upgrading; but i dont know it obviously or i would have told you :)

But more importantly; ubuntu 8.10 is not a long term support release; in fact, support ended a few months ago; so you have no more access to updates; no more repository etc. You are going to have to up (or down)grade anyhow. 10.04 is a LTS release and will be supported until 2015.

As for speed; 512 Mb I think should just about cut it. You can give it a try using a livecd or usb stick and find out (keep in mind longer boot times are due to the live cd) and see if bluetooth and everything else works properly. 10.04 has some very nice speedups but it does use more RAM. If you find its too slow, consider lubuntu or perppermint linux (both ubuntu based but much lighter weight).

As for the upgrade process.. there no longer is an upgrade path from 8.10. There would have been one a few months ago; although a tedious one (8.10 -> 9.04 -> 9.10 -> 10.04). You are now looking at a reinstall Im afraid. And yes that means you have to reinstall all the apps and reconfigure anything that needs configuring. If you have a seperate /home partition; that latter shouldnt be too much work; and if you want you can export a list of installed packages and apps and import that on your fresh install, but I have never tried that across 4 versions so i dont know how well it works. I guess it should work.

```
sudo dpkg --get-selections > packages.lst 
```

Then import that lst file again after the reinstall. It will obviously install all new versions of those same apps in so far they exist in the repository.

---

### Post by Mortesins93 on 2010-07-27
So you are saying I practically have no choice because i can't even install new packages, right? Ok, so I guess i will have to do it. Thanks for the information.

---

