---
title: "avahi-daemon time machine share not working any more"
date: 2011-04-14
forum: General Help
---

### Post by big_blue on 2011-04-14
Hi.

I few days ago my TimeMachine share does not work any more. I worked a few month, but now i´m not able to mount the shares. Maybe there is a problem with the new version of the avahi-daemon. Here is the message from the syslog:
```
Apr 14 23:42:57 atom avahi-daemon[11740]: Loading service file /services/tm.service.
Apr 14 23:42:57 atom avahi-daemon[11740]: /services/tm.service: parse failure: didn't expect element <service>.
Apr 14 23:42:57 atom avahi-daemon[11740]: XML_ParseBuffer() failed at line 4: not well-formed (invalid token).
Apr 14 23:42:57 atom avahi-daemon[11740]: Failed to load service group file /services/tm.service, ignoring.
```

Here is the tm.service:
```
<service>
  <type>_adisk._tcp</type>
  <port>9</port>
  <txt -record>sys=waMA=MYMAC</txt>
  <txt -record>dk0=adVF=0x81,adVN=TimeMachine,adVU=8f8e20e6-f027-4e45-9a7c-e090c89da36d</txt>
</service>

```

Here is the AppleVolume.default from the netatalk share:
```

~/ "$u" allow:USER1,USER2 cnidscheme:cdb
#/TimeMachine TimeMachine allow:USER1,USER2 options:tm cnidscheme:dbd cnidscheme:cdb options:usedots,upriv

```
If i uncomment the TimeMachine share, i´m not able to mount one of the shares. So the HOME directory is working.

If someone have an idea what happend would be nixe. I would prefere the backup via the timemachine software of my mac.

---

