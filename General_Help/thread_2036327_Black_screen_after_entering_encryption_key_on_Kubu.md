---
title: "Black screen after entering encryption key on Kubuntu 12.04"
date: 2012-08-01
forum: General Help
---

### Post by Kalantir on 2012-08-01
Yesterday I installed Kubuntu 12.04 with full disk encryption using the alternate install cd. After it installed/rebooted, I entered my encryption key, logged in, configured the system settings(but not anything which is remotely related to encryption or the login screen), unpacked the b43 wireless drivers into /lib/firmware, did a "sudo modprobe b43", and installed the following software using apt-get:

macchanger-gtk
gcc
g++
firefox

After installing that software, I rebooted my computer, entered my encryption key, and was greeted by a black screen (instead of the login screen).  I figured it was busy unencrypting/loading stuff so I let it sit for about 20 minutes while I made myself something to eat. When I came back, I found it was still at the black screen. I tried hitting ctrl-alt-f1 to get to a shell but it didn't work. Eventually I hit ctrl-alt-del which caused the Kubuntu gear to get displayed for a second or two before the computer rebooted.

What could be causing this black screen and how can I avoid this issue when I reinstall Kubuntu again? Please note that I want full disk encryption (not just the home folder).

Also, it may be worth mentioning that before this installation, I was running Kubuntu 12.04 with home folder encryption (installed from the live-cd) and it ran just fine (other than some minor issues which aren't relevant to this thread). Before reinstalling I ran Darik's Boot & Nuke to erase the contents of my hard drive.

Just for extra clarification:
1. Boot OS
2. Enter encryption key
3. Enter account username/password
4. You are now logged in

My problem appears to take place between steps 2 and 3.

Also, if it helps, I am using a Dell Latitude D620 Laptop.
I would be happy to provide any additional information you might find useful.

---

### Post by elmanuel on 2012-10-10
Have you figured this out yet?

I am seeing the exact same issue and am getting a little sick of rebooting until it works.

Thanks

---

