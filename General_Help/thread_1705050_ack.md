---
title: "ack"
date: 2011-03-11
forum: General Help
---

### Post by xeare on 2011-03-11
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

computer froze while i was downloading something and i cannot use synaptic package manager anymore. help me please? the dpkg message came up saying --configure0a was an unknow option

---

### Post by davidmohammed on 2011-03-11
use the terminal and type in the sudo command as described.

and its not --configure0a...

---

### Post by xeare on 2011-03-11
dpkg: parse error, in file '/var/lib/dpkg/updates/0071' near line 0:
 EOF during value of field `/xhtml' (missing final newline)

i got this. now what?

---

### Post by davidmohammed on 2011-03-11
hmmm - strange error.  Google search on the error mentioned that this error appears if you have run out of disk space...

have you

type

df

---

### Post by xeare on 2011-03-11
no, ive got 48% disk space.  OH, this might help. my computer froze while i was downloading from the synaptic package manager, any ideas?

---

### Post by davidmohammed on 2011-03-11
the freeze would cause this issue.

try this

```
cd /var/lib/dpkg/updates/
ls -la
sudo rm -rf 0071

cd ~/
sudo dpkg --configure -a

```

note be very careful - 

ls -la should show various folders like 0071 etc

if sudo dpkg --configure -a fails with another folder then repeat but with that number

If you have lots of updates - maybe try deleting all of the folders in one go

---

### Post by xeare on 2011-03-11
thanks, it works now

---

### Post by davidmohammed on 2011-03-11
excellent - just mark the thread as solved please.

---

