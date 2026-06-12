---
title: "Unknown process mysql at startup"
date: 2010-10-06
forum: General Help
---

### Post by satish_j on 2010-10-06
What is this unknown mysql program that is running at startup.I have removed all the mysql packages from synaptic.
```

satish@Titan:~$ ps aux|grep mysql
satish    4599  0.0  0.1   3320   780 pts/0    S+   23:21   0:00 grep --color=auto mysql
satish@Titan:~$ ps aux|grep mysql
satish    4603  0.0  0.1   3320   776 pts/0    S+   23:21   0:00 grep --color=auto mysql
satish@Titan:~$

```
Moreover,as you can see,its PID keeps on changing.If i try to kill first PID,it says "No such PID"

---

### Post by TeoBigusGeekus on 2010-10-06
I think it's funny, but me thinks that this process is the grep command searching for mysql.

---

### Post by TeoBigusGeekus on 2010-10-06
I'll post this to reddit...

---

### Post by satish_j on 2010-11-30
> **TeoBigusGeekus said:**
> I think it's funny, but me thinks that this process is the grep command searching for mysql.

you was right..if i entered mysql2,it gave 'mysql2' in output as well,which confirms that process is the grep command itself

---

