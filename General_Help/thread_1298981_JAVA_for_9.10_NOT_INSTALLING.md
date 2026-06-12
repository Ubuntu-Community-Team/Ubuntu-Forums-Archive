---
title: "JAVA for 9.10 NOT INSTALLING?"
date: 2009-10-23
forum: General Help
---

### Post by MichaelDance on 2009-10-23
Hey, sorry to bother you guys as other people who really need help need you, but i carnt install JAVA can you help me please.

---

### Post by prem1er on 2009-10-23
How did you try to install it?

---

### Post by MichaelDance on 2009-10-23
> **prem1er said:**
> How did you try to install it?

Via the Java Website

---

### Post by ColdFFF on 2009-10-23
Do you want to install the Java Runtime Environment (so you can run Java based apps) or the Java SDK (so you can develop them)?

---

### Post by MichaelDance on 2009-10-23
> **ColdFFF said:**
> Do you want to install the Java Runtime Environment (so you can run Java based apps) or the Java SDK (so you can develop them)?
Java Runtime Environment please

---

### Post by QIII on 2009-10-23
You can install Update 15 from the repos.

Unless you need Update 16 (see poster's question above), Update 15 should do OK.

There may be some security issues with Update 15.  I say MAY.  Depends what you are using it for.  I wouldn't do any development for clients using it.

I was able to install Update 16 on my Karmic 64 bit test machine before the RC came out.  I can uninstall it and see what happens.

I just installed the RC as my primary on my "production/every day use" machine, but just installed Update 15 from the repos at this point.

I had planned to install Update 16 this weekend when I have time.  If this isn't marked as solved by then, I'll try to get back with news.

---

### Post by Mighty_Joe on 2009-10-23
> **QIII said:**
> You can install Update 15 from the repos.

Unless you need Update 16 (see poster's question above), Update 15 should do OK.

I'm running 9.04 and got JRE 1.6.0_16-b01 from the repos.

---

### Post by QIII on 2009-10-23
I may have had Update 16 from the repos on Jaunty as well, now that you mention it.  I may not have actually used Sun's file to install from.

Interesting.

I'll have to take a look at that tonight.  

I usually install from the terminal, but this time I installed from Synaptic.  I wouldn't think there would be a difference between the two, since Synaptic is just apt in a slick suit and tie.

---

### Post by Monotoko on 2009-10-23
The ubuntu-restricted-extras package comes with the JRE as well as other codecs and flash.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by QIII on 2009-10-23
Here's the scoop:  Java Update 16 is NOT IN THE KARMIC REPOSITORIES and likely will not be.  Ubuntu is moving to OpenJDK.

So, if you want to install Sun Java 6, you'll have to do this:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

I just ran through it.  It is very straight forward.

---

### Post by PerfectReign on 2009-10-24
> **QIII said:**
> Here's the scoop:  Java Update 16 is NOT IN THE KARMIC REPOSITORIES and likely will not be.  Ubuntu is moving to OpenJDK.
Woah! That's not a good thing.

Why would Ubuntu do this? 

As for using the hack method, if the JRE/JDK updates as a result of a security hole, the OS won't be able to auto-patch.

---

### Post by QIII on 2009-10-24
> **PerfectReign said:**
> Woah! That's not a good thing.

Why would Ubuntu do this? 

As for using the hack method, if the JRE/JDK updates as a result of a security hole, the OS won't be able to auto-patch.

No.  Not a good thing at all.  This is something to address with Canonical.  Arrogantly assuming that they should only include OpenJDK because it is open source is flying in the face of those of us who develop in Java with client specifications for Sun's Java.  Assuming that the "good alternative" of OpenJDK is a valid test of how a client's application will work in Sun's JRE is foolish.

And you'll have to keep an eye on updates, use the "uninstall" instructions at the bottom of his tutorial and reinstall future Updates.

I'm also going to have to figure out how to get the most recent SDK/JDK.  To run the .bin to install it requires libstdc++5, which is not in the Karmic repositories...

---

### Post by MichaelDance on 2009-10-24
> **QIII said:**
> Here's the scoop:  Java Update 16 is NOT IN THE KARMIC REPOSITORIES and likely will not be.  Ubuntu is moving to OpenJDK.

So, if you want to install Sun Java 6, you'll have to do this:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

I just ran through it.  It is very straight forward.

Thanks Mate its is easier and does the job

---

### Post by MichaelDance on 2009-10-24
> **Monotoko said:**
> The ubuntu-restricted-extras package comes with the JRE as well as other codecs and flash.

```
sudo apt-get install ubuntu-restricted-extras
```

Works too :) Thanks Mate

---

