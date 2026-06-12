---
title: "apt-get install running old package"
date: 2009-10-17
forum: General Help
---

### Post by tzavaleta on 2009-10-17
Everytime I try to run any installations it hangs with a configuration request for noip2:
>Setting up noip2 (2.1.9-1) ...
>
>Auto configuration for Linux client of no-ip.com.
>
>1 host and 1 group are registered to this account.
>Do you wish to have them all updated?[N] (y/N)

No matter what I select it stays here until I kill the noip2 process.  Noip is actually working fine but I don't know why this gets triggered when I install unrelated packages (today it was Bugzilla).  

How can I remove noip2 from the installation dependency?  Is there someting the installer is looking for that says this is incomplete and must try again? 

thanks

---

### Post by eric3_14159 on 2009-11-09
That is weird. I would try uninstalling and reinstalling noip2, and if that doesn't work then using "apt-get purge noip2" before reinstalling, to try to remove all traces of it.

---

### Post by joeinbend on 2009-11-09
I have the same issue, and I have purged noip2 (sudo apt-get purge noip2) and gone through all the preventative stuff afterward like (sudo apt-get autoremove and autoclean) rebooted, then tried to re-install it, but I get stuck at the same point during the dpkg install. I'm running v9.04 server.

The PITA part of this package is it doesnt have just a text-based .conf file, the program itself creates the .conf, which is encrypted (hashed? i dunno..) because it contains password info, i assume. arg.

---

### Post by joeinbend on 2009-11-09
I figured this one out, at least as it applies to Ubuntu Server v9.04. Seems to me that the package needs to be updated in the repo's. Here's what I did:

- Install the package from the repo's (sudo apt-get install noip2)
- During the install if it hangs up on you, just ctrl+C out of it.
- download the newer version from the no-ip website (2.1.9)
- untar it, sudo make and sudo make install
- Now set the chmod and chown on the config file, as stated in the "README.FIRST" file. 

After that it should be working correctly. I was able to reboot the server, and it properly updated the IP on my no-ip account, and (I set the refresh interval to 5 minutes), I rebooted my modem to get a new IP, and the no-ip service successfully detected the new IP and updated it within 5 minutes as scheduled. If you have trouble still, post here I'll see if I can help.

I'm a "hack" linux guy, so I'm pretty positive this is not the correct way to do it, probably the new client should be packaged into a .deb first so the kernel recognizes it, but this worked. If anyone has the correct method based on what I did, let me know!!

---

