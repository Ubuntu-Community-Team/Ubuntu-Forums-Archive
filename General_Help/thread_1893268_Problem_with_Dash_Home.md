---
title: "Problem with Dash Home"
date: 2011-12-09
forum: General Help
---

### Post by agamjain on 2011-12-09
I am currently using Ubuntu 11.10 edition with Unity desktop. After the last update, I am having trouble accessing my applications. I click on the Dash Home and then I try to search for some application, but it does not return any results. Also, under 'More applications' or 'Internet Applications' I can see nothing. Can you please advise how I can resolve this?

---

### Post by agamjain on 2011-12-10
Now even my Ubuntu Software Center won't open up.

---

### Post by Dlambert on 2011-12-10
Sounds almost like a corrupted install, maybe try reinstalling with your PC hooked up to the internet to download the updates.

---

### Post by agamjain on 2011-12-10
But it was working for me till now. It was only after I installed the latest updates that this happened. Before this it was ok. Is there any way I could do it without having to do a reinstall?

---

### Post by hansdown on 2011-12-10
Hi, agamjain.

I just did the update, and can confirm this.

A bug report is necessary.

Please don't re-install.

---

### Post by agamjain on 2011-12-10
Can you tell me how to do that? Is it happening to you as well?

---

### Post by wildmanne39 on 2011-12-10
Hi, that happened to me two days ago, I could not get synaptic open or install with the terminal and nothing was running right, I waited 24 hours and another update came out that fixed it, but I think I just got lucky, I was just about to reinstall completely when the update came out.

---

### Post by agamjain on 2011-12-10
Should I be waiting for an update then?

---

### Post by hansdown on 2011-12-10
> **agamjain said:**
> Should I be waiting for an update then?

Yes.

---

### Post by agamjain on 2011-12-10
Thanks. I will not be reinstalling my distro for the moment and wait for the update. In the meantime, if anybody has any ideas how to get around this please let me know.

---

### Post by wildmanne39 on 2011-12-10
Hi, you can open a terminal ctrl+alt+t then install synaptic.
```
sudo apt-get install synaptic
```
then open it and click on edit, fix broken packages and see if there are any packages that can be fixed.

If not you can wait a little while and see if the next update fixes your issues or if you file a bug report wait and see if they have a fix for you.

You can open synaptic by running ```
gksu synaptic
``` in the terminal.
Thank you

---

### Post by lolpenguin on 2011-12-10
Check if unity-applications-lens/unity-*-lens is running.

---

### Post by agamjain on 2011-12-10
> **wildmanne39 said:**
> Hi, you can open a terminal ctrl+alt+t then install synaptic.
```
sudo apt-get install synaptic
```then open it and click on edit, fix broken packages and see if there are any packages that can be fixed.

If not you can wait a little while and see if the next update fixes your issues or if you file a bug report wait and see if they have a fix for you.

You can open synaptic by running ```
gksu synaptic
``` in the terminal.
Thank you
There are no broken packages to be fixed. I checked in the Synaptic Package Manager.

---

### Post by agamjain on 2011-12-10
> **lolpenguin said:**
> Check if unity-applications-lens/unity-*-lens is running.
Can you give me the command that I can type into the terminal to check that?

---

### Post by XtraFear on 2011-12-10
I'm also having trouble with the new update... the search isn't working, and Unity doesn't work... but Unity 2D does.

EDIT:  The search works occasionally... :/

---

### Post by agamjain on 2011-12-10
> **XtraFear said:**
> I'm also having trouble with the new update... the search isn't working, and Unity doesn't work... but Unity 2D does.

EDIT:  The search works occasionally... :/
My search is not working at all. And I do have the latest updates for Ubuntu. I hope a fix is released for this soon and Unity starts working again.

---

### Post by pretty_whistle on 2011-12-10
[SIZE=3]Hey everyone,

Hansdown, when did you get updated and have it backfire?  And did you use update manager to get updated?

I'm just wondering because I've used update manager just now and it's found about 8 since the last time ran it and that was 18 hours ago.  I'm chicken to install what it's found.  Maybe the ones it's offering aren't the cause because it was earlier ones that were the culprits in your system.

Same question for the rest of you who got a bad update.  When did you look for updates and did you use update manager?




[/SIZE]

---

### Post by pretty_whistle on 2011-12-10
[SIZE=3]What type of updates are the bad ones?  Security updates or recommended updates?[/SIZE]  [SIZE=3]Or both?[/SIZE]

---

### Post by wildmanne39 on 2011-12-10
Hi, I am not sure which updates broke my system it was about three or four days ago now.

There were several that night I read each one but I do not remember what they were and the only way to know which one caused the problem would have been for me to install them one at a time.
Thanks

---

### Post by pretty_whistle on 2011-12-10
> **wildmanne39 said:**
> Hi, I am not sure which updates broke my system it was about three or 4 days ago now.

There were several that night I read each one but I do not remember what they were and the only way to know which one caused the problem would have been for me to install them one at a time.
Thanks
Ok.

I'm trying to figure out if the list of 7 recommended updates it found for me this morning has the bad one(s) in the list.  Hard saying....

I wonder what I should do with it.  For now I've changed the setting to not search for recommended updates (it's mostly kernel updates in the list).

---

### Post by wildmanne39 on 2011-12-10
Hi, the updates today work just fine on my computer it was updates from three or four days ago that broke mine so you should be safe.
Thanks

---

### Post by pretty_whistle on 2011-12-10
> **wildmanne39 said:**
> Hi, the updates today work just fine on my computer it was updates from three or four days ago that broke mine so you should be safe.
Thanks
Oh.

That's good news.

Thanx.

---

### Post by Dlambert on 2011-12-12
I also had this problem!, but a reboot fixed it, and I have not been able to recreate it. I'm glad you didn't reinstall like I said!

---

### Post by agamjain on 2011-12-14
I have tried everything and it is not solving the issue with me. I installed the latest updates, tried restarting my laptop a couple of times, also tried Ubuntu 2D but to no avail. I do not know the exact package name so am unable to report the bug as well. What shall I do?

---

