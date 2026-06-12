---
title: "problem with wifi when downloading"
date: 2010-03-05
forum: General Help
---

### Post by viduthalairr on 2010-03-05
Hi,
I have installed ubuntu 9.10. I access internet through wifi. the internet works just fine but when i start some download the connection just stops and it taks a very long time to resume... this doesn happen with my xp.. please help.

---

### Post by viduthalairr on 2010-03-05
i am new to ubuntu. so please help me.

---

### Post by Daveski on 2010-03-05
Is this downloading via Firefox?
You could try diabling IPv6 in FF:

Type **about:config** in the address bar, and hit the Enter
Type **ipv6** in the filter field.
Highlight **network.dns.disableIPv6** by right-clicking it, and change the value from **false** to **true** using Toggle

---

### Post by viduthalairr on 2010-03-05
Hi Daveski,
Thanks for your reply. but, its every thing... even if i update ubuntu, install some software from the software centre or any download for that matter. Do you still advise me to do what you suggested??

---

### Post by Daveski on 2010-03-05
It won't do any harm.

What speed to you get reported if you visit

[http://speedtest.net/]("http://speedtest.net/")

---

### Post by viduthalairr on 2010-03-06
Hi if i use the link, first it shows more than 6mb and then it starts decreasing slowly. but while it was decreasing i lost my connection... ::(

---

### Post by viduthalairr on 2010-03-06
i have another problem. when i start firefox now its not working.... plz see the attached screen shot:(

---

### Post by Daveski on 2010-03-06
Oh dear. This is the soft of thing that a broken addon can cause. Try starting FF in safe mode from a terminal:

```
firefox -safe-mode
```

Then go to Tools > Add-ons. It will give you a list of Add-ons - you could try disabling any Add-ons you have and see if that makes a difference.

As for the speed problem, are you in a position to try another computer on your internet connection and run the test again? I wonder if it is a problem with the connection rather than Ubuntu?

---

### Post by viduthalairr on 2010-03-09
hi deveski,
thanks for the help. i got my firefox fixed and as u said its the problem with the connection.. i got the tecnical person to fix the problem. thanks once again.

---

