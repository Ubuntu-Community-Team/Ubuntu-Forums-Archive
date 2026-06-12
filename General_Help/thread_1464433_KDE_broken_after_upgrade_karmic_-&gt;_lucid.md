---
title: "KDE broken after upgrade karmic -&gt; lucid"
date: 2010-04-28
forum: General Help
---

### Post by bsphere on 2010-04-28
Hi,

After upgrading my 64bit 9.10 install to lucid, KDE went poof. I am presented with the login screen, and after supplying my credentials the screen goes black and all I am left with is a mouse pointer.

According to ps kded4 is dead (zombie). kdm.log also indicates a problem with ibus. I installed the "ibus" pkg, but didn't resolve it. Attached is an excerpt of my kdm.log, I can't really find useful information in syslog/dmesg/messages. The system is up-to-date and I've tried starting with a clean user account as well as removing the .kde directory.

Any ideas?

---

### Post by sandyd on 2010-04-28
> **bsphere said:**
> Hi,

After upgrading my 64bit 9.10 install to lucid, KDE went poof. I am presented with the login screen, and after supplying my credentials the screen goes black and all I am left with is a mouse pointer.

According to ps kded4 is dead (zombie). kdm.log also indicates a problem with ibus. I installed the "ibus" pkg, but didn't resolve it. Attached is an excerpt of my kdm.log, I can't really find useful information in syslog/dmesg/messages.

Any ideas?

try```
sudo apt-get update && sudo apt-get upgrade && rm -rf ~/.kde
```

---

### Post by bsphere on 2010-04-28
Thanks, in fact I had already done that, sorry for not including it. after dist-upgrade I checked to make sure there weren't any updates left. Clean .kde didn't make any difference :|

---

### Post by dren.dk#1 on 2010-04-30
I have what seems to be exactly the same problem, I even tried creating a completely new user, but that user also gets a black screen with no background or menu upon login.

The upgrader seems to have forgotten to install plasma, I ran this and restarted kdm and everything was back to normal:

sudo apt-get install kdebase-workspace

---

### Post by bsphere on 2010-04-30
Thanks a lot, this package was indeed missing. I installed it remotely, I will let you know if it works.

Unfortunately I also need to address an issue with statd dying on bootup first, because NFS mounts are not handled correctly since the upgrade. But this is off-topic.

Thanks again.

---

### Post by kooldino on 2010-04-30
> **dren.dk#1 said:**
> I have what seems to be exactly the same problem, I even tried creating a completely new user, but that user also gets a black screen with no background or menu upon login.

The upgrader seems to have forgotten to install plasma, I ran this and restarted kdm and everything was back to normal:

sudo apt-get install kdebase-workspace

This worked for me too, thanks!

Can't believe such an obvious problem went undetected.  :confused:

---

### Post by myjess on 2010-05-01
ditto on my netbook.

Somone try this please, just in case it is my netbook apt lists.

apt-get install kubuntu-desktop

I get ERR.


anyone else get that?

ta.

---

### Post by randyr505 on 2010-05-04
I have a similar problem. I did an upgrade from Karmic to Lucid 64bit. Now when I login to KDE I get a black screen, a few flashes then back to the login prompt. I can however login to failsafe mode. I checked and the kdebase-workspace was already up to date. I too had the ibus errors in kdm.log. I did an apt-get install ibus. I then restarted X and had the same problem. After looking more in the kdm.log I noticed it was complaining about not finding a compatible NVIDIA X driver. I recall the upgrade wanting to remove some nvidia packages. I said yes assuming the upgrade new what it was doing and had packages that would work with my graphics card. I also remember seeing something about some kernel sources not being available to build something. It may have been the nvidia drivers. Any ideas?

Thanks,

---

### Post by GDR! on 2010-05-05
Any ideas on this? I tried all solutions from these forums, from reinstalling nvidia packages to installing kdebase and kubuntu-desktop to deleting xorg.conf. This does not change the fact that I'm unable to use my main computer for three days because it throws me back 2 seconds after logging in.

---

### Post by bsphere on 2010-05-10
> **dren.dk#1 said:**
> I have what seems to be exactly the same problem, I even tried creating a completely new user, but that user also gets a black screen with no background or menu upon login.

The upgrader seems to have forgotten to install plasma, I ran this and restarted kdm and everything was back to normal:

sudo apt-get install kdebase-workspace
Thanks a lot this fixed it. :)

---

### Post by kweetniet on 2010-06-08
kweetniet=dontknow

I had the same: after upgrade 9.04 --> 9.10 blackscreen , was able to start kdm

but no internet no laptop mousepad and after restart i had to start kdm manually

I have no clue

---

### Post by bsphere on 2010-06-08
I don't think that's related. I also had a problem when upgrading 9.04 to 9.10 but the solution was completely different. Perhaps it would be best to either try upgrading to 10.04 or start a separate thread.

---

### Post by kweetniet on 2010-06-09
> **bsphere said:**
> I don't think that's related. I also had a problem when upgrading 9.04 to 9.10 but the solution was completely different. Perhaps it would be best to either try upgrading to 10.04 or start a separate thread.


Please help me out 

I can start my laptop
but only by typing kdm after a badstartup
after that KDE starts but no connection with internet: wired or wireless or VPN, no mousepad either
can i make a live cd with my desktop etc
what about my data =Save?



i'm a wannabe but still thinking as a newbe

---

### Post by Fatboy Snarky on 2010-07-18
THANKS!

I also had to install kdebase-workspace manually.

You guys are priceless!

(But, how come this isn't fixed in the Ubuntu packages?)

---

