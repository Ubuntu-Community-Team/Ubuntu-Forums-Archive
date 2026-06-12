---
title: "Wireless/NetworkManager won't auto-connect!"
date: 2012-06-08
forum: General Help
---

### Post by carrett on 2012-06-08
Hello,

I have a WPA router. I can connect fine using the default tool in the top panel (nm-applet, I think). However, even after editing the connection in settings, it will not auto-connect. Instead, every time I reconnect/reboot, a new profile is created and I must re-enter the wireless password. Any clues why NetworkManager is not using the saved profile to auto-connect? I have seriously over 20 profiles in /etc/NetworkManager/system-connections (yes, I've tried deleting all profiles (via GUI and CLI) and starting over). Also, at some point I would like to be able to use static IP, but if profiles can't be saved I'm SOL.

I know I could use WICD et al but if there's an easy fix to make the default work, that would be swell.

Thanks folks!

---

### Post by carrett on 2012-06-09
Bump #1.

---

### Post by steeldriver on 2012-06-09
what happens when you try to save the connection? does it ask for authentication (sudo)? does it actually create a new file in the /etc/NetworkManager/system-connections/ directory?

---

### Post by carrett on 2012-06-09
Hi, thanks for answering!

It does not ask me to authenticate when I check the boxes for "Connect automatically" and "Available to all users." In fact I am never asked for my keyring password or to authenticate as root/sudo/whatever. The only password I am asked for is the wireless password, which I have to enter every time I select my wireless AP from the applet (which I must do every time I want to connect to it, auto-connect is not happening). And yet, /etc/NetworkManager/system-connections now contains 12 profiles (all of which say the same thing).

I don't know which behavior I'm most disturbed by, the lack of fucntionality or the writing to a supposedly root-owned folder without asking permission. Happy to furnish further details.

---

### Post by carrett on 2012-06-09
Bump #2

---

### Post by carrett on 2012-06-10
Bump #3. Willing to try anything/provide any info.

---

### Post by carrett on 2012-06-11
One last bump. Pretty desperate here :(

---

### Post by steeldriver on 2012-06-11
beyond deleting the system-connections, have you tried just purging and reinstalling the network-manager package? 

I'm all in favor of diagnosing things properly but sometimes it's just not worth the effort

---

### Post by carrett on 2012-06-11
I'll try that when I get home. I guess I'll just use /etc/network/interfaces or wicd, which I've never had problems with. It's just a bummer to not be able to use the flashy option Ubuntu wants you to use.

---

### Post by steeldriver on 2012-06-11
I think if it was a widespread problem there'd be plenty of chatter about it - which leads us to something being screwy in your particular config - and hence why a package reinstall might be in order

I've got 3 machines running network-manager and they all handle automatic connections under WPA just fine

---

### Post by carrett on 2012-06-11
Purging and reinstalling worked. There are a couple of things I can think of as possible culprits:

1. I added the connection during installation.
2. The connection was added automatically as a result of my using the applet and selecting my wireless AP from the list of available ones. After purging I went through system settings and manually added the connection first.

That being said, one shouldn't have to be so careful. Further, I find it troubling that at no point in modifying the system network settings was I ever asked for a password. Users should be asked to authenticate when writing files to an /etc subdirectory, IMHO.

Anyway it works now. Horray. I'm still interested in researching into the matter because I had the same problem on Debian testing (and even Debian Developers were scratching their heads). I still believe there's some funkiness with N-M, permissions, and or keyrings.

Thanks for the help!

---

