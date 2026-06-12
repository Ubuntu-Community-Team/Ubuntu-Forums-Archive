---
title: "unable to download whole packages...ubuntu 10.04"
date: 2010-08-08
forum: General Help
---

### Post by CROLMAC on 2010-08-08
Hi there I am having some problems"I had experimented a little yesterday and had ended up losing my software center and being unable to update and /or download Any software. I figured I had crapped my system and so decided to reinstall... as I say I decided to  experiment. Since then I have had oodles of problems to download packages that I had downloaded before, and there is aways a failure in gettting files, such as 404 reports, the files may be expired or removed from their site, too old, etc. For example I went to install greek in the language center and it told me to check my internet connection...Where did I goof it up? or am I just having a bad server day?btw I tried tweaks that I know how to do, lust to be sure it isn't my anti geekiness that kicked in. thanks bunches for your help
    eeepc 900 ubuntu lucid lynx

---

### Post by soldier1st on 2010-08-08
which version did you install?also is it the 32bit or 64bit version?also it could be a server issue but when you installed it did you select the greek language when it first booted up?

---

### Post by linux18 on 2010-08-08
if " ping -c 1  [www.google.com](www.google.com) " returns anything other than unknown host, your connected to the internet.
then try ```
 
sudo killall synaptic && sudo killall aptitude && sudo killall mintinstall && sudo killall software-center 
sudo rm /var/lib/dpkg/lock && sudo rm /var/cache/apt/archives/lock && sudo rm /var/lib/apt/lists/partial/* && sudo rm /var/cache/apt/*.bin 
sudo dpkg --purge $(dpkg -l |grep  ^rc |awk '{print $2}' | tr '\012' ' ') 
sudo apt-get -f install && sudo apt-get clean && sudo apt-get autoclean 
sudo apt-get autoremove && sudo apt-get update && sudo apt-get --fix-broken upgrade 
 
``` 
to fix synaptic then  post back with the results

---

### Post by linux18 on 2010-08-08
if " ping -c 1  [www.google.com]("http://www.google.com") " returns anything other than unknown host, your connected to the internet.
then try ```
 
sudo killall synaptic && sudo killall aptitude && sudo killall mintinstall && sudo killall software-center 
sudo rm /var/lib/dpkg/lock && sudo rm /var/cache/apt/archives/lock && sudo rm /var/lib/apt/lists/partial/* && sudo rm /var/cache/apt/*.bin 
sudo dpkg --purge $(dpkg -l |grep  ^rc |awk '{print $2}' | tr '\012' ' ') 
sudo apt-get -f install && sudo apt-get clean && sudo apt-get autoclean 
sudo apt-get autoremove && sudo apt-get update && sudo apt-get --fix-broken upgrade 
 
```to fix synaptic then  post back with the results

---

### Post by CROLMAC on 2010-08-09
thanks for your interest. My internet connection works fine, I think, and I am a native english speaker, but living in greece makes it usefull to be able to change written language at will as the alphabet is different.
 In my first install on my 900, all worked ootb.
 I experimented a little, goofed up a few things, and lost the content of ubuntu software center. Thinking I was smart,I said no sweat,I'll reinstall lucid lynx. 
 My husband had to reinstall,'cos I  goofed that one too (apparently I had it reinstall on the 16 gb ssd) He reinstalled apparently on the 4gb ssd, and I said to myself good, this is ok, but just now I tried to install the language package, got the same problem, and also the ubuntu restricted extra package, again with the message that I should check my internet connection. In my firstt install I had as I said no such problem.
  I'll try to see if I can manage your fix, and would still and always appreciate any help. I am desperatly trying to learn, but I don't always have the time to spend hours on this.

---

### Post by CROLMAC on 2010-08-09
I tried to copy paste your code and got 
    synaptic: no process found
  should I have paste line after line? anti-geek and nOOb alert

---

### Post by Quackers on 2010-08-09
Yes, line by line

---

### Post by CROLMAC on 2010-08-09
pasted the first line and got "no process found"..

---

### Post by stoneage on 2010-08-09
That is fine, it just means none of those things are running at the moment.

Go ahead and run the other commands.


It might also help to open System -> Adinistration -> Software Sources, uncheck the repositories for Ubuntu, and other software, then re-enable the ones you want to use(a bit like turning them off and back on again). :D


Maybe slightly off topic, but 4GB is a small partition, do any of the errors mention disk space?

---

