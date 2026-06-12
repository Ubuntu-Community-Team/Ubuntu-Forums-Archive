---
title: "SSH Banner Repeats Itself??"
date: 2011-05-05
forum: General Help
---

### Post by burtonrhodes on 2011-05-05
I performed an apt-get upgrade and now my SSH Welcome Banner looks like the following. You'll notice that the banner repeats itself. The bottom half is acutally "static" and doesn't change. The top part is what I would normally see. How do I remove the bottom portion of the banner? Or modify the banner? Using Ubuntu Server 10.04 LTS
 
```

Using username "brhodes".
brhodes@66.101.58.90's password:
Linux mail.aframeonline.com 2.6.32-30-server #59-Ubuntu SMP Tue Mar 1 22:46:09 UTC 2011 x86_64 GNU/Linux
Ubuntu 10.04.2 LTS
 
Welcome to the Ubuntu Server!
 * Documentation:  [http://www.ubuntu.com/server/doc](http://www.ubuntu.com/server/doc)
  System information as of Thu May  5 06:27:35 CDT 2011
  System load:    0.06              Memory usage: 14%   Processes:       381
  Usage of /home: 0.6% of 32.08GB   Swap usage:   0%    Users logged in: 0
  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)
Ubuntu 10.04.2 LTS
 
Welcome to the Ubuntu Server!
 * Documentation:  [http://www.ubuntu.com/server/doc](http://www.ubuntu.com/server/doc)
  System information as of Mon May  2 20:31:20 CDT 2011
  System load:    0.22              Memory usage: 24%   Processes:       373
  Usage of /home: 1.0% of 32.08GB   Swap usage:   0%    Users logged in: 0
  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)
17 packages can be updated.
0 updates are security updates.
Last login: Thu May  5 06:09:55 2011 from 75-31-216-248.lightspeed.dllstx.sbcglobal.net
 
brhodes@mail:~$

```

---

### Post by Grenage on 2011-05-05
I am going to guess that the motd somehow copied itself into the tail section; does the text appear here?

```
/etc/motd.tail
```

---

### Post by burtonrhodes on 2011-05-05
Yes!  Should I just delete all the text in that file?  Contents of the file are below...
 
```

Ubuntu 10.04.2 LTS
Welcome to the Ubuntu Server!
 * Documentation:  [http://www.ubuntu.com/server/doc](http://www.ubuntu.com/server/doc)
  System information as of Mon May  2 20:31:20 CDT 2011
  System load:    0.22              Memory usage: 24%   Processes:       373
  Usage of /home: 1.0% of 32.08GB   Swap usage:   0%    Users logged in: 0
  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)
17 packages can be updated.
0 updates are security updates.

```

---

### Post by Grenage on 2011-05-05
Yup, it's safe to remove it. :)

---

### Post by nutznboltz on 2011-05-20
[this is why that happens]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/785424")

---

