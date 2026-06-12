---
title: "synaptic programs manager error"
date: 2010-11-09
forum: General Help
---

### Post by BeginnerLinuxUser on 2010-11-09
I'm new to the linux system and I just tried to download skype but got the limbsound2 error. I checked out one of them threads on where to download it and a poster said that I should install it in synaptic programs manager. When I tried opening my synaptic programs manager it got this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Is there anything I can do to fix this? I rely on skype a lot for communication with family over seas since I don't have long distance calling. Thanks! 
Also, I am very very sorry if this question has already been answered. I tried searching "synaptic" and nothing came up.

---

### Post by TeoBigusGeekus on 2010-11-09
Do what it says: 
Open a terminal and give
```
sudo dpkg --configure -a
```

---

### Post by BeginnerLinuxUser on 2010-11-09
> **TeoBigusGeekus said:**
> Do what it says: 
Open a terminal and give
```
sudo dpkg --configure -a
```

I'm sorry, I'm not sure what a terminal is. :redface:
Can you please tell me how to open a terminal?
And thank you for the response :)

---

### Post by TeoBigusGeekus on 2010-11-09
Applications>Accessories>Terminal
Type the command and press enter.
You'll be prompted to give your password - type it and press enter (you won't see anything while typing).

---

### Post by BeginnerLinuxUser on 2010-11-09
> **TeoBigusGeekus said:**
> Applications>Accessories>Terminal
Type the command and press enter.
You'll be prompted to give your password - type it and press enter (you won't see anything while typing).

Thank you. :) I'm still waiting for it to get done setting everything up, so as soon as it finishes I will try to reopen synaptic.

---

