---
title: "Ubuntu is running slow"
date: 2009-07-16
forum: General Help
---

### Post by RealG187 on 2009-07-16
Lately my Ubuntu is running slow. It takes forever to log in and now sometimes it says "xx Gnome Panel cannot be loaded, would you like to delete it from the configuration?" I restart and it's fine but it takes forever.

I see my Firefox windows turning gray more (as that's what Ubuntu does when a program is not responding).

I have 9.04 and keep current with updates (I never did before). How can I make it fast again short of reinstalling.

And if I did have to reinstall is there a way I could do that without losing my (backed up) home folder?

---

### Post by chriskin on 2009-07-16
> **RealG187 said:**
> Lately my Ubuntu is running slow. It takes forever to log in and now sometimes it says "xx Gnome Panel cannot be loaded, would you like to delete it from the configuration?" I restart and it's fine but it takes forever.

I see my Firefox windows turning gray more (as that's what Ubuntu does when a program is not responding).

I have 9.04 and keep current with updates (I never did before). How can I make it fast again short of reinstalling.

And if I did have to reinstall is there a way I could do that without losing my (backed up) home folder?


can you check the system monitor to tell us what uses up your cpu and/or ram?

---

### Post by NightwishFan on 2009-07-16
Try the top command to see what is slow. Open a terminal and type:
```
top
```
It is sorted by CPU usage.

You can reset all gconf (GNOME) preferences, but I would back up all of your email first. I am not sure (but i doubt) if evolution would delete it. This may resolve some problems, however you will have to set up all gconf compatible applications again. 

To reset all GNOME settings, log out, then go in to a virtual terminal by pressing CTRL+ALT+F5. Type this command:

```
gconftool --recursive-unset /
```

---

### Post by RealG187 on 2009-07-16
I don't want to reset all my panels.

How exactly would I use System Monitor, I can post a screenshot of it if that helps, which tab of it would help?

Something I remembered is I recenlty set VMWare to start a virtual machine up with my system so maybe resources being used to start it are being used and therefore not being used during the initial startup.

---

### Post by chriskin on 2009-07-17
since you already know the problem, fix it, don't have the Virtual Machine start with your computer. virtual machines are resource holes, stealing your ram and cpu :P

as for the system monitor, that would be the processes tab, where it shows who uses what ram and cpu. find the one the uses the most, and you have found your problem.

---

### Post by RealG187 on 2009-07-17
I closed the VM and it seems like my system is running faster now.

I set it to wait 120 seconds instead of the 30 I had it set to. I think it was 120 but I lowered it, but now I see why it was higher.

I'll see how my system goes.

---

