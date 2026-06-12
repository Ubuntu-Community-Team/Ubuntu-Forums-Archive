---
title: "df -h showing negative hdd space"
date: 2012-07-26
forum: General Help
---

### Post by buffchick on 2012-07-26
Can anyone think of a reason that df -h would show negative hdd space?
```
user@SVR1:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             1.6T  261G  1.3T  18% /
none                  127G  260K  127G   1% /dev
none                  127G  164K  127G   1% /dev/shm
none                  127G  420K  127G   1% /var/run
none                  127G     0  127G   0% /var/lock
none                  127G     0  127G   0% /lib/init/rw
/dev/sdb1              19T -676G   19T   -  /sandbox

```

---

### Post by Cheesemill on 2012-07-26
What type of filesystem is it?
```
df -h -T
```

---

### Post by buffchick on 2012-07-26
Ah sorry. I should have mentioned. GPT partition XFS format.

---

### Post by Habitual on 2012-07-26
> **cheesemill said:**
> ```
df -h -t
```

+1

---

### Post by buffchick on 2012-07-30
little t requires an argument. Assuming you wanted me to use the previously stated xfs.

```
root@SVR1:/# df -h -t xfs
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              19T -584G   19T   -  /sandbox

```

Big T shows
```
/dev/sdb1      xfs     19T -584G   19T   -  /sandbox
```

---

