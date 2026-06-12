---
title: "i CANT BELIEVE THIS"
date: 2010-12-30
forum: General Help
---

### Post by Totally Annoyed on 2010-12-30
OMG, i am in the process of transferring from windows to ubuntu and all i want to is allow this OS to be able to see my Iomega Network Drive. Why is this so difficult?!?!?!

---

### Post by matt_symes on 2010-12-30
Hi

> **i CANT BELIEVE THIS** 			
 			 			 		   		 		 		OMG, i am in  the process of transferring from windows to ubuntu and all i want to is  allow this OS to be able to see my Iomega Network Drive. Why is this so  difficult?!?!?!


Calm down. Ranting on this forum will not get you anywhere.

Having said that, you are in the right place to ask (although i might not be the best person to answer).

Are you having trouble getting Ubuntu to see your iomega network drive?

Kind regards

---

### Post by Totally Annoyed on 2010-12-30
> **matt_symes said:**
> Hi



Calm down. Ranting on this forum will not get you anywhere.

Having said that, you are in the right place to ask (although i might not be the best person to answer).

Are you having trouble getting Ubuntu to see your iomega network drive?

Kind regards


Yes I am having problems with my iomega being discovered. I have went the route of enabling ftp and entering the ip/port/user name that haven't work. I have been goggling for at least two hours to no avail. I read in PC World that this OS is better than Windows so I decided to give it a try. I think i will like it as soon as i get over the learning curve.

thanks in advance

---

### Post by Rubi1200 on 2010-12-30
It would be helpful if you could tell us what exact steps you have taken to try and discover the drive.

Are you doing this from a LiveCD?

The more information you provide us, the better we can help you.

---

### Post by matt_symes on 2010-12-30
Hi

I do not have an iomega network drive myself but i will do some research for you and try to find out the best way to access it from Ubuntu.

I'm sure others on this forums do have iomega drives and they will be able to supply an answer for you, but you will have to be a bit patient.

Kind regards

---

### Post by Rubi1200 on 2010-12-30
Hi,
take a look here:
[http://ubuntuforums.org/showpost.php?p=6537536&postcount=3](http://ubuntuforums.org/showpost.php?p=6537536&postcount=3)

Does not seem to be the ideal solution, but at least it points you in the right direction.

I would also wait to see what matt_symes manages to come up with.

---

### Post by IWantFroyo on 2010-12-30
Try going into System-Administration-Additional Drivers. Usually, if there's a driver available for something, it will be in there. If you have something like a wireless card it will almost certainly have a driver or two in there.

---

### Post by Grenage on 2010-12-30
Can you not mount the drive using fstab, as per below?

[http://ccollins.wordpress.com/2008/10/27/home-network-hard-drives/](http://ccollins.wordpress.com/2008/10/27/home-network-hard-drives/)

Regarding PcWorld saying that Linux is 'better' - it's different.  It will take you a while to get used to how things work, because it's not a Windows clone.

---

### Post by Idefix82 on 2010-12-30
> **IWantFroyo said:**
> Try going into System-Administration-Additional Drivers. Usually, if there's a driver available for something, it will be in there. If you have something like a wireless card it will almost certainly have a driver or two in there.

IWantFroyo, please stop posting the same off-topic reply everywhere. Just because you have just discovered the "Additional drivers" section doesn't mean that it will solve all hardware problems for all Ubuntu users.

---

### Post by drewsus on 2010-12-30
I can't really believe I am responding to such a spaz thread, but here goes... (future reference: Give informative title and body. Be verbose. Don't freak out. Stay calm).

You may need to install Samba: 
```
sudo apt-get install samba
```

Restart. 

Go to Place -> Network 
and see if you can spot it there. I really don't know how the Iomega network drive interfaces with a network, but this might just be what you need.

---

### Post by Totally Annoyed on 2010-12-30
Thank you all for your responses and suggestions to my question. I figured out what was wrong, it was that i had the firewall enabled on. As soon as I disabled it i was able to get to my network drive. Now I just have to figure out how o create a rule to allow it through the firewall. 

Again thank you all very much.

---

### Post by nothingspecial on 2010-12-30
Hi,

Try reading this

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by trinitydan on 2010-12-30
You also might want to have a look at this [article]("http://linux.oneandoneis2.org/LNW.htm") when you get time.  Welcome to Ubuntu Linux!  In time things will become less frustrating.

---

### Post by Idefix82 on 2010-12-30
I love users who fail to configure their system correctly and then come here to rant and to shout "I CAN'T BELIEVE THIS".

---

### Post by Totally Annoyed on 2010-12-30
> **Idefix82 said:**
> I love users who fail to configure their system correctly and then come here to rant and to shout "I CAN'T BELIEVE THIS".

I love user's who dont contribute to the thread..

---

### Post by Yellow Pasque on 2010-12-30
Please mark thread solved and try and be a bit less abrasive in the next one you make.

---

### Post by Idefix82 on 2011-01-01
> **Totally Annoyed said:**
> I love user's who dont contribute to the thread..

There was nothing to contribute. Your original post was address to Your God (who is most probably not registered on this forum) and didn't contain any request of help, only the question why something was difficult (followed by a sequence of punctuation that doesn't have a syntactical meaning) and it's not clear to me what kind of answer such a question expects:

> **Totally Annoyed said:**
> OMG, i am in the process of transferring from windows to ubuntu and all i want to is allow this OS to be able to see my Iomega Network Drive. Why is this so difficult?!?!?!

---

### Post by nothingspecial on 2011-01-01
> **Idefix82 said:**
> There was nothing to contribute. Your original post was address to Your God (who is most probably not registered on this forum) and didn't contain any request of help, only the question why something was difficult (followed by a sequence of punctuation that doesn't have a syntactical meaning) and it's not clear to me what kind of answer such a question expects:

This is funny.

You should look at what you write before you criticize others.

---

### Post by Totally Annoyed on 2011-01-01
> **Idefix82 said:**
> There was nothing to contribute. Your original post was address to Your God (who is most probably not registered on this forum) and didn't contain any request of help, only the question why something was difficult (followed by a sequence of punctuation that doesn't have a syntactical meaning) and it's not clear to me what kind of answer such a question expects:

Thanks for the insight, i will do better......(to avoid a senseless discussion)

---

### Post by MG&amp;TL on 2011-07-20
Just sidestepping the fighting, (now, now, children ! :P) You said PC world says Ubuntu's a better OS? 

Two things:

a) that's a breakthrough!

b) why do they still ship windows then?

Just looked at the date of this thread. oops.

---

