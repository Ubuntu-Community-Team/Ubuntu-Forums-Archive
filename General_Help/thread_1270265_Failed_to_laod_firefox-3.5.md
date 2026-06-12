---
title: "Failed to laod firefox-3.5"
date: 2009-09-19
forum: General Help
---

### Post by Tapas Bose, India on 2009-09-19
Hallo everybody.
I am facing a problem with my firefox for one month or over. I had enabled "Show text during boot" option from System -> Administration -> Start up Manager. From that text I saw some failure of loading of firefox 3.5. Like:

*Skipped: /etc/apparmor.d/usr.bin.firefox-3.5
Error: #include <abstractions/private-data> not found at line 81 in /etc/apparmor.d/usr.bin.firefox-3.5
Error: #include <abstractions/ubuntu-mail> not found at line 166 in /etc/apparmor.d/usr.bin.firefox-3.5
Error: #include <abstractions/ubuntu-console-email> not found at line 167 in /etc/apparmor.d/usr.bin.firefox-3.5
Error: #include <abstractions/ubuntu-gnome-terminal>  not found at line 167 in /etc/apparmor.d/usr.bin.firefox-3.5
*Failure: /etc/apparmor.d/usr.bin.firefox-3.5 failed to load                      [fail]

I have uninstall and again install firefox-3.5 for 3 times. But the error message is still displayed during shut down and startup. 

Thanks in advance.

---

### Post by lovinglinux on 2009-09-19
Firefox is not loaded at startup. What you see in that report is about [Apparmor](http://ubuntuforums.org/showthread.php?t=1008906), which is probably having issues with firefox-3.5, although I'm not sure what those errors means and if they are a real problem or not. Perhaps you could check if there is a profile in Apparmor settings for firefox-3.5 and delete it, if you do not use Apparmor.

---

### Post by Soul-Sing on 2009-09-19
Indeed it is an apparmor message. Is the firefox apparmor profile in the enforced mode?

---

### Post by Tapas Bose, India on 2009-09-21
> **leoquant said:**
> Indeed it is an apparmor message. Is the firefox apparmor profile in the enforced mode?
Thank you for reply. I don't no whether firefox is in the enforced mode or not?

---

### Post by Soul-Sing on 2009-09-21
> **Tapas Bose, India said:**
> Thank you for reply. I don't no whether firefox is in the enforced mode or not?

```
sudo /etc/init.d/apparmor status
```

---

### Post by Tapas Bose, India on 2009-09-21
> **leoquant said:**
> ```
sudo /etc/init.d/apparmor status
```
Thank you for reply. I have been checked the status. These are the results:

> 
apparmor module is loaded.
21 profiles are loaded.
9 profiles are in enforce mode.
   /usr/share/gdm/guest-session/Xsession
   /usr/sbin/cupsd
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/sbin/avahi-daemon
   /usr/lib/connman/scripts/dhclient-script
   /usr/sbin/tcpdump
   /usr/lib/cups/backend/cups-pdf
   /sbin/dhclient3
   /sbin/dhclient-script
12 profiles are in complain mode.
   /usr/sbin/traceroute
   /bin/ping
   /usr/sbin/mdnsd
   /usr/sbin/ntpd
   /usr/sbin/identd
   /usr/sbin/nmbd
   /usr/sbin/dnsmasq
   /sbin/klogd
   /usr/sbin/smbd
   /sbin/syslogd
   /sbin/syslog-ng
   /usr/sbin/nscd
5 processes have profiles defined.
3 processes are in enforce mode :
   /usr/sbin/avahi-daemon (2955) 
   /usr/sbin/cupsd (2984) 
   /usr/sbin/avahi-daemon (2958) **
2 processes are in complain mode.
   /sbin/klogd (2431) 
   /sbin/syslogd (2411) 
0 processes are unconfined but have a profile defined.

What to do now?
**2958

---

### Post by Soul-Sing on 2009-09-21
So you get apparmor (.usr.bin.firefox 3.5)  errormessages, but firefox isn't in the enforce or even in the complain apparmor mode.
Strange. No idea how i could help you with this error.

Where did you put the apparmor firefox profile?

---

### Post by Tapas Bose, India on 2009-09-21
> **leoquant said:**
> So you get apparmor (.usr.bin.firefox 3.5)  errormessages, but firefox isn't in the enforce or even in the complain apparmor mode.
Strange. No idea how i could help you with this error.

Where did you put the apparmor firefox profile?
I did not put apparmor firefox profile anywhere! I did not create it.

---

### Post by Tapas Bose, India on 2009-09-21
I found a website
[http://www.dtschmitz.com/dts/2009/07/how-to-install-apparmor-profile-for-firefox-351-in-ubuntu-904.html](http://www.dtschmitz.com/dts/2009/07/how-to-install-apparmor-profile-for-firefox-351-in-ubuntu-904.html)
but can not understand this.

---

### Post by Soul-Sing on 2009-09-21
And is this directory?
```
 /etc/apparmor.d
```  or
```
 /etc/apparmor.d
```
no apparmor firefox profile?

---

### Post by Tapas Bose, India on 2009-09-21
Yes I have /etc/apparmor.d directory. I have attached a screen shot of this directory. I can not understand what is the apparmor firefox profile among these files and directory..

---

### Post by Soul-Sing on 2009-09-21
You could with sudo rights remove this usr.bin.firefox-3.5 profile.
and check the logs again. You should not have the warnings anymore after removing this profile.

---

### Post by Tapas Bose, India on 2009-09-21
> **leoquant said:**
> You could with sudo rights remove this usr.bin.firefox-3.5 profile.
and check the logs again. You should not have the warnings anymore after removing this profile.
Can you please tell me how can I remove this profile? I am new in linux. And what is that particular profile? And logs means
sudo /etc/init.d/apparmor status ?

---

### Post by Tapas Bose, India on 2009-09-21
I have deleted the file usr.bin.firefox-3.5. And the log is:
apparmor module is loaded.
21 profiles are loaded.
9 profiles are in enforce mode.
   /usr/share/gdm/guest-session/Xsession
   /usr/sbin/cupsd
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/sbin/avahi-daemon
   /usr/lib/connman/scripts/dhclient-script
   /usr/sbin/tcpdump
   /usr/lib/cups/backend/cups-pdf
   /sbin/dhclient3
   /sbin/dhclient-script
12 profiles are in complain mode.
   /usr/sbin/traceroute
   /bin/ping
   /usr/sbin/mdnsd
   /usr/sbin/ntpd
   /usr/sbin/identd
   /usr/sbin/nmbd
   /usr/sbin/dnsmasq
   /sbin/klogd
   /usr/sbin/smbd
   /sbin/syslogd
   /sbin/syslog-ng
   /usr/sbin/nscd
5 processes have profiles defined.
3 processes are in enforce mode :
   /usr/sbin/avahi-daemon (2970) 
   /usr/sbin/avahi-daemon (2971) 
   /usr/sbin/cupsd (2996) 
2 processes are in complain mode.
   /sbin/syslogd (2422) 
   /sbin/klogd (2442) 
0 processes are unconfined but have a profile defined.

---

### Post by Tapas Bose, India on 2009-09-21
Thank you very much. I have rebooted my computer for two times now and not get the failure message any more. I think the problem is solved. Isn't it?
Thank you very much again. I am getting frustrated seeing the failure message each and every time of start up and shut down.
Thank you for spending time for me.
Good night.

---

