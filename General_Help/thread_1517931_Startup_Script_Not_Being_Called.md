---
title: "Startup Script Not Being Called"
date: 2010-06-25
forum: General Help
---

### Post by AmishDave on 2010-06-25
I'm setting up an Ubuntu 10.04 machine with the sole purpose being to function as a vpn server.

I got openvpn set up but the startup script doesn't appear to be called on bootup even though it is does appear in the rcX.d directories and the openvpn script is in /etc/init.d and is executable and belongs to root:root.

I tried running "update-rc.d -f openvpn remove" and "update-rc.d openvpn defaults" on the offchance something went wrong when it was first added to the startup links.

If anyone has any idea why this isn't working please let me know.

---

### Post by Brandon Williams on 2010-06-28
Are you certain that the script simply isn't being run? Is it possible that it's being run and an error condition is causing the program to be stopped?

Try running it from a root session. Start the session with 'sudo -i', and then at the prompt, run '/etc/init.d/openvpn start'.

If it doesn't work, then are there any useful error messages?

If it does work, then maybe the problem has to do with startup ordering? In the filename, /etc/rc2.d/SNNopenvpn, what is the real number for NN?

---

### Post by AmishDave on 2010-06-28
"sudo -i /etc/init.d/openvpn start"
Runs successfully

jared@ez-server:/etc/rc2.d$ l
README                 S25bluetooth@   S70dns-clean@       S99ondemand@
S20fancontrol@         S50cups@        S70pppd-dns@        S99rc.local@
S20kerneloops@         S50pulseaudio@  S90binfmt-support@
S20openvpn@            S50rsync@       S99acpi-support@
S20speech-dispatcher@  S50saned@       S99grub-common@

So you were spot on.  I just bumped it up...err...down in the order?  Up in number down in order?  Aw screw it.  It's moved it works.  You know what I mean.

Thank you ever so kindly.

---

