---
title: "Multiple odd issues suddenly appearing"
date: 2010-03-31
forum: General Help
---

### Post by 9001 on 2010-03-31
Alright, bear with me on this one. Basically I suddenly got one/multiple odd issues. Here goes...

My Aspire One D150 just started acting up, and I have no idea what's causing it. I've been running ubuntu on it since 9.04 without issues, upgraded to 9.10 as it was released however.

*First off*, as I was browsing through my home folder, I accidentally hit F1. I closed the help window as it popped up, and an empty window titled "Ubiquity" replaced it. The system locked up completely at this, so I did SysRq-reisub to reboot.

*Later on*, when I did "ps -e" to get a PID, I noticed a process called "zenity <defunct>" which wouldn't let itself be killed. As the system was getting slow, I decided to **sudo shutdown -P now**.

*Then*, flipping through some folders to remove dupes, I found "somefile.flac" and "somefile (1).flac". The (1) file didn't seem to be visible for tabcomplete (yes I added \<space> after what it suggested) so I typed out the filename manually. Note that gnome-terminal was the only thing I'd opened since the former reboot. Right as I hit enter, everything turns black for 5 seconds. Then I'm met with the login screen. While everything seemed to work just fine after logging back in (including tabcomplete)... What?

Oh, also, occasionally when I shut down my computer, I get a message about ""ttyX main processes" being killed. Even though I haven't used any TTYs during the session.
```

Broadcast message from ont@netbook
    (/dev/pts/1) at 18:27 ...

The system is going down for power off NOW!
init: tty4 main process (1047) killed by TERM signal
init: rsyslog-kmsg main process (829) killed by TERM signal
acpid: exiting

init: avahi-daemon main process (852) terminted with status 255
init: tty5 main process (1050) killed by TERM signal
init: tty2 main process (1056) killed by TERM signal
init: tty3 main process (1057) killed by TERM signal
init: tty6 main process (1059) killed by TERM signal
init: cron main process (1060) killed by TERM signal
init: tty1 main process (1028) killed by TERM signal
  * Stopping web server lighttpd
modem-manager: Caught signal 15, shutting down...
init: Disconnected from system bus
 * Stopping Music Player Daemon mpd
 * Stopping Jetty servlet engine (was reachable on http://netbook:8080/), jetty
 * Stopping the Postfix Mail Transport Agency postfix
 * Stopping the Winbind daemon winbind
 * Stopping the MySQL database server mysqøld
    ...done.-
 * Shutting down ALSA...
 * Asking all remaining processes to terminate...

```...though I noticed how my grandfather's laptop has been occasionally getting the ttyX stuff starting today as well, about 1/10 times when shutting down. Taking this into consideration, it might not me correlated.

I have no idea whether either of these cases are connected at all, but I have never had any problems up until now, so I believe there's a good chance that they are. Just because I thought it'd be a quick solution, I ended up doing a dd if=/dev/zero of=/dev/sda bs=8M for a few seconds before I reinstalled 9.10 from a USB stick. I have all my documents on an external at any rate. But yet, now I'm seeing the TTY stuff occasionally again.

I'd really like to know what might be going on, as I'm afraid there's hardware issues afoot. Thanks.

---

