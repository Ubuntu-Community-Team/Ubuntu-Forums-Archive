---
title: "Glest slow ang jerky on 9.04 but fine on 7.10"
date: 2009-09-02
forum: General Help
---

### Post by cogvos on 2009-09-02
Dear all,

Appols if this is the wrong place to ask. I have two installs - 7.10 which has been running fine for ages and a new install 9.04. I thought I would have a look around at changes and so loaded up a couple of apps that I use. One is Glest, the 3d strategy game. This was a surprise as it is fine on 7.10 but chops and jerks horrendously on 9.04. I'm guessing this is due to changes in something or other (sorry not techie) but don't know where to start looking. other applications and other open gl applications I have tried look OK. Though I have yet to find something that really tests a system.

Can someone point me at likly reasons for Glest to be so choppy and slow on 9.04 and can someone suggest another game/app that tests graphics and sound so I can see if it is the install or version of Glest I am running.

Incidentally the installs are on the same pc so it's not a hardware issue.

Here's hoping.

---

### Post by cogvos on 2009-10-28
OOOkay. After a lot of fiddling around I downloaded 3.2.2 from the Glest site - they have zips and archives there so I copied all the files and it works. Problem is it only works as ROOT.

So can someone tell me how I get an application to run as a normal user? There is a log file in glest - but it just shows 

Log file

Core data

Which is not very helpful.

J.

---

### Post by MaxIBoy on 2009-10-28
Install it to your home directory. Then make sure you have read/write permissions on all its files.


Also, maybe your performance problem is becasue you have Intel graphics hardware. The drivers for Intel graphics in 9.04 were defective so 3D acceleration had to be crippled. You can revert them to a working version; look up "revert intel drivers ubuntu 9.04" and you should find tutorials.

---

### Post by cogvos on 2009-10-28
> **MaxIBoy said:**
> Install it to your home directory. Then make sure you have read/write permissions on all its files.


Also, maybe your performance problem is becasue you have Intel graphics hardware. The drivers for Intel graphics in 9.04 were defective so 3D acceleration had to be crippled. You can revert them to a working version; look up "revert intel drivers ubuntu 9.04" and you should find tutorials.

Many thanks for the info. It's currently installed in user/libs/glest (quite why the synaptic install has put it there is beyond me) ans I just copied the new files over the old. Probably not the correct thing to do but I could not figure out how else do do this so that all users could run it. Sadly as mentioned at present they cant :( . 

Sorry to say I am very green at all this, so how do I give myself/ other users read/write permissions to the files? If I look at the permissions in Nautilus I get 3 options, I guess I need others, but can't figure how to do a blanket change. Is there a way I can 'poke' the main glest directory so that other users can read/write files? 

Re the performance problem. 3.2.1 (as installed from the repositories) hits the processor 100%. 3.2.2 from the glest site does not, which suggests that it's the repository version that has a problem. I have an Nvidia card and am running the non-free drivers.

---

