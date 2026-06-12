---
title: "One profile, two systems"
date: 2012-04-22
forum: General Help
---

### Post by unknown user on 2012-04-22
At the moment, I have two systems running Ubuntu, one on 11.10 and the other on 11.904. The one running the the slightly later version. So soon I will update the 11.04 to 11.10. So I was thinking would I be able to put my profile into my Ubuntu One folder and then be able to point both systems to it, so that no matter which system I was on, I would be able have the most up to date version of my profile.

So my question is, can I 1) have two systems running one profile 2) can I point both systems to look for and load the shared profile in my Ubuntu One folder and would this work?

---

### Post by strafe_sawdoffe on 2012-04-22
I don't think that would be very practical, if even possible. If for no other reason, the latency alone whenever you switch machines might be a showstopper. Also, if you shared your home folder, there's be the possibility of lots of config/settings files getting backed up that the other machine would have no use for. Even if you use the same version of Ubuntu on both computers, I'm sure Machine A will have some programs and settings that machine B doesn't have, etc.

Maybe do that on a small scale, like a feasibility study? Try it with just docs, pictures, and your firefox profile, or something like that, and see how smooth things are.

One last note... how much personal data do you have? Ubuntu One's free service only allows 5GB; I've got over 30GB of music and about the same in ISO files... if you tend not to save a lot of large files maybe you could just create sub-directories in the generic home/Ubuntu One folder, and ignore the local folders like home/Documents, home/Pictures, etc.

If you do end up finding a practical way to do this, be sure to detail it here; I'd be very interested!

---

### Post by HermanAB on 2012-04-22
Google 'NFS Home Dir'.

---

### Post by unknown user on 2012-04-23
I must admit that I was thinking the there may be an issue with the use of two different machines which have different settings.

Thanks for the google search info. That will take a bit of both reading and doing, so may be able to post my reqults later.

---

### Post by audiomick on 2012-04-23
You might be able to get a step along the way by using the same /home partition for both installations. If you don't have separate /home, look at this
[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

bear in mind that if the two installations are too different, you could have problems. Using the same /home for very different flavours of Linux, for instance Suse and Ubuntu, is not a good idea, as far as I know. For two subsequent Ubuntu versions, it might be ok.

You can also copy the config files out of one /home into another.

---

### Post by mangmista on 2012-04-25
well after i bought new laptop and get to my ubuntu one i had registred two PC in so i guest it is posible. I didn´t need smething from it so i deleted one laptop.

---

