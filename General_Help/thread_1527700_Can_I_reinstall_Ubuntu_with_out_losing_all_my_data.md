---
title: "Can I reinstall Ubuntu with out losing all my data?"
date: 2010-07-09
forum: General Help
---

### Post by skikir on 2010-07-09
I Had an odd happening.  I have a Dell lap top with two Hard drives.  One normal and one in the CD bay.  I use the F12 boot sequece to boot to either drive.  W7 does not see the Ubuntu drive but Ubuntu sees the w7 drive.  I noticed that I was not getting and sound in Ubuntu so I reboot to W7 and had no sound there either.  I thought my laptop was dying.  I replaced my normal internal drive with my experimental drive that dual boots to W98xp and ubuntu 10.4 and I had sound again in both those OSs.  Going back and fourth I realized that I had lost the sound only in the first configuration; two drives.  In W7 I did a system restore for a few days in the  past and I had sound again in  W7.   I ran system test and it showed no hardware to configure.  I am not aware of a restore function in Ubuntu but I did a janitor whatever.  I ran some sudo somethings and found that Linux at least saw the Intel hardware.  After some research about sound problems I uninstalled all ALSA and OSS drivers and loaders and then reloaded only ubuntu marked alsa drivers. When I rebooted I had no video and it will not boot to low res failsafe mode!   It's taken me three days working with the sound problem only to bugger up the video.  Even though I'm great in DOS I don't know linux commands, they look like they are totally made up as they go along to me. 

So, Can I reinstall from my CD and get every thing back like you could in Windows 98 or am I going to loose everything?  IF not then I want to get my documents, Firefox bookmarks and Firefox last session open tabs information.  I was doing some research and had about 12 open tabs that took me several days to get to and I don't think I can get back to them with out real hassles.  Of course I didn't bookmark them.  I can get to the drive with my dual boot drive and see everything but I haven't a clue where to find the Firefox install directory!  In windows I'd go to C:\Program Files\Mozilla Firefox\ and poke around and find it but in Linux I haven't a clue where to start.

Any help would help.

---

### Post by 3Miro on 2010-07-09
Many things so lets see if I can answer them one by one:

1. Linux Console/Terminal/CLI (not DOS) commands are faster to type. cd, cp, mv, rm are all two characters and the system folders are /*** with three characters. It may take some time to get used to it, but you will see that it is faster and more convenient. Also 
```
man some_command
some_command --help
```
and will give you info for specific things.

2. For the HDD issue, if you installed Ubuntu with separate partitions for / and /home, then you can just reinstall the thing formatting only the / partition.

3. Since you can access the data on the drive as is (if not, you can try with a live CD or USB stick), it is best to backup anything important just in case something goes wrong. You can make a copy of your
```
/home/your_username/.mozilla
```
folder and move it to another Ubuntu machine or installation. This will preserver history/installed add-ons/bookmarks and so on.

4. I could try to give advice on how to fix the sound without reinstall, however, since even the video is out, it is probably easier to just do a complete reinstall.

---

### Post by bobcollard on 2010-07-09
Put your Live CD in the drive and backup your HD Home folder then reinstall the system.

---

### Post by skikir on 2010-07-14
Thanks all,  I was able to get it up just long enough to get firefox up and export my book marks and last tabs open.  The system was running in low res and felt cludgy like it was about to crash again.  Still did not get sound back after reinstalling.  Looks like the asound folder was empty.  I finally just reformat the the drive.  Funny how my dual boot drive ubuntu partition started acting up also and I reinstalled that as well.  I wonder if I caught a virus.  linux sure is a pain when things go wrong.  Sorry, I have no desire (mental block) to learn Linux commands.  I had enough of that in the 80s.  Ubuntu feels like windows 3.1 which was like a GUI for DOS.  The only thing I do in terminal in W7 anymore is ipconfig.   I guess I should figure out what to back up to restore for emergency conditions.

---

