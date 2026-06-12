---
title: "Unable to boot after Installation over LAN"
date: 2009-07-18
forum: General Help
---

### Post by Tyrsius on 2009-07-18
I have never done an installation over LAN, and so I realize this is probably my own fault, but I do not know what to do to fix the issue. First, the details:

I used UNetbootin from a Windows XP installation to start an installation over LAN. I used the Ubuntu ftp for this. I have never seen the installer that was used, but the options were very familiar. After installing the core system it asked what I wanted to install, and I chose Ubuntu Desktop (thinking this would be the same thing as other Ubuntu installations I have done from CD).

After the installation was finished I encountered an error on booting "no resume image found" and it booted to a terminal, instead of the GUI desktop. I searched around and found a suggestion to apt-get install GDM. After doing this, I come to the normal login screen after booting. I enter the login credentials and get this error

Xsession: Warning xrdb command not found. X Resources not merged.

After this, it returns to the terminal. I have tried startx, but am told I am not allowed to access X server. I have tried repairing broken packages from the recovery boot, but this does not resolve the issue.

I want to get to a standard installation of Ubuntu Desktop, the same you would have after running an installation from the standard .iso. If I need to re-install, that is fine, but I clearly did something wrong so please provide instructions for the correct LAN installation method.

BTW: The reason for the LAN method is because the cd-rom is not working, and the BIOS will not boot from USB. LAN is the only method I have available.

---

### Post by Tyrsius on 2009-07-19
After more investigation it appears ubuntu desktop simply didn't get installed. I have the core system (though I am not entirely sure that that means) but nearly no applications installed. This should mean that I can still install Ubuntu Desktop on top of the ubuntu installation already in place though, right?

I used UNetbootin to get this first netboot to run, and I must have not hit the right option to install ubuntu desktop (I thought I did). Somebody has to know how to run a netboot from the terminal. The tutorials I have found,like the one [here]("https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet") tell me to download something and save it to /boot. I don't know how to do this from the terminal.

If someone could give me this one step I could manage the rest.

Edit: Did more looking, seems the wget command is what I am after, but I haven't been able to get the syntax right. I need to download the entire directory of [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/) to /boot (I should probably make a new folder to put this stuff in). Unfortunately just using "wget http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/" gives me an error about the index.html. Clearly I am doing something wrong, but after looking through about 3 articles and the wget manual I haven't been able to figure out what the syntax should look like.

---

