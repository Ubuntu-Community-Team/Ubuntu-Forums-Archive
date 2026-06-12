---
title: "ls: cannot access &quot;mount folder&quot;: Host is down"
date: 2012-08-03
forum: General Help
---

### Post by vrparekh on 2012-08-03
i have windows 2008 server machine, and i mount few its folders in ubuntu.

suppose i mounted five location.
abc,
bcd,
def,
efg,
ghi

now when i do ls,  it just hangs and after some time it shows listing with as per below

ls: cannot access "abc": Host is down
bcd def efg ghi

now this problem is arbitrary and not permanent. means after i restart Ubuntu server (one or couple of times) with init 6 (or after some time automatically it works), and run ls command and it works,   

after some time again it hangs with errors, also that error host is down is not coming for particular any location, it also arbitrary

once it gives error on abc, and after it gives error on efg and ghi.

i have mounted using cifs.

please help me to solve this problem.

Thanks

---

