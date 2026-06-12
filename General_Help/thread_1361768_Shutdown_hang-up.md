---
title: "Shutdown hang-up"
date: 2009-12-22
forum: General Help
---

### Post by grr51 on 2009-12-22
Hi,

On shutdown, the screen becomes completely fuzzy and the computer does not shutdown.

I need to hold the power button in order to force it to shutdown, which is not a very good practice for the file system.  This used to happen occasionally, but it is now systematic.

I am using version 9.10, and Grub2 version 1.97 beta 4 and a dual-boot.   Ubuntu is installed on the second disk (sdb) while Grub is installed on the first disk (sda).
Regarding Grub2, I noticed that the boot time is now much longer, compared to Grub Legacy which I was using with version 9.04.  Could this be the culprit?

Thanks for your help,

Gaétan

---

### Post by ratcheer on 2009-12-22
Try going to a console (Ctrl-Alt-F1) and shut down, manually:

sudo init 0

Maybe there will be some messages that help you figure out what is going wrong.

Tim

---

### Post by grr51 on 2009-12-22
Hi,

When I tried 'Ctrl-Alt-F1', the screen went completely fuzzy and the computer hung-up.  No other key combination would get it out of there.  Again, I had to hold the power switch to shut it down.

Gaétan

---

### Post by ratcheer on 2009-12-22
Ouch, that sounds serious. You will need more help than I know how to give.

Tim

---

### Post by MickeT on 2009-12-26
Hi
Having the same problem, I am using mythbuntu and ever since upgrading to 9.10
my HTPC hangs in 50% of the cases during shutdown&power off, tried various tips
but none seems to help.(some came through updates later)
(myth is using /sbin/poweroff tried changing that to shutdown -H -P now, same problem)
Rather annoying since my recordings then fails..
 
Linux tvuser-desktop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux

Last lines from syslog, then just no power off
Dec 26 00:09:30 tvuser-desktop init: tty4 main process (1123) killed by TERM signal
Dec 26 00:09:30 tvuser-desktop NetworkManager: <WARN>  nm_signal_handler(): Caught signal 15, shutting down normally.
Dec 26 00:09:30 tvuser-desktop init: tty5 main process (1125) killed by TERM signal
Dec 26 00:09:30 tvuser-desktop init: tty2 main process (1129) killed by TERM signal
Dec 26 00:09:30 tvuser-desktop init: tty3 main process (1130) killed by TERM signal
Dec 26 00:09:30 tvuser-desktop init: tty6 main process (1141) killed by TERM signal
Dec 26 00:09:30 tvuser-desktop init: cron main process (1160) killed by TERM signal
Dec 26 00:09:30 tvuser-desktop init: tty1 main process (2002) killed by TERM signal
Dec 26 00:09:31 tvuser-desktop kernel: Kernel logging (proc) stopped.

 
BR, MickeT

---

### Post by MickeT on 2009-12-26
Hi again
Just found an interesting piece of log during a succesfull shutdown
, well it powered off anyway, any tips?
 
 
Dec 26 10:51:36 tvuser-desktop kernel: [ 1709.495436] __ratelimit: 18 callbacks suppressed
Dec 26 10:51:36 tvuser-desktop kernel: [ 1709.495446] mythshutdown[3800]: segfault at 8a0303c ip 06d7aab3 sp bf8fc530 error 7 in libGL.so.185.18.36[6d4f000+81000]
Dec 26 10:52:23 tvuser-desktop wpa_supplicant[1171]: CTRL-EVENT-SCAN-RESULTS
Dec 26 10:54:23 tvuser-desktop wpa_supplicant[1171]: CTRL-EVENT-SCAN-RESULTS
Dec 26 10:56:23 tvuser-desktop wpa_supplicant[1171]: CTRL-EVENT-SCAN-RESULTS
Dec 26 10:58:23 tvuser-desktop wpa_supplicant[1171]: CTRL-EVENT-SCAN-RESULTS
Dec 26 11:00:23 tvuser-desktop wpa_supplicant[1171]: CTRL-EVENT-SCAN-RESULTS
Dec 26 11:01:18 tvuser-desktop lircd-0.8.6[1791]: accepted new client on /var/run/lirc/lircd
Dec 26 11:01:27 tvuser-desktop lircd-0.8.6[1791]: removed client
Dec 26 11:02:23 tvuser-desktop wpa_supplicant[1171]: CTRL-EVENT-SCAN-RESULTS
Dec 26 11:02:58 tvuser-desktop kernel: Kernel logging (proc) stopped.

---

### Post by NFblaze on 2009-12-26
Yes, I have been having this problem for quite a while, approximately since 9.04 if I'm not mistaken maybe 8.10. I have a laptop Compaq.

I have made a bug report, I think it's either the cause of SystemVinit and something combined with disk drives, as I tend to have this happen when I have an improper unmount of my external hard drive. Also, this will consistetly happen if I telinit to any runlevel 1 or 0. [As you can see here I've asked about this problem here last month.]("http://ubuntuforums.org/showthread.php?t=1318832")

I dont know, what it could be either. Though either try making sure you unmount any extra disk drives properly before shutting down.

Also, if you want you can also report your having the same issues as a bug over at  [launchpad here is where I filed mine ]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/481023")

---

### Post by MickeT on 2009-12-27
I only have one disc and my problems came with 9.10, there seem to be many people
with same problem. I am scanning for a solution or some help to pinpoint the problem

---

### Post by MickeT on 2009-12-30
Found out I was suffering from
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/440470](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/440470)
 
added
acpi_enforce_resources=lax to kernel boot options and I have now done
5 successfull shutdowns in a row, hope this workaround works,,,
 
dmidecode -s bios-version
ASUS M2NPV-VM ACPI BIOS Revision 1401
 
uname -r
2.6.31-16-generic

---

### Post by MickeT on 2010-01-01
weird, using kernel option above did not realy help but that I at the same time removed quiet and splash did the trick, if I just add quiet and splash the hanging
starts again, feels like some timing issue maybe.
 
also found myth-halt.sh script using dbus for shutdown, could this maybe be another
workaround for powering off:confused:

---

### Post by grr51 on 2010-01-03
Hi,

I found a workaround solution to my shutdown problem.  As mentioned, I found that when I was using "Ctrl-Alt-F1" the screen would get all fuzzy and the computer would freeze forcing a hard reset.

I therefore thought it might be related to video and I de-activated the proprietary NVIDIA accelerated graphics driver (version 96) recommended by Ubuntu.

My Video card is the following, as obtained from the command "lspci"
VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

Since I am not using any 3D or desktop effects, using the Ubuntu default video driver does not affect my display capabilities.

I did not have any shutdown or reboot freeze for almost a week now and I can therefore conclude that in my case the nVIDIA proprietary driver was the culprit.

Gaétan

---