### Post by CROLMAC on 2010-08-09
Hi, just got home, just tried your last solution, and still no go with the language update. I got this message for the 4 files that had to be fetched: W: Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-el-base/language-pack-el-base_10.04+20100422_all.deb](http://gr.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-el-base/language-pack-el-base_10.04+20100422_all.deb)
  Could not connect to gr.archive.ubuntu.com:80 (147.102.222.211). - connect (110: Connection timed out)
I think I will try the solutions proposed earlier, but what gets me is that when I had freshly installed lucid the 1st time everything worked ok. Why , since I reinstalled , are there problems? thanks

---

### Post by CROLMAC on 2010-08-09
linux18, I tried your lines of sudo as you said they obviously fixed and updated a coulpe of things, but failed to fetch a hell of a lot of files, if you care to see all this I've reserved it to show you, if it helps. but I still cannoyt reach my language... maybe I have to restart? ge back to you later, will try a few things, thanks for the tips. I swear that I Am trying to learn!

---

### Post by stoneage on 2010-08-09
CROLMAC I can't access that archive either, have you tried downloading from another server?
Open Software Sources and change the 'Download from' to some other server.

Also as a last resort you can find anything you need at [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by CROLMAC on 2010-08-09
well' I tried to change server, checked choose best server, it came up with ote ubuntu gr or something like that, went to the language center, and am allowed to choose only english....go figure, the server name suggests that it is the greek phone company's server... thought maybe you needed a laugh!

---

### Post by CROLMAC on 2010-08-09
funny thing, did that server fix, chose a greek server and all of a sudden I could use synaptic to apply greek packages.. IT WORKED!!! I'll try something else now, thanks

---

### Post by CROLMAC on 2010-08-09
Hey people, the server fix did the job!!the software center works also, I wanted to get extras to rip my cd's to mp3 for my phone, and the options are there in rythmbox's choices! as I am here, I am performing a little victory dance. I thank you for the opportunity to learn

---

### Post by stoneage on 2010-08-09
:d

:D

---

### Post by CROLMAC on 2010-08-26
> **linux18 said:**
> if " ping -c 1  [www.google.com](www.google.com) " returns anything other than unknown host, your connected to the internet.
then try ```
 
sudo killall synaptic && sudo killall aptitude && sudo killall mintinstall && sudo killall software-center 
sudo rm /var/lib/dpkg/lock && sudo rm /var/cache/apt/archives/lock && sudo rm /var/lib/apt/lists/partial/* && sudo rm /var/cache/apt/*.bin 
sudo dpkg --purge $(dpkg -l |grep  ^rc |awk '{print $2}' | tr '\012' ' ') 
sudo apt-get -f install && sudo apt-get clean && sudo apt-get autoclean 
sudo apt-get autoremove && sudo apt-get update && sudo apt-get --fix-broken upgrade 
 
``` 
to fix synaptic then  post back with the results


  I did this a while back, trying to fix a problem, but something else fixed it anyways ... but I was wondering, is it a one time thing? or does it continue to run and you have to kill it after?
  Just that I had gone to paris, put my photos as usual in my onboard sd, and as I am a little careful, in a usb, and when I checked them they were ok, removed the usb, deleted them from my camera memory, and put the memory in the camera. 
  Since then the camera can't see the memory, the photos disappeared from the sd, and in my panic I checked my usb from where they disappeared also, and then I remembered that I haden't deleted my trash, went there and they had disappeared too.
  I do remember checking everything twice as I don't really trust myself. What did I do? Could this be a coincidence? nothing else disappeared...and this is not the first time i do this. The saving I mean.. the losing is a first. Thanks for your time.

---

### Post by stoneage on 2010-08-27
Those commands would only affect the Synaptic Package Manager and they only run once when you hit enter. It has to be a coincidence. 

I can't say what happened to the photos, but I am sure those commands played no part in their disappearance.

I can only guess that maybe the camera memory card has failed and the write to the sd and usb only seemed to have succeeded, until you removed either the memory card, the usb or both. 
It does seem odd though, especially since you checked they were there. You could try mounting the camera memory to see if that problem was caused by an unclean shutdown - maybe the memory card can be saved, but otherwise I don't know what to recommend.

---

### Post by linux18 on 2010-08-27
ddrescue or photorec can get information from a memory card after it's been erased

---

### Post by CROLMAC on 2010-08-31
thanks, ithink 
i will leave that to my personal house geek...take care

---

