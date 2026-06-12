---
title: "Linux Support for IPod Touch?"
date: 2012-04-16
forum: General Help
---

### Post by mabo5184 on 2012-04-16
Hello,
 
Can anyone point me to the difinitive source regarding which versions of IPod/iOS are fully supported in Linux.
 
I know now I made a big mistake buying an Apple product ...
 
I use my ipod to listen to podcasts and music, and I have tried using Banshee and Rhythmbox.
 
Podcasts sycned with Banshee wont play on my ipod, and most of my content syned with Rhythmbox works but not all ...
 
I have been putting up with this situated for a couple of years, basically since I started using linux my preferred OS, but I would like to have a system that just works smoothly, so the option of buying a new media player is on the horizon ...
 
My research so far tells me that the problem with apple products is their practice of encrypting the database. The library libgpod is the main software that talks with the database but it only supports early versions iOS when the encryption was cracked by some resourceful hackers, but unfortunately Apple changed their encryption method ...
 
Unfortunately, I upgraded my IPod iOS at some point whith out saving the SHSH Blob so I cannot go back, I now know this was a big mistake ...
 
Currently I am using Ubuntu 11.10 and IPod 3G iOS 4.0
 
If I jailbreak my ipod then is their software that will fix this problem or should I start looking for a new media player?
 
The Samsung Galaxy S WiFi looks nice ...

---

### Post by iponeverything on 2012-04-16
> If I jailbreak my ipod then is their software that will fix this problem or should I start looking for a new media player?


lets see.. jailbreak or buy something else.. where perhaps you will be faced with same jailbreak or buy dilemma 

seems like you a need break in there somewhere to prevent an infinite loop that might run up your credit card.

---

### Post by zdeuyo on 2012-04-16
Try gtkpod ipod manager. It works for my iphone 3gs. You may have to update your repositories. Let me know.

---

### Post by mabo5184 on 2012-04-16
zdeuyo, what version of iOS is your IPhone running?

---

### Post by zdeuyo on 2012-04-16
5.1 (9b176)

---

### Post by mabo5184 on 2012-04-17
I installed gtkpod but unfortunately it does improve my situation.
 
GTKPod does recognize my ipod and reads the database and I can delete files from my ipod. The app does not download podcasts so I would need to use another program for doing the download. 
 
I used Banshee to download a podcats I am having problems with "GNU World Order", but GtKPod will not import because wrong format, I guess because it is an ogg format, anyhow I could use another program to convert to mp3, so that would mean 3 apps to listen to my podcast.
 
I tried downloading another podcast from "NPR", this imported into GTKPod ok, and it syned to my ipod showing no errors, but the the podcast shows up on my ipod with unkown title and when I select it to play it has no music available.
 
So in summary I appreciate the suggestion but it does not improve my situation.
 
Rhythmbox works the best because it downloads my podcasts, it converts non-mp3 automatically while syncing, and it sync's most of my media to my ipod. It is just a handful of podcasts I have problems with like Gnu World Order.
 
I think the problems may be iOS database format not fully supported and/or id3tag version support issues in Rhythmbox. I have thought of loading a bug for Rhythmbox but I don't want to waist their time if it's a simple fix I can find myself.
 
Any other suggestions are welcome ...

---

### Post by zdeuyo on 2012-04-17
Hello,


I am sorry to hear that. The problem with connecting lies with the repository for the IPhone.

To make the answer simple it is good to have Windows dual booted with Itunes installed.

I am against using Windows at all means possible, but since Apple 'locks down' their devices and they are not open sources like android this causes the use of multiple programs on Linux sub Ubuntu to make it work.

Hopefully an open source program will spawn in the Software center soon. I am sorry I could not be more of a help.

---

