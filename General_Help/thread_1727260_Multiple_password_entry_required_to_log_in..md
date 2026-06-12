---
title: "Multiple password entry required to log in."
date: 2011-04-12
forum: General Help
---

### Post by engr_sav on 2011-04-12
I have a Dell Mini 9 running Ubuntu Netbook edition. At start up I have to input my password three times before it finally catches and logs me in. Any suggestions on what could be happening here? Thanks.

---

### Post by sanguinoso on 2011-04-12
Are you sure you're typing it right? Is there a network login?

---

### Post by engr_sav on 2011-04-12
I have to type in the same password three times. No network login.

---

### Post by sanguinoso on 2011-04-12
Do you have KeyTouch2 installed?

---

### Post by engr_sav on 2011-04-12
Nope, doesnt look like it.

---

### Post by earthpigg on 2011-04-12
hrm. i have a mini 9 and haven't seen this problem, so i don't *think* it is a mini 9-specific problem - though i've never used UNR. but, who knows. we need to dig around a bit...

can you show us the output of this command, please, *immediately* after logging in:

```
tail /var/log/auth.log
```

---

### Post by David Vincent-Jones on 2011-08-31
Could you enlighten me as to my multi password problem and a possible solution:
****************

david@david-desktop:~$ tail /var/log/auth.log
Aug 31 13:21:54 david-desktop su[1372]: + ??? root:lp
Aug 31 13:21:54 david-desktop su[1372]: pam_unix(su:session): session opened for user lp by (uid=0)
Aug 31 13:21:54 david-desktop su[1372]: pam_unix(su:session): session closed for user lp
Aug 31 13:21:55 david-desktop polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session1 (system bus name :1.25 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_CA.UTF-8)
Aug 31 13:21:56 david-desktop gnome-keyring-daemon[1386]: unsupported key algorithm in certificate: 1.2.840.10045.2.1
Aug 31 13:21:56 david-desktop gnome-keyring-daemon[1386]: unsupported key algorithm in certificate: 1.2.840.10045.2.1
Aug 31 13:21:57 david-desktop dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.33" (uid=1000 pid=1489 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.10" (uid=0 pid=976 comm="/usr/sbin/console-kit-daemon))
Aug 31 13:21:57 david-desktop gnome-keyring-prompt: could not grab keyboard: 3
Aug 31 13:21:57 david-desktop gnome-keyring-prompt: could not grab keyboard: 3
Aug 31 13:22:05 david-desktop gnome-keyring-daemon[1386]: couldn't allocate secure memory to keep passwords and or keys from being written to the disk
david@david-desktop:~$ 
******************

Thanks

David

---

