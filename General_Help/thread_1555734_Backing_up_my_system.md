---
title: "Backing up my system?"
date: 2010-08-18
forum: General Help
---

### Post by Buying_Some_Time on 2010-08-18
I start up my laptop, and it works great for about an hour but then it starts to make a loud scratching sound and I know that sound is my HD and after I have to shut it down (by holding the power button), it takes a few tries to get it to boot normally. So I'm pretty sure my HD is the problem but if anyone thinks it's something else, please let me know. Okay, so my question is how can I back up my system (I'm running Ubuntu 10.4)? Just in case something really bad happens. I remember there was a thread sometime ago and a guy there said something about a program that would create a iso of the whole system, and it would back up everything even programs and stuff. So can anyone help me with this? (Btw the search feature is not working for me) Also if you wanna buy me a new HD you can do that too XD. Thanks!

---

### Post by inameiname on 2010-08-18
I use Remastersys to backup my computer, and it does make a simple ISO for you to put on a disc or usb drive. Very easy.


[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

Although, if you are having software issues along with your hardware woes, I doubt it's wise to backup a system with troubles. But that's just me.

---

### Post by Buying_Some_Time on 2010-08-19
For some reason I can't install it. I followed the instructions on the site that you gave me but, it says that the "package could not be found", is there something I'm missing here?

---

### Post by inameiname on 2010-08-19
Hmmm, well I don't know. Let's see... did you:

sudo gedit /etc/apt/sources.list

...and add the following line to 'sources.list':

deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

...and then:

sudo apt-get update && sudo apt-get install remastersys

...?

That should do it.

---

### Post by Buying_Some_Time on 2010-08-19
> **inameiname said:**
> Hmmm, well I don't know. Let's see... did you:

sudo gedit /etc/apt/sources.list

...and add the following line to 'sources.list':

deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

...and then:

sudo apt-get update && sudo apt-get install remastersys

...?

That should do it.
Yes sir, I did that and it just says: E: Couldn't find package remastersys  :(

---

### Post by inameiname on 2010-08-19
That is strange. Perhaps their site is down or something, idk. Here is the deb file for remastersys, which I just downloaded from the site. Just install it and then see if it works.

---

### Post by Buying_Some_Time on 2010-08-19
Haha, thanks! I got it now. You're awesome!

---

### Post by inameiname on 2010-08-19
Coolz. Glad you got it all figured out. Enjoy. Remastersys rocks!

---

