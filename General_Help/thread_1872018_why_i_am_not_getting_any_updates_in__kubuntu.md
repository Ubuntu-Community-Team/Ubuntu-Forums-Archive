---
title: "why i am not getting any updates in  kubuntu"
date: 2011-10-29
forum: General Help
---

### Post by mac4rfree on 2011-10-29
Hi Guys,

Earlier i was using Ubuntu for almost a year. I used to get updates on constant basis. Then i switched to Kubuntu.
But now i am not getting any notifications for Updates.

Can somebody tell me where i need to check for the updates.. (PS: i might have uninstalled it i don knw wat i was doin...)


Cheers!!!!!!

---

### Post by oldtimer7777 on 2011-10-29
> **mac4rfree said:**
> Hi Guys,

Earlier i was using Ubuntu for almost a year. I used to get updates on constant basis. Then i switched to Kubuntu.
But now i am not getting any notifications for Updates.

Can somebody tell me where i need to check for the updates.. (PS: i might have uninstalled it i don knw wat i was doin...)


Cheers!!!!!!

in terminal try running:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install kubuntu-desktop

---

### Post by mac4rfree on 2011-10-29
> **oldtimer7777 said:**
> in terminal try running:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install kubuntu-desktop
Yeah thanks!!!! it did update but i was looking for some graphic application where i can select which to update which not to...

---

### Post by oldtimer7777 on 2011-10-29
> **mac4rfree said:**
> Yeah thanks!!!! it did update but i was looking for some graphic application where i can select which to update which not to...

Use synaptic package manager:

sudo apt-get install synaptic 
sudo synaptic

You can change everything you like in there.

---

### Post by oldos2er on 2011-10-30
> **mac4rfree said:**
> Yeah thanks!!!! it did update but i was looking for some graphic application where i can select which to update which not to...

Muon package manager should've been installed with Kubuntu; or you can just use Synaptic as oldtimer7777 suggested.

There's also the System Settings, Software Management tool.

---

### Post by mister_playboy on 2011-11-05
I see the same issue... muon package manager runs daily and find updates just fine, but it doesn't display any notifications or tray icons that updates are available.

These notifications *are* enabled in the settings... :confused:

For now I'll just have remember to apply the updates manually every so often.

---

