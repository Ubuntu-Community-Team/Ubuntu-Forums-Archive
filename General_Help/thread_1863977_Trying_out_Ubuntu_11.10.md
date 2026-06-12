---
title: "Trying out Ubuntu 11.10"
date: 2011-10-18
forum: General Help
---

### Post by lianazaman on 2011-10-18
Good day all :)

First time trying out Ubuntu 11.10, and noticed something:

1) In Unity, there is no power options like the performance modes. Is there any? I'm running on laptop and sometimes would like to change from power-saving to high performance.

2) Also in Unity,  I check on the Power options, I could not Suspend nor Hibernate. Only Shutdown or Do nothing. What should I do if I want to use Suspend and Hibernate, especially Hibernate?

3) I installed the Gnome-Shell, using
[PHP]sudo apt-get install gnome-shell[/PHP]and I logged in using the Gnome option instead of the Unity. However, I noticed there are somekind of 'buzz' display (the ones you get out of the broken tv, usually), and the text on my username and options become..weird.

For example:

Nor Liana Kamaruzzaman ->  or L  n    m  uzz   n
Log out                           ->  og  u 

Does anyone understand what problem this is, and can help shed some light to me? ^_^

---

### Post by 2F4U on 2011-10-18
Can you provide more details about your hardware? It could be a problem with the graphics driver, so it would be good if you could tell us what graphics driver you are currently using.

---

### Post by lianazaman on 2011-10-18
Well...if I remembered correctly:

ATI Radeon 3200 Graphics

I'm also currently using AMD Turion X2, 2.2 Ghz.

Does these help?

---

### Post by MonolithImmortal on 2011-10-18
Concerning the power options, if you want to pick power saving modes vs performance modes, I recommend installing Jupiter. You can get it from the webupd8 Jupiter ppa.

Just run:
[PHP]sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update && sudo apt-get install jupiter[/PHP]

[http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html](http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html)

Jupiter will also vastly improve your battery life. I assume you are running Ubuntu on a laptop?

---

### Post by lianazaman on 2011-10-18
Hm..okay! Will try, but maybe I should back up first, just in case :D. Will notify of the results!

---

### Post by lianazaman on 2011-10-19
Jupiter:

Installed it, using the 'sudo apt' method, but I don't see any changes or addition though, not at the software center nor on the tray. Where is the performance mode, or what should I expect exactly after I installed it?

Gnome Shell:

I guessed mine is not meant to have Gnome  Shell, since I removed it and re-install (first time using sudo, second time using software center), and both looks, er...words with missing pieces? o.O

---

### Post by Quincy5 on 2011-10-21
I have no Hibernate/Suspend options either. Any ideas on how to get them back?

---

### Post by lianazaman on 2011-10-21
> **Quincy5 said:**
> I have no Hibernate/Suspend options either. Any ideas on how to get them back?


Hey quincy, I don't know what's the problem is, so I backup the important files first. Then I reinstalled. Funnily, now they are always available. At first I thought it's the updates, but I updated and it's still okay.  So it must be that my self-installed apps or I screwed up at some point with the settings.

Not much help, but a suggestion. In short, backup important, reinstall (check during the live cd, do you have the suspend and hibernate options? If not, then it's your comp settings. If yes, then that's mean we did the problem)

---

### Post by Quincy5 on 2011-10-21
I am not going to do anything about it, as switching from Unity to classic Gnome gave me the old shut down dialog back, with the hibernate and suspend buttons. It is a work pc and I don't have time to do a complete reinstall and I am used to Gnome anyhow. I forgot to mention the problem actually started after upgrading from 11.04 to 11.10.

---

### Post by lianazaman on 2011-10-21
Woh...cool then :). My Gnome Shell's acting pretty weird, with this 'buzz' before the desktop ( or do you call it shell?) come to view, and some parts on the tray have choppy titles (missing alphabets and all). I end up using the gnome classic, unity 2d, and lately having fun with xubuntu desktop (lighter on the performance, for me that is).

---

