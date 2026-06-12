---
title: "Postfix problem with delivery"
date: 2011-07-25
forum: General Help
---

### Post by supradave on 2011-07-25
My current email setup is Postfix and MailScanner.  My machine went down due to a power outage and I cannot figure out what my problem is.  

I'm receiving and sending and everything gets marked as in the hold queue, the ! after the queue ID.  To release it I have tried postsuper -H ALL and rebooting and restarting and many other things.  To get mail to deliver finally, I have to release each email individually with postsuper -H $ID.  

```
while :
do 
for i in `postqueue -p | grep \! |cut -d\! -f1`
do 
postsuper -H $i
done
sleep 30
done
```

Any ideas as everything has worked normally for many months and other than having to do the above, everything appears to be normal.

---

