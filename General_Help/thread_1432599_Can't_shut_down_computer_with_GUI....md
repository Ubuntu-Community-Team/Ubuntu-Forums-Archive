---
title: "Can't shut down computer with GUI..."
date: 2010-03-17
forum: General Help
---

### Post by adamkleiner on 2010-03-17
OK, so basically my problem is that I can't log out, shut down, or restart my computer through the GUI. The thing is, it *used* to work. Any suggestions or possible workarounds? :confused:
 
**Note:** this started happening right after I put in the lock / logout widget, but it's really a pain to have to go through the Kickoff menu to lock the screen each time, and leaving my files, online accounts, and what's on my screen open to anyone who wants to snoop is not an option. I may have to just suck it up and lock the screen the old-fashioned way, but *only* as a last resort.
 
**Configuration:** An older Gateway (idk the exact specs) desktop machine with Windows XP and Kubuntu 9.10 Karmic (dual-boot)

---

### Post by d3v1150m471c on 2010-03-17
Sounds like your hardware is conflicting with software. Any recent changes or updates?

---

### Post by adamkleiner on 2010-03-17
> **d3v1150m471c said:**
> Sounds like your hardware is conflicting with software. Any recent changes or updates?
Yes, I downloaded some bug and security updates today (by clicking on a pop-up dialog) and added the "lock/logout widget" the other day. Other than that, it's a fresh install, and all of my important stuff is on my primary computer running Windows 7. Would a fresh reinstall fix it? I know it's drastic, but since I don't like holding down the power button and forcing a shutdown, and since it's a serious problem, I would do it.

---

### Post by Ozymandias_117 on 2010-03-18
Have you tried using the command line?
```
sudo shutdown -h now
```
shuts down
```
sudo shutdown -r now
```
restarts

---

### Post by d3v1150m471c on 2010-03-18
Boot to recovery mode and repair broken packages

---

### Post by adamkleiner on 2010-03-18
> **Ozymandias_117 said:**
> Have you tried using the command line?
```
sudo shutdown -h now
```
shuts down
```
sudo shutdown -r now
```
restarts
Thanks! I have *very* little experience with bash, but was able to figure it out because I have heard of "sudo" before, and it needed admin privileges. Thanks for pointing that out!

---

### Post by Ozymandias_117 on 2010-03-18
> **adamkleiner said:**
> Thanks! I have *very* little experience with bash, but was able to figure it out because I have heard of "sudo" before, and it needed admin privileges. Thanks for pointing that out!

Sorry, I'm not quite sure, are you saying it DID shut down using those commands? :P You said your problem was shutting down with GUI so I was trying to figure out if it's a problem with the shutdown GUI or something else :)

---

### Post by adamkleiner on 2010-03-18
> **Ozymandias_117 said:**
> Sorry, I'm not quite sure, are you saying it DID shut down using those commands? :P You said your problem was shutting down with GUI so I was trying to figure out if it's a problem with the shutdown GUI or something else :)
It looked like, for some reason, it wants admin privileges to shut down! When I entered those commands, it said that I needed admin rights, so I tried again with the "sudo" prefix, and it worked (after I entered my password to run the command as root)!

---

