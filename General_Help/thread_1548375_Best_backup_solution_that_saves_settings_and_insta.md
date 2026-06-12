---
title: "Best backup solution that saves settings and installed packages &amp; scripts"
date: 2010-08-08
forum: General Help
---

### Post by Rubicon421 on 2010-08-08
What is the best back up solution for saving all your settings, installed packages, added repos and ATP lines, scripts, tweaks, etc...? 

I am pretty good about keeping personal files backed up and I have all the really important ones in Dropbox so I don't need to back up the whole drive, just the things I have added to the OS since installing. 

Basically, I'm looking for a way to save these settings so that if I had to reinstall Ubuntu, I could do it from the disc then in one step, restore all my settings, repos, ATPs, scripts, etc...

If I saved my home folder to another disk then used a liveCD to over write the new home folder after a reinstall would that do it?

---

### Post by HermanAB on 2010-08-08
When you install ALWAYS make a /home partition.  When you re-install, simply DON'T format /home.  Similarly, to make a backup, save the /home partition.

---

### Post by Rubicon421 on 2010-08-08
I did make a separate home partition. I just wasn't sure if that one folder would contain all of the things I was wanting to back up. So if I reinstalled and didn't format the home folder then everything I am wanting to back up would still be there and work right after the install?

---

### Post by ajgreeny on 2010-08-08
> **Rubicon421 said:**
> I did make a separate home partition. I just wasn't sure if that one folder would contain all of the things I was wanting to back up. So if I reinstalled and didn't format the home folder then everything I am wanting to back up would still be there and work right after the install?
Almost, yes.

Most of your configuration is in hidden folders and files in your home partition, but there are some others in /etc and /usr.  However, as long as you have /home fully backed up, including the hidden bits, you will have almost everything that is really important to you.

If you want to keep all your installed programs and packages keep a backup of /var/cache/apt/archives as well, or use aptoncd to make an iso file every so often. Alternatively use clonezilla to clone your whole disk.

---

### Post by Vaphell on 2010-08-08
you can also go to synaptic and save the list of installed packages (remember to check  'full state not changes' in the save dialog). Preview it to see if it contains the list and later you can use synaptic to read that file and install everything automatically. It won't work with stuff you installed manually from source but 99% of the work will be done. Don't forget to copy repo list if you have some PPAs added.

---

### Post by Rubicon421 on 2010-08-08
Great suggestions! I'm going to use all of them. 

What exactly would I be loosing if I don't back up the etc and usr folders though?

---

### Post by ajgreeny on 2010-08-08
> **Rubicon421 said:**
> Great suggestions! I'm going to use all of them. 

What exactly would I be loosing if I don't back up the etc and usr folders though?
Very little, and I have never bothered to keep anything other than /home, and the aptoncd iso files which are already in home.

It is now so quick to install from a clean start that I think updating is hardly worth the trouble it seems to cause, particularly when there are a number of PPAs enabled.

---

### Post by erkorb on 2011-03-01
I just started using CrashPlan.  Works nicely and not too much load on the system.

---

