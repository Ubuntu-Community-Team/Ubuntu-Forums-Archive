---
title: "System Monitor opens whenever pressing the Delete button."
date: 2012-01-07
forum: General Help
---

### Post by shayli147 on 2012-01-07
Hello

This is a thread I opened in launchpad, no answer yet, so i wish to try here as well.

I use ubuntu 10.04.
I opened once the System Monitor in the normal way: System > Administration > System Monitor, and since then (I don't know why) it opens after I press the Delete button on my keyboard. I see no logic in it, since I have done nothing in this System Monitor, anyways I'm not an expert...

My question is how to disable the Delete button from opening the System Monitor? (It is quite annoying)

I tried to add a shortcut in System > Preferences > Keyboard Shortcuts maybe to confuse it, but couldn't confuse a computer at the end... plus all I've found in the search I have done in Google was about creating the windows shortcut to open the "linux task manager" as the "System Monitor" was nicked there...

In hope you could provide me the help I need,
Thanks ahead,

Shay

---

### Post by LinuxFan999 on 2012-01-07
Try removing and reinstalling System Monitor
 
```
sudo apt-get remove gnome-system-monitor
sudo apt-get update
sudo apt-get install gnome-system-monitor
```
 
Removing and reinstalling system monitor can also be done through the Software Center or Synaptic.

---

### Post by shayli147 on 2012-01-07
Thank you for your fast reply

I removed and re-installed through Terminal, the Delete button still opened the System Monitor afterwards.
I removed it using the Synaptic and tried to use the Delete button when System Monitor isn't installed, but then it didn't even respond, it does nothing now when the System Monitor isn't installed...

Could it be something with the keyboard's settings, and if so, how can it be changed?
It cannot be done through System > Preferences > Keyboard, as far as I could see...

Thank you

---

### Post by blackbird34 on 2012-01-07
> **LinuxFan999 said:**
> Try removing and reinstalling System Monitor
 
```
sudo apt-get remove gnome-system-monitor
sudo apt-get update
sudo apt-get install gnome-system-monitor
```Removing and reinstalling system monitor can also be done through the Software Center or Synaptic.

Try purging and reinstalling System Monitor
 
```
sudo apt-get purge gnome-system-monitor
sudo apt-get update
sudo apt-get install gnome-system-monitor
```

...Which should remove any odd settings.

---

### Post by shayli147 on 2012-01-07
> **blackbird34 said:**
> Try purging and reinstalling System Monitor
 
```
sudo apt-get purge gnome-system-monitor
sudo apt-get update
sudo apt-get install gnome-system-monitor
```

...Which should remove any odd settings.

Thank you,
I was trying it a moment ago, but doesn't seem to solve the problem yet. :(
Can I do something to help you to understand the situation better? Well, it is a weird one...

---

### Post by shayli147 on 2012-01-25
I'm sorry to rise this thread again, since this problem is not solved I still wish to find a solution :)

Is there a possibility to manually define the keys action on the keyboard somehow?
Maybe that would help.

Thanks in advance :)

---

