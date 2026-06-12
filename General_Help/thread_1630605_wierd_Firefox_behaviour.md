---
title: "wierd Firefox behaviour"
date: 2010-11-25
forum: General Help
---

### Post by bachor on 2010-11-25
running FF 3.6.12 w/ NoScript  on Ubuntu 10.10 with Apparmor and FF profile from BodhiZazen

 problem:

Firefox sometimes WON'T let me to see certain pages [NoScript Enabled] right when I need them ;)

 Example:

 trying to load :   [http://bfads.net/Online-Black-Friday-Sales-Starting-Now-2010](http://bfads.net/Online-Black-Friday-Sales-Starting-Now-2010)

 got this: 

**Invalid URL**

 The requested URL "/Online-Black-Friday-Sales-Starting-Now-2010", is invalid. Reference #9.67cf8f18.1290705237.1878e3d3 





 How come URL says ONLY /Online......    and not whole page [http://bfads.net/Online-Black-Friday-Sales-Starting-Now-2010](http://bfads.net/Online-Black-Friday-Sales-Starting-Now-2010)  ?

 Sometimes restart FF helps. Just rarely thou.

 Any idea?

---

### Post by Rubi1200 on 2010-11-25
First link worked for me, second not.

I also use NoScript, but not AppArmor.

Try starting Firefox in Safe Mode and see if that makes a difference.

Either that or there may be a problem with the FF AppArmor profile, though it seems this is quite random from your description.

What about changing DNS servers?

---

### Post by bachor on 2010-11-25
> **Rubi1200 said:**
> First link worked for me, second not.

I also use NoScript, but not AppArmor.

Try starting Firefox in Safe Mode and see if that makes a difference.

Either that or there may be a problem with the FF AppArmor profile, though it seems this is quite random from your description.

What about changing DNS servers?


 Rubi: sorry I fixed the 2nd link.

 how do I do Safe mode FF?

 I don't do anything with DNS servers. What should I do? and why?

thanx

---

### Post by Rubi1200 on 2010-11-25
Applications > Accessories > Terminal
```
firefox -safe-mode
```

First try this and then we can see what else might be going on.

---

### Post by bachor on 2010-11-25
> **Rubi1200 said:**
> Applications > Accessories > Terminal
```
firefox -safe-mode
```First try this and then we can see what else might be going on.

thanx Rubi,

problem is that it does only once a while, sometimes I'm in my email and can't log off.

 anyhow did FF safe :

pawel@pawel-Inspiron-6000:~$ firefox -safe-mode
2.4+ kernel w/o ELF notes? -- report this
Unknown HZ value! (40) Assume 100.
NOTE: child process received `Goodbye', closing down

---

### Post by Rubi1200 on 2010-11-25
You say this is on 10.10; just out of curiosity are you running the 32 or 64bit version?

---

### Post by bachor on 2010-11-25
> **Rubi1200 said:**
> You say this is on 10.10; just out of curiosity are you running the 32 or 64bit version?


 32bit

---

### Post by bachor on 2010-11-25
it might be something with the cable internet [DNS?], because even TV sometimes freezes. And I did the speed test and once it was 200kb down and once 1000kb down. just a thought

---

### Post by Rubi1200 on 2010-11-25
Can you post the output of this command please:

```
uname -r
```

---

### Post by bachor on 2010-11-25
> **Rubi1200 said:**
> Can you post the output of this command please:

```
uname -r
```


2.6.35-23-generic

---

### Post by Rubi1200 on 2010-11-26
To be honest, I am not sure what the problem might be.

You might try disabling the AppArmor profile just to see if that is causing the issues.

Or, it could be a corrupt FF profile.

Hopefully, others will have some better advice to offer.

---

### Post by James78 on 2010-11-26
While we're at it, it could be any one of your extensions. You could try starting firefox with "firefox -safe-mode", then select disable all addons and continue in safemode. If everything works that way, then one of your addons is going haywire.

---

### Post by bachor on 2010-11-27
> **Rubi1200 said:**
> To be honest, I am not sure what the problem might be.

You might try disabling the AppArmor profile just to see if that is causing the issues.

Or, it could be a corrupt FF profile.

Hopefully, others will have some better advice to offer.

thanx Rubi for trying


> **James78 said:**
> While we're at it, it could be any one of your extensions. You could try starting firefox with "firefox -safe-mode", then select disable all addons and continue in safemode. If everything works that way, then one of your addons is going haywire.


thanx James as well. It is wierd, it does only once in a while. It works since. I did NoScript update and it stopped, for now. So it was probably why.

 thanks all!

P. :P

---

### Post by bachor on 2010-11-29
wow, here we go again. I was trying to Upload pictures to Mpix.com via Mpix's Java tool and....

 .... having same issue again!!:frown:

What I did this time I set Firefox in AppArmor from "Enforced" to "complain" mode:

pawel@pawel-Inspiron-6000:~$ **[COLOR=Red]sudo complain firefox[/COLOR]**
Setting /etc/apparmor.d/usr.bin.firefox to complain mode.
pawel@pawel-Inspiron-6000:~$ sudo /etc/init.d/apparmor status
apparmor module is loaded.
37 profiles are loaded.
14 profiles are in enforce mode.
   /sbin/dhclient3
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/chromium-browser/chromium-browser//browser_java
   /usr/lib/chromium-browser/chromium-browser//browser_openjdk
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/firefox-3.6.12/firefox-*bin//browser_java
   /usr/lib/firefox-3.6.12/firefox-*bin//browser_openjdk
   /usr/sbin/cupsd
   /usr/sbin/tcpdump
   /usr/share/gdm/guest-session/Xsession
23 profiles are **[COLOR=Red]in complain mode[/COLOR]**.
   /bin/ping
   /sbin/klogd
   /sbin/syslog-ng
   /sbin/syslogd
   /usr/lib/chromium-browser/chromium-browser
   /usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox
   /usr/lib/dovecot/deliver
   /usr/lib/dovecot/dovecot-auth
   /usr/lib/dovecot/imap
   /usr/lib/dovecot/imap-login
   /usr/lib/dovecot/managesieve-login
   /usr/lib/dovecot/pop3
   /usr/lib/dovecot/pop3-login
   **[COLOR=Red]/usr/lib/firefox-3.6.12/firefox-*bin[/COLOR]**
   /usr/sbin/avahi-daemon
   /usr/sbin/dnsmasq
   /usr/sbin/dovecot
   /usr/sbin/identd
   /usr/sbin/mdnsd
   /usr/sbin/nmbd
   /usr/sbin/nscd
   /usr/sbin/smbd
   /usr/sbin/traceroute
5 processes have profiles defined.
1 processes are in enforce mode :
   /sbin/dhclient3 (1654) 
3 processes are in complain mode.
   /usr/lib/firefox-3.6.12/firefox-*bin (3116) 
   /usr/sbin/avahi-daemon (814) 
   /usr/sbin/avahi-daemon (882) 
1 processes are unconfined but have a profile defined.
   /usr/sbin/cupsd (1089) 


 

than run Firefox in Safe mode [without NoScript add-on] , and got this:

pawel@pawel-Inspiron-6000:~$ firefox -safe-mode
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.1) (6b20-1.9.1-1ubuntu3)
OpenJDK Client VM (build 17.0-b16, mixed mode, sharing)
Aurigma ImageUploader version: 6.5.19.0
Current document URL: [http://www.mpix.com/customer/](http://www.mpix.com/customer/)
2.4+ kernel w/o ELF notes? -- report this
Reading cookies
Cookies: __utma=242362718.1358241613.1291061094.1291061094.1291061094.1; __utmb=242362718.2.10.1291061094; __utmc=242362718; __utmz=242362718.1291061094.1.1.utmcsr=(direct)|utmccn=(direct)|utmcmd=(none); __utmv=242362718.mpixuser%2F728381
Reading referer
Referer: [http://www.mpix.com/customer/](http://www.mpix.com/customer/)
Killed



 Whole Firefox went grey, and I couldn't do anything in browser so I shut it off.

 Am I the only one having this issue? :P

---

### Post by aeronutt on 2010-12-21
I'm having it in Firefox and Chrome.  A lot of googling about it shows that it's happening to some people even with Windows. Quite a few posts in LInksys forums on the issue.  Seems to be some sort of router/DNS/something something issue I can't understand and can't put together from all the search results. But...I wish I could figure out a fix, because it happens to me a few times a day.

---

### Post by bachor on 2010-12-22
> **aeronutt said:**
> I'm having it in Firefox and Chrome.  A lot of googling about it shows that it's happening to some people even with Windows. Quite a few posts in LInksys forums on the issue.  Seems to be some sort of router/DNS/something something issue I can't understand and can't put together from all the search results. But...I wish I could figure out a fix, because it happens to me a few times a day.


 yea,it is probably something with DNS or some. I did install Kubuntu on USB flash with no Apparmor [or anything that would mess it up] and No-script disabled on FF and once I got same issue. Couldn't get to my yahoo email.
 Seems to me that everytime there's Kernel update it works for bit with new Kernel,and then it starts again. Could it be too?  .)

---

