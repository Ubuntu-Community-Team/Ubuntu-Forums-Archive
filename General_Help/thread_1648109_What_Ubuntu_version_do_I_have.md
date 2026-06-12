---
title: "What Ubuntu version do I have?"
date: 2010-12-18
forum: General Help
---

### Post by thelugnut on 2010-12-18
I downloaded Ubuntu 10.10 and installed it.
 
When I navigate as follows: System>About Ubuntu, I get the following:

> Ubuntu - Linux for Human Beings!

You are using Ubuntu 11.04
                - the Natty Narwhal - released in April 2011 and supported until October 2012.
	
 This confuses me. Any answers as to what is going on?

---

### Post by karthick87 on 2010-12-18
Have you upgraded your system??

---

### Post by Dave_L on 2010-12-18
What's the output from this shell command?

lsb_release -a

---

### Post by Frogs Hair on 2010-12-18
Open the system monitor and the current version is displayed in the system tab.

---

### Post by karthick87 on 2010-12-18
Post the output of,

```
lsb_release -a
```

---

### Post by ivanovnegro on 2010-12-18
> **thelugnut said:**
> I downloaded Ubuntu 10.10 and installed it.
 
When I navigate as follows: System>About Ubuntu, I get the following:


 This confuses me. Any answers as to what is going on?

It seems that you upgraded to Natty, the next Ubuntu version, how you did this?
You downloaded really the 10.10 Live CD and not another thing?
Maybe you configured something strange in your update manager to be yet possible to have the Alpha of Natty.

---

### Post by thelugnut on 2010-12-18
I downloaded the Ubuntu 10.10 cd and installed it. During the installation options I chose to enable updates while installing. Then, after installation, I again updated using the Update Manager. 
I checked the installation Cd and it is 10.10.
Now I know it appears that the updates have installed the upgrade, but in the Update Manager options I did not choose to allow upgrades.
Please see the attachment.

---

### Post by ivanovnegro on 2010-12-18
> **thelugnut said:**
> I downloaded the Ubuntu 10.10 cd and installed it. During the installation options I chose to enable updates while installing. Then, after installation, I again updated using the Update Manager. 
I checked the installation Cd and it is 10.10.
Now I know it appears that the updates have installed the upgrade, but in the Update Manager options I did not choose to allow upgrades.
Please see the attachment.

Strange, I see, your update manager has the correct settings.
Did you check the MD5sum of the 10.10 CD?
In the worst case you could make a new install, maybe with a different CD.

---

### Post by thelugnut on 2010-12-18
> Strange, I see, your update manager has the correct settings.
Did you check the MD5sum of the 10.10 CD?
In the worst case you could make a new install, maybe with a different CD. 
Yes, it is strange.
And yes, to the MD5sum question. Always do that.
And finally, the computer is running just fine. I am not going to make a new install yet. I have a suspicion that someone might have goofed up with a typo in the "About Ubuntu" box. I don't think it is really 11.04 because it seems to me it is way to early for the program to be running this smoothly. I've never seen even an "alpha" look this good. I think it is 10.10.

---

### Post by ivanovnegro on 2010-12-18
> **thelugnut said:**
> Yes, it is strange.
And yes, to the MD5sum question. Always do that.
And finally, the computer is running just fine. I am not going to make a new install yet. I have a suspicion that someone might have goofed up with a typo in the "About Ubuntu" box. I don't think it is really 11.04 because it seems to me it is way to early for the program to be running this smoothly. I've never seen even an "alpha" look this good. I think it is 10.10.

Do you care to say what is the actual output of:

```
lsb_release -a 
```like mentioned by the other posters?

---

### Post by karthick87 on 2010-12-18
I think your release upgrade should point Long Term Support Release..

[IMG]http://imgur.com/h6O1c.png[/IMG]

---

### Post by thelugnut on 2010-12-18
Sorry I missed that request before. This answers the question, doesn't it?

:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick

---

### Post by ivanovnegro on 2010-12-18
> **thelugnut said:**
> Sorry I missed that request before. This answers the question, doesn't it?

:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick

With that output it seems you have installed 10.10 and not Natty (11.04).

---

### Post by thelugnut on 2010-12-18
Which is what I suspected and posted.
It doesn't answer the question as to why the "About Ubuntu" states it is 11.04.
Thanks to all for commenting on this post. I will mark it as solved.

---

