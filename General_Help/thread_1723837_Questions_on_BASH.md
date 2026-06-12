---
title: "Questions on BASH"
date: 2011-04-07
forum: General Help
---

### Post by Neill_R on 2011-04-07
1 Is this the right forum to raise questions on BASH scripting
2. What method would you use to extract the IP address from the file given by wget from checkip.dyndns.com e.g.

<html><head><title>Current IP Check</title></head><body>Current IP Address: 89.195.?.15</body></html>
I can get 

89.195.?.15</body></html> but can't seem to get rid of the tailing text.

Many thanks in advance 

Neill

---

### Post by CharlesA on 2011-04-07
```
wget -q checkip.dyndns.org -O index.html && cat index.html|cut -d ' ' -f 6 | cut -d '<' -f 1
```

From here: [http://www.linux.com/community/forums?func=view&catid=19&id=9528](http://www.linux.com/community/forums?func=view&catid=19&id=9528)

---

### Post by WorMzy on 2011-04-07
Note that with that example, you will need to manually remove the index.html afterwards.

Save the file to /tmp/ to have the OS remove the file automatically at the next boot.

```
wget -q checkip.dyndns.org -O /tmp/index.html && cat /tmp/index.html|cut -d ' ' -f 6 | cut -d '<' -f 1
```

---

### Post by Neill_R on 2011-04-07
Thank You

---

### Post by amauk on 2011-04-07
Minor point, but if you output wget to stdout you can pipe directly into other programs without the need for any temporary files

```
wget -q checkip.dyndns.org -O - | grep -o 'Current IP Address: [^<]*' | sed 's|Current IP Address: ||'
```

---

