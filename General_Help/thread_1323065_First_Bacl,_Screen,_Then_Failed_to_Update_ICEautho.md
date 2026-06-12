---
title: "First Bacl, Screen, Then Failed to Update ICEauthority, The Device Full"
date: 2009-11-11
forum: General Help
---

### Post by harryhoudini66 on 2009-11-11
Hello everyone,

Been using Ubuntu as my main OS for about 6 months now. Yesterday when I restarted I could no longer get a display. After the login for user and password, I would get a black screen with a white cursor. I could move the cursor around. I looked through the forums and the solutions posted did not work. I ended up logging on to Failsafe GNOME.

This then displayed an error about being unable to update the ICEauthority file. Found a few threads on how to fix it and nothing worked. Changed permissions and stuff. I then saw the update manager came up and asked if I wanted to update. I said yes but it said device was full.

I have a 250 gig hard drive and am only using about 40 gigs as far as I can tell. Anyways, I decided to delete some videos from my home folder and this freed up some space. I was then able to login to failsafe GNOME without getting the ICEauthority error. I then decided to go back to regular GNOME and see if that worked. Well I was able to login but Compiz was no longer enabled and the Nvidia driver did not load. I reactivated and all is well now. Well I also had to recreate my Mozilla profile.

I am now at the following problems. I had setup simple back and it looks like that may have been the culprit. I since have removed it but cannot access the backup folder so I can delete it. Any ideas on how to accomplish that. Says I dont have permission. I tried to login as root but then says the folder does not exist. This is weird because the dir shows it does. I am a newb so any ideas would be helpful.

Last issue, I know have a folder called Tmpp50RPo in my home folder. I am sure this was created when I logged in to failsafe GNOME. How do I delete that one as well? I tried to by right-clicking and it says I dont have permission. Also has a lock on it.

---

### Post by cariboo on 2009-11-11
Start nautilus as root, press Alt-F2 and type:

```
gksudo nautilus
```

This will start the file manager as root, you can then delete the file. Make sure you clean out root's trash after removing the file.

---

### Post by harryhoudini66 on 2009-11-11
Thank you very much. That allowed me to delete the files. Just one question. How do I empty the trash?

---

### Post by harryhoudini66 on 2009-11-11
Okay, I think I found out. I ran the command you told me and then navigated to

home/harryhoudini66/.local/share/Trash and deleted them from there.

I also went to /root/.local/share/Trash

When I open up the Trash though under my user it still shows the items in there. I try to delete them again and then it says they dont exists. FUnny how Simple Backup is what caused all these problems. It was meant to save me when I did have a problem.

---

### Post by harryhoudini66 on 2009-11-11
After reboot, the trash was empty. I now have 40 gigs used out of 250. 

Thank you so much for your help. You are a lifesaver. I was getting ready to reinstall. I knew Ubuntu was not like Windows in which bigger problems required reinstalling. I was just running out of patience. 

You're the best.

---

