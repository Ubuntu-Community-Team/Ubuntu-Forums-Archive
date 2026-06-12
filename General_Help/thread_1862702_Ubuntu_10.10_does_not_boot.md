---
title: "Ubuntu 10.10 does not boot"
date: 2011-10-17
forum: General Help
---

### Post by Amateur_Linux on 2011-10-17
Hi everyone!! I'm new to ubuntu as my username projects.... 
  I've been using ubuntu 10.10 for a month... i was changing some boot options and when i logged out i cannot log in again..( back then i didn't know byepassing gui login)...
  i shut it down forcefully and when i restarted my laptop i found the following message....
  Could anyone help me...
  

  Thanks in advance...

---

### Post by An Sanct on 2011-10-17
Welcome to the forums!

First of all, it is helpful if you remember what you did before the problem occurred?

You can run a Live Ubuntu session from the installation media, where you installed from. From there, you can revert the changes you made and it should work again.

---

### Post by Amateur_Linux on 2011-10-17
> **An Sanct said:**
> Welcome to the forums!

First of all, it is helpful if you remember what you did before the problem occurred?

You can run a Live Ubuntu session from the installation media, where you installed from. From there, you can revert the changes you made and it should work again.
I changed the login options.... It was intially on automatic login... I changed it to show users... Apart from that i tried to install Salome...
 There is no problem with the GRUB... windows 7 boots properly...
 And sorry for being ignorant, how do you revert previous changes using live cd? 
  I've tried the option revert in advanced install option....

Plus I checked the syslog ... The warning lines are

Oct 16 15:20:38 ananth-VPCEB16FG pulseaudio[1599]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Oct 16 15:20:38 ananth-VPCEB16FG pulseaudio[1599]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Oct 16 15:20:38 ananth-VPCEB16FG pulseaudio[1599]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Oct 16 15:46:38 ananth-VPCEB16FG AptDaemon: INFO: Initializing daemon
Oct 16 15:51:39 ananth-VPCEB16FG AptDaemon: INFO: Quiting due to inactivity
Oct 16 15:51:39 ananth-VPCEB16FG AptDaemon: INFO: Shutdown was requested
Oct 16 16:04:28 ananth-VPCEB16FG AptDaemon: INFO: Initializing daemon
Oct 16 16:09:29 ananth-VPCEB16FG AptDaemon: INFO: Quiting due to inactivity
Oct 16 16:09:29 ananth-VPCEB16FG AptDaemon: INFO: Shutdown was requested
Oct 16 16:17:01 ananth-VPCEB16FG CRON[6990]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 16 16:17:01 ananth-VPCEB16FG CRON[6988]: (CRON) error (grandchild #6990 failed with exit status 1)
Oct 16 16:22:53 ananth-VPCEB16FG ntfs-3g[2940]: Unmounting /dev/sda3 ()
Oct 16 16:22:59 ananth-VPCEB16FG console-kit-daemon[1164]: WARNING: Unable to restart system: Failed to execute child process "/usr/lib/ConsoleKit/scripts/ck-system-restart" (Too many levels of symbolic links)
Oct 16 16:22:59 ananth-VPCEB16FG gnome-session[1474]: WARNING: Unable to restart system: Unable to restart system: Failed to execute child process "/usr/lib/ConsoleKit/scripts/ck-system-restart" (Too many levels of symbolic links)
Oct 16 16:23:00 ananth-VPCEB16FG console-kit-daemon[1164]: WARNING: Unable to spawn /usr/lib/ConsoleKit/run-session.d/pam-foreground-compat.ck: Failed to execute child process "/usr/lib/ConsoleKit/run-session.d/pam-foreground-compat.ck" (Too many levels of symbolic links)

Also i've attached the syslog file here... tks

---

