---
title: "How to restore Ubuntu from LiveCD or Rescue"
date: 2006-04-02
forum: General Help
---

### Post by Dafydd on 2006-04-02
Hi

After trying to install webcams (motioneye and spacecam 120) I did something stupid with the modules. Previously Ubuntu would give me an error message with the meye (motioneye) module...

Now the modules for the mouse, wireless and sound don't appear to load.

How do I just reinstall the basic modules (not the system)? I've tried "sudo dpkg-reconfigure xserver-xorg" but to no avail. It gave me options etc to reconfigure but when I reboot there was still no working mouse and the ipw2200 modules was 'not found' when i did modprobe.

Anyone have any suggestions?

Cheers
Dafydd

---

### Post by mlalkaka on 2006-04-02
I don't know what you did exactly, but try tracing back the steps you did.
If you are thinking, "It's not that simple", then please provide more information; otherwise, no one will be able to solve your problem.

One way to go back to the original Ubuntu installation is possible if / and /home are two separate partitions. In this case, all you have to do is reinstall Ubuntu Linux on the / partition. All files and directories in /home will/should be unaffected.

[COLOR="Red"]**Disclaimer: Do not hold me responsible for any loss of critical data caused by following these instructions. I am no expert.**[/COLOR]Thank you :D.

---

