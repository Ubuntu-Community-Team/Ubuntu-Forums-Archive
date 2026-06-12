---
title: "rhythmbox using the internet"
date: 2010-09-19
forum: General Help
---

### Post by Dex73 on 2010-09-19
I have firestarter installed and was making sure my video was loading when I noticed rhythmbox was using port 80. I took screen shots of active connections and events in firestarter hoping someone could tell me why rhythmbox needs to use the internet. This happens even when rhythmbox is closed.

I've attached the screen shots.
Selection_001 says rhythmbox under Program, but for some reason not in the picture.

---

### Post by robsoles on 2010-09-20
Do you subscribe to (or use in any way) last.fm?

Here is the whois record for 195.24.232.207 at the time of this posting (may the RIPE database owners forgive me or an admin/mod save me! ;))
```
rob@rob-desktop:~$ whois 195.24.232.207
% This is the RIPE Database query service.
% The objects are in RPSL format.
%
% The RIPE Database is subject to Terms and Conditions.
% See http://www.ripe.net/db/support/db-terms-conditions.pdf

% Note: This output has been filtered.
%       To receive output for a database update, use the "-B" flag.

% Information related to '195.24.232.0 - 195.24.233.255'

inetnum:        195.24.232.0 - 195.24.233.255
netname:        LASTFM-1
descr:          Last.FM Ltd
country:        GB
org:            ORG-LFL1-RIPE
admin-c:        MB18318-RIPE
tech-c:         MB18318-RIPE
admin-c:        LD659-RIPE
tech-c:         LD659-RIPE
status:         ASSIGNED PI
mnt-by:         RIPE-NCC-HM-PI-MNT
mnt-by:         AS24867-MNT
mnt-lower:      RIPE-NCC-HM-PI-MNT
mnt-routes:     AS24867-MNT
mnt-domains:    AS24867-MNT
source:         RIPE # Filtered

organisation:   ORG-LFL1-RIPE
org-name:       Last FM Ltd
org-type:       OTHER
address:        1-11 Baches Street, London, N1 6DL
e-mail:         hostmaster@last.fm
mnt-ref:        AS24867-MNT
mnt-by:         AS24867-MNT
source:         RIPE # Filtered

person:         Mike Brodbelt
address:        Last.fm Ltd
address:        1-11 Baches Street
address:        London
address:        N1 6DL
address:        England, UK
phone:          +44 (0)20 7780 7089
e-mail:         mike@last.fm
nic-hdl:        MB18318-RIPE
mnt-by:         AS24867-LWR-MNT
source:         RIPE # Filtered

person:         Laurie Denness
address:        Last.fm Ltd
address:        1-11 Baches Street
address:        London
address:        N1 6DL
address:        England, UK
phone:          +44 (0)20 7780 7097
nic-hdl:        LD659-RIPE
mnt-by:         AS24867-LWR-MNT
source:         RIPE # Filtered

% Information related to '195.24.232.0/23AS44948'

route:          195.24.232.0/23
descr:          LastFM
origin:         AS44948
mnt-by:         AS24867-MNT
source:         RIPE # Filtered


rob@rob-desktop:~$ 
```

---

### Post by Dex73 on 2010-09-20
Yes, I use it some times. So it's some sort of updating thing?
Is this a problem? That it's happening or that it fails? Either or both?

---

### Post by robsoles on 2010-09-20
Please tell me what the indication of failure is.

I imagine it is a harmless enough connection although it may be dribbling bytes. Setting a packet sniffer on it may be in order to determine how much data it is passing while you are not trying to listen to last.fm and reviewing the data may be worthwhile as well.

---

### Post by Dex73 on 2010-09-20
> **robsoles said:**
> Please tell me what the indication of failure is.

What I meant was that the connection was blocked.(I showed it in the second picture)  Fail may not have been the best terminology to use.

---

### Post by robsoles on 2010-09-21
That connection is not related as far as I can tell. It has more to do with windows file sharing.

---

### Post by Dex73 on 2010-09-21
OK, that just as long as it's not a huge problem. Thanks for the help.

---

