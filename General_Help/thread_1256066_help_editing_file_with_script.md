---
title: "help editing file with script"
date: 2009-09-02
forum: General Help
---

### Post by b-boy on 2009-09-02
Hi 

I have a file and need to change A LINE from 
```
ethtool -s eth0 autoneg off speed 100 duplex full
```
to
```
ethtool -s eth0 autoneg on
```

any ideas ??

I have manged to get what i need in std out with 
```
grep ethtool /etc/init.d/local |cut -d " " -f 1,2,3,4,5|sed -e 's/off/'on'/g'
```

but cannot have this line changed in the file itself

---

### Post by b-boy on 2009-09-02
resolved

```
sed -i.bck -r '/ethtool/ s/(.*autoneg).*/\1 on/' /etc/init.d/local
```

---

