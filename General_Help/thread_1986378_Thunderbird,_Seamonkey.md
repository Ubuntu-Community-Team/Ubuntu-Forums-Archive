---
title: "Thunderbird, Seamonkey"
date: 2012-05-24
forum: General Help
---

### Post by tlan on 2012-05-24
Can someone give any advise to this situation

12.04 64bit logging into 12.04 32 bit server running openldap/nfs/

when i installed 11.04 thunderbird and seamonkey work

when i install upgrade or fresh 12.04. neither thunderbird or seamonkye start.

seems to be a caching issue between login id and server home 

this is the error from terminal when starting thunderbird.
(thunderbird-bin:20014): GLib-WARNING **: getpwuid_r(): failed due to: Connection refused.

i can start thunderbird and/or seamonkey as root

---

### Post by tlan on 2012-05-25
> **tlan said:**
> Can someone give any advise to this situation

12.04 64bit logging into 12.04 32 bit server running openldap/nfs/

when i installed 11.04 thunderbird and seamonkey work

when i install upgrade or fresh 12.04. neither thunderbird or seamonkye start.

seems to be a caching issue between login id and server home 

this is the error from terminal when starting thunderbird.
(thunderbird-bin:20014): GLib-WARNING **: getpwuid_r(): failed due to: Connection refused.

i can start thunderbird and/or seamonkey as root


Anyone ????

---

### Post by tlan on 2012-06-17
for some reason this was a simple resetting of my password in openldap. 

once that was done, and logging in again both mozilla apps started working, whoohoo

---

### Post by tlan on 2012-07-05
> **tlan said:**
> for some reason this was a simple resetting of my password in openldap. 

once that was done, and logging in again both mozilla apps started working, whoohoo


Correction

This error GLib-WARNING **: getpwuid_r(): failed due to: Connection refused.

is because i am authenticating a user account via openldap when logging in to the PC. the fix is to install nslcd which will also install nscd.

configure it to point to the ldap server and all is ok. This has been verified working on several computers that had this issue.

---

