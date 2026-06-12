---
title: "Swap File not Active? Cannot Hibernate. ?"
date: 2011-08-07
forum: General Help
---

### Post by jRdbRR on 2011-08-07
Hello and thank you in advance for the help.  Somewhere along the way in this little dual boot i have going, i lost my Hibernate, which sucks cause i REALLY like it.  Here's some screenshots...

Did i do something wrong in the partitioning?

---

### Post by tredegar on 2011-08-07
You have a swap partition, but you are not using it.
You need a line like this in /etc/fstab```
/dev/sda6  none            swap  sw  0  0
```
so it will be mounted.
Then ```
sudo mount -a
```

---

### Post by Elfy on 2011-08-07
If you think that you might have changed the swap partition at any time then it could be worth checking the /etc/initramfs-tools/conf.d/resume file once you've got swap added to fstab. 
```

sudo blkid |grep swap
cat /etc/initramfs-tools/conf.d/resume
```

The UUID's should match - if the UUID in the resume file is different - edit the file

```
gksudo gedit /etc/initramfs-tools/conf.d/resume
```

save the file exit and then run 

```
sudo update-initramfs -u
```

---

### Post by jRdbRR on 2011-08-07
oh man you guys are life savers! i know exactly what happened now, the swap file DID change cause i was going to triple boot with jolicloud and decided not to in the end so merged that partition w/ the others.  Thanks!

---

### Post by jRdbRR on 2011-08-07
i was also wondering about my partitioning structure, i may be doing a dual boot for a friend and wondered if this set up is ok?

---

### Post by tredegar on 2011-08-07
@jRdbRR
> i was also wondering about my partitioning structure, i may be doing a dual boot for a friend and wondered if this set up is ok?
_What_ *exact* "set up is OK" ?

You need to start a new thread, with some relevant information.

You should also read up on the use of capitals: "i was.." != "I was.."

Please spell out your words, or I (and, perhaps others) will see you as lazy and not worthy of answers.

---

### Post by jRdbRR on 2011-08-08
thank you for your informative reply. i am sorry you did not fully understand that the partition set up i was referring to was the same shown in the image above, perhaps if i had used capitals you would have understood.

> **tredegar said:**
> @jRdbRR

_What_ *exact* "set up is OK" ?

You need to start a new thread, with some relevant information.

You should also read up on the use of capitals: "i was.." != "I was.."

Please spell out your words, or I (and, perhaps others) will see you as lazy and not worthy of answers.

---

