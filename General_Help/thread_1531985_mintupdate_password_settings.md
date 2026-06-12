---
title: "mintupdate password settings"
date: 2010-07-15
forum: General Help
---

### Post by COKEDUDE on 2010-07-15
Could someone please tell me how to turn my password settings back on for mintupdate? Somehow it got turned off. I don't like how software can be updated without my password now.

---

### Post by hansdown on 2010-07-15
Hi COKEDUDE.

Click system> administration> software sources.

Click updates, and be sure to uncheck the box that says,"install security updates without confirmation".

---

### Post by COKEDUDE on 2010-07-15
I am using Mint. This is what my software sources looks like. 
[IMG]http://lookpic.com/d2/i2/1576/hHWwReUf.png[/IMG]
[http://lookpic.com/d2/i2/1576/hHWwReUf.png](http://lookpic.com/d2/i2/1576/hHWwReUf.png)

---

### Post by hansdown on 2010-07-16
Wow, I didn't realize There are some differences in our systems.

Which version are you using? Mintupdate has had some changes.

Try, mintupdate> preferences.

---

### Post by COKEDUDE on 2010-07-16
This is what I see. It doesn't have anything that I see that is related to passwords. 

[IMG]http://lookpic.com/d2/i2/1509/jFurH8HH.png[/IMG]
[http://lookpic.com/d2/i2/1509/jFurH8HH.png](http://lookpic.com/d2/i2/1509/jFurH8HH.png)

---

### Post by hansdown on 2010-07-16
Nice! Thanks COKEDUDE.

Click** update method**, and see if there is a setting for passwords.

---

### Post by ubunterooster on 2010-07-16
No, there is not.

---

### Post by hansdown on 2010-07-16
Thanks for answering my question, ubunterooster.

You wouldn't perchance, have an answer for the question, that COKEDUDE asked?

I don't have mint installed.

---

### Post by ubunterooster on 2010-07-16
I do not have the answer, it is slightly annoying though to have anyone able to update.

---

### Post by hansdown on 2010-07-16
> **ubunterooster said:**
> I do not have the answer, it is slightly annoying though to have anyone able to update.

That's cool.

I'm relying on my finely honed internet search skills.

---

### Post by COKEDUDE on 2010-07-16
> **hansdown said:**
> Nice! Thanks COKEDUDE.

Click** update method**, and see if there is a setting for passwords.

I wish it was there :(. 

[IMG]http://lookpic.com/d2/i2/1263/1hgR4Rp3.png[/IMG]
[http://lookpic.com/d2/i2/1263/1hgR4Rp3.png](http://lookpic.com/d2/i2/1263/1hgR4Rp3.png)

> **hansdown said:**
> Thanks for answering my question, ubunterooster.

You wouldn't perchance, have an answer for the question, that COKEDUDE asked?

I don't have mint installed.

I have a very annoying solution. It just seems like this is a simple feature to add to the program. 
```
ps -ef | grep [m]intUpdate
sudo kill -9 5208
```

---

### Post by hansdown on 2010-07-16
Keep us posted, COKEDUDE.

I hope that does the trick.

---

### Post by ubunterooster on 2010-07-17
That does work.

---

