---
title: "Conky Default Config ONO"
date: 2011-01-19
forum: General Help
---

### Post by GeissT on 2011-01-19
Hey,

So i have just tried out Conky and I really like it. But I just cant  seem to find the default/sample conky config. Yes i know that i can use  others ones but i want one that is basically what people start with.

If anyone could help please post.

GeissT

---

### Post by Hippytaff on 2011-01-19
Hi and welcome
 
As far as I'm aware there isn't a 'standard' conky config file. Just a matter of searching to find the most basic one

---

### Post by Hippytaff on 2011-01-19
Was trying to edit my post but it's not working (forum troubles)
 
was going to edit it with Hi and Welcome (I always forget the pleasanrties :-) )

---

### Post by GeissT on 2011-01-19
Hey,

Thanks for the response.

Do you think it would be a good idea for me to build from scratch using the following resources:

[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)
[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

Thanks,

GeissT

---

### Post by GeissT on 2011-01-19
Hey,

Thanks for the response.

Do you think it would be a good idea for me to build from scratch using the following resources:

[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)
[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

Thanks,

GeissT

---

### Post by m_duck on 2011-01-19
I'm not sure about Ubuntu specifically, but generally the default Conky configuration file is:```
/etc/conky/conky.conf
```
So to take that as your base, copy it to your home directory as .conkyrc and edit that.```
cp /etc/conky/conky.conf ~/.conkyrc
```
Creating a Conky configuration file from scratch would be quite a lot of effort, but those two resources are good when modifying the stock config. Also useful is the Conky screenshots thread on these forums, along with the plethora of configs that can be found lying around the internet.

---

### Post by GeissT on 2011-01-19
> **m_duck said:**
> I'm not sure about Ubuntu specifically, but generally the default Conky configuration file is:```
/etc/conky/conky.conf
```So to take that as your base, copy it to your home directory as .conkyrc and edit that.```
cp /etc/conky/conky.conf ~/.conkyrc
```Creating a Conky configuration file from scratch would be quite a lot of effort, but those two resources are good when modifying the stock config. Also useful is the Conky screenshots thread on these forums, along with the plethora of configs that can be found lying around the internet.

Thanks.

This worked great. I just need to know how to stop it from flickering? Each time it updates?

GeissT

EDIT: Dont worry bout the flicker issue, i fixed it.

---

### Post by m_duck on 2011-01-19
The [Conky FAQ](http://conky.sourceforge.net/faq.html) is also good ;)

But the option in question is:```
double_buffer yes
```
Put that above ***TEXT*** in .conkyrc.

---

### Post by GeissT on 2011-01-19
Thanks, 

I got that sorted before you posted. I remembered from my last Conky experience.

GeissT

PS: How do i make the thread solved?

---

### Post by m_duck on 2011-01-19
In 'Thread Tools' perhaps?

---

### Post by m_duck on 2011-01-19
In 'Thread Tools' perhaps? I'm not positive though.

---

### Post by MiKOTRON on 2011-01-19
Oh sorry!

---

### Post by Hippytaff on 2011-01-19
this is anice conky thread - lost of conkyrc files and screenshots :-)

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by Hippytaff on 2011-01-19
this is anice conky thread - lost of conkyrc files and screenshots :-)

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by GeissT on 2011-01-19
Thank you for your sarcastic but helpful reply.

---

### Post by GeissT on 2011-01-19
Thanks Hippy,

I was looking there but i wanted to build my own from the basic one.

Thanks though, ill use that thread as a reference.

GeissT

---

### Post by m_duck on 2011-01-20
> **GeissT said:**
> Thank you for your sarcastic but helpful reply.

Sorry, it wasn't meant sarcastically. It's hard to convey oneself properly in forums. I only said it like that because I actually don't know; I've not started a thread here before and so have never done it! I just remember thread tools being mentioned previously for marking a thread as solved.

---

### Post by GeissT on 2011-01-20
Haha. Ok then. Sorry then.

---

