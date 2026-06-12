---
title: "Shotwell for 9.10"
date: 2010-10-01
forum: General Help
---

### Post by Cpierce on 2010-10-01
I installed shotwell on my 10.04 machine and it worked great, especially uploading to facebook. It installed version 0.7.2 

So I installed it on a 9.10 machine, and it installed version 0.5.2  which has problems uploading to facebook. I installed using these commands:

sudo add-apt-repository ppa:yorba/ppa

sudo apt-get update && sudo apt-get install shotwell

I tried using "sudo apt-get upgrade" but nothing happened. I searched for a Deb file for version 0.7.2 but couldn't find one. 

Can someone tell me how to get Shotwell 0.7.2 on 9.10 ?

---

### Post by gandaran on 2010-10-01
> **Cpierce said:**
> I installed shotwell on my 10.04 machine and it worked great, especially uploading to facebook. It installed version 0.7.2 

So I installed it on a 9.10 machine, and it installed version 0.5.2  which has problems uploading to facebook. I installed using these commands:

sudo add-apt-repository ppa:yorba/ppa

sudo apt-get update && sudo apt-get install shotwell

I tried using "sudo apt-get upgrade" but nothing happened. I searched for a Deb file for version 0.7.2 but couldn't find one. 

Can someone tell me how to get Shotwell 0.7.2 on 9.10 ?
since you have run sudo apt-get update you should have an update for shotwell if the old version is still installed, check that the repository was correctly added to software sources then check your updates in synaptic package manager.

---

### Post by skyjacker on 2010-10-01
This is the home page for Shotwell. "http://yorba.org/shotwell/install/#binaries"  
Pick the button for Ubuntu and follow the directions... It is not a good idea to install the application this way because this version has not been tested for the version of Ubuntu you are trying to put it in. This is why you can't get the latest version installed using the software manager

---

### Post by Cpierce on 2010-10-01
I am still confused. I went to the home page, pushed the Ubuntu button, and followed the instructions and it still installed the version 5.

---

### Post by gandaran on 2010-10-02
> **Cpierce said:**
> I am still confused. I went to the home page, pushed the Ubuntu button, and followed the instructions and it still installed the version 5.

look, the whole thing is very simple, first check if the ppa repository was correctly added to software sources and make sure the package list was updated, then remove version 5 first, (use synaptic package manager to do [COLOR="Red"]complete removal[/COLOR] of the package), then find in synaptic the new version and mark for install and click the apply button or use the CLI install command.

---

### Post by Cpierce on 2010-10-02
I really appreciate the help. I know the PPA installed correctly and is checked in the "other sources". I did remove the old version in synaptic, but didn't do "complete removal" because I have had that remove way more than just the program I was trying to remove. I did however remove the hidden ".shotwell" file in my home folder. I do know that when I go into synaptic after running "sudo apt-get update" and type in shotwell, there is only one file available and that is 0.5.2. If there is an update, it must not be able to bring up by typing "shotwell".

I will run through the whole process again and report back.

---

### Post by Cpierce on 2010-10-02
Here is what I did. 

-went to synaptic and did "complete removal"
-went to "other sources" and removed the PPA
-went back to synaptic and verified that Shotwell was removed/not listed.
-went to home folder and made sure .shotwell was deleted
-re-installed PPA and ran sudo update
-went back to synaptic typed in shotwell and 0.5.2 was the only option available. 

so I am back to my original question, how do I install shotwell 0.7.2 ? Version 5 has bugs and won't do what I am trying to do. Even on their homepage to solve the issue, they recommend installing a newer version. Just wish I knew how to do it.

Any help is greatly appreciated.

---

### Post by gandaran on 2010-10-02
> **Cpierce said:**
> Here is what I did. 

-went to synaptic and did "complete removal"
-went to "other sources" and removed the PPA
-went back to synaptic and verified that Shotwell was removed/not listed.
-went to home folder and made sure .shotwell was deleted
-re-installed PPA and ran sudo update
-went back to synaptic typed in shotwell and 0.5.2 was the only option available. 

so I am back to my original question, how do I install shotwell 0.7.2 ? Version 5 has bugs and won't do what I am trying to do. Even on their homepage to solve the issue, they recommend installing a newer version. Just wish I knew how to do it.

Any help is greatly appreciated.
looked in the ppa repository, theres no version 7 there for ubuntu 9.10, only 10.04 and 10.10 have it
[https://launchpad.net/~yorba/+archive/ppa?field.series_filter=karmic](https://launchpad.net/~yorba/+archive/ppa?field.series_filter=karmic)
[https://launchpad.net/~yorba/+archive/ppa?field.series_filter=lucid](https://launchpad.net/~yorba/+archive/ppa?field.series_filter=lucid)

---

### Post by Cpierce on 2010-10-02
So, can it not be done ? On the homepage it talks about installing version 7 into 9.10 via "from source" by building the package. 

Or should I edit that PPA from karmic to lucid, and then update and install in synaptic ?

---

### Post by Cpierce on 2010-10-03
I just updated her computer from 9.10 to 10.04, so this isn't an issue for me anymore

---

