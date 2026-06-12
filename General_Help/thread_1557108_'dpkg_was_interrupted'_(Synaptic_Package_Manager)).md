---
title: "'dpkg was interrupted' (Synaptic Package Manager))"
date: 2010-08-20
forum: General Help
---

### Post by Fallen_Enigma on 2010-08-20
I keep getting an error message when opening the Synaptic Package Manager.

"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

I also can't install any software from the software center. When I run the line in terminal, I get lost. Can someone please help me?

---

### Post by ronnielsen1 on 2010-08-20
Open up a terminal by going to Applications > Accessories > Terminal and typing the following into it

sudo dpkg --configure -a

---

### Post by Fallen_Enigma on 2010-08-20
> **Fallen_Enigma said:**
> When I run the line in terminal, I get lost.
^^

---

### Post by ronnielsen1 on 2010-08-20
That's the only place to fix it right now. If you get lost, copy and paste all of the output after you copy and paste the following in a terminal - type in your password when prompted

```
sudo dpkg --configure -a 	
```

---

### Post by ronnielsen1 on 2010-08-21
Give up?

---

### Post by faim2600 on 2010-08-29
I believe the issue is not typing the space between "configure" and "-a." That's how it appeared to be typed in the error message. When I typed it without the space it brought a whole different menu up.

Typing it correctly solved the problem for me.  Thanks.

---

