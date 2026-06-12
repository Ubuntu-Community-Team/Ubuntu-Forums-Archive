---
title: "Help about libasound2"
date: 2010-03-03
forum: General Help
---

### Post by BlooD Master on 2010-03-03
This is first time for me to use ubunto. I tried to install Skype and i can`t it`s showing this message: Error:Dependency is not satlsfiable: libasound2

Sorry for my bad english

---

### Post by gradinaruvasile on 2010-03-03
What version of Ubuntu and what version of Skype?

---

### Post by BlooD Master on 2010-03-03
The latest version of Skype 34bit and where i can see what version am useing ? I am asking everything like this because i don`t know nothung about ubuntu yet:(

---

### Post by huangweiqiu on 2010-03-03
Did you install it via apt-get? if so ,it should be no dependency problem .Please just try to reinstall it .

---

### Post by BlooD Master on 2010-03-03
I tried and it shows the same i thing that i have an old version of libasound

---

### Post by gradinaruvasile on 2010-03-03
And what version do you have?
Open a terminal and type in:

aptitude show libasound2 | grep Version

What does it return?

---

### Post by BlooD Master on 2010-03-03
Version: 1.0.13-1ubuntu5

---

### Post by karthick87 on 2010-03-03
To get Ubuntu version

```
lsb_release -a
```

---

### Post by gradinaruvasile on 2010-03-03
> **BlooD Master said:**
> Version: 1.0.13-1ubuntu5

Dude that's ancient. Where did you get that CD? Go to 

[http://www.ubuntu.com/]("http://www.ubuntu.com/")

And download version 9.10 and install that one.

---

### Post by BlooD Master on 2010-03-03
But i am not allowed to reinstall the operative sistem because this is my mothers computer from work can i upgrade somehow?

---

### Post by BillyRuffian on 2010-03-04
I have the same problem - trying to install Skype, and all I get is that "Dependency is not satisfiable: libasound2" error message.

What I've done so far:

1. I trawled through all the online help, which pointed to loading libasound2 and the other things that it depends on - well, they were all loaded, according to Synaptic Package Manager.

2.  The next thing all the online help suggested was upgrading, so I went to Upgrade Manager and told it to bring this system up to date.  The version I have, according to the Terminal commands given above is 8.04.4 LTS.  (I see from the Ubuntu site that 9.10 is available - why didn't it tell me about that version?)  This system has been on version 8 for at least a couple of months.

3.  The libasound2 version is 1.0.15-3ubuntu4

What's stopping Skype from installing now? 

The other tangential question is: why did Skype install cleanly on my Ubuntu machine, but not this one (my Mum's)?  After hours of frustration I'm looking forward to hearing your suggestions.

 BTW, I'm a novice, as you can guess - any command line stuff will need to be VERY specific.

---

### Post by Francewhoa on 2010-03-05
Same issue here. **The following worked for me [http://ubuntuforums.org/showpost.php?p=8919096&postcount=6](http://ubuntuforums.org/showpost.php?p=8919096&postcount=6)**

---

### Post by BillyRuffian on 2010-03-05
Ah, what a relief - Skype now works on this machine!  Wasn't quite as straightforward as suggested and don't ask me what I did to get it working 'cos I'm not sure I'd be able to repeat it.

Many thanks for the link - I'd all but given up on Skype, and am getting a pretty jaundiced view of Ubuntu as well.

---

