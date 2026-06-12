---
title: "Problem with SMB &amp; AFP (TimeMachine)"
date: 2012-09-30
forum: General Help
---

### Post by Zikofski on 2012-09-30
i am trying to get my ubuntu 12.04 to run SMB share and AFP share for Time Machine,

SMB share works perfectly until i start the avahi-daemon service

disabling SMB wont allow AFP to work, but disabling avahi-daemon allows SMB to work


when everything is on, my MACbook pro can see the server, but trying to log in gets me this error message

i have also tried using different logins

```
There was a problem connecting to the server “storage.local”.
```

```
Check the server name or IP address, and then try again. If you continue to have problems, contact your system administrator.
```

added the following info into respective places

/etc/netatalk/AppleVolumes.default
```
/mnt/raid1/TimeMachine/ "TimeMachine" allow:andrew cnidscheme:dbd volsizelimit:650000 options:usedots,upriv,tm
```

/etc/netatalk/afpd.conf
```
 - -tcp -noddp -uamlist uams_dhx.so,uams_dhx2.so -nosavepassword
```

in /etc/default/netatalk i ensured CNID_METAD_RUN=yes was running

and created this file
/etc/avahi/services/afpd.service 
```
<?xml version="1.0" standalone='no'?><!--*-nxml-*-->
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
<name replace-wildcards="yes">%h</name>
<service>
<type>_afpovertcp._tcp</type>
<port>548</port>
</service>
<service>
<type>_device-info._tcp</type>
<port>0</port>
<txt-record>model=Xserve</txt-record>
</service>
</service-group>


```

please could someone help me, this has been bugging me all day

---

