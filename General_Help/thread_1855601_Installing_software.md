---
title: "Installing software"
date: 2011-10-06
forum: General Help
---

### Post by AV Town Crier on 2011-10-06
I go to the ubuntu software center and click on install and nothing happens.
Help.
Thanks

---

### Post by stlsaint on 2011-10-06
Have you tried using apt-get via cli?

---

### Post by Frogs Hair on 2011-10-06
Try running the update manager run the following commands in the terminal   and try again .```
sudo apt-get update
``` ```
sudo apt-get upgrade
```

---

### Post by MG&amp;TL on 2011-10-06
There are several ways of doing things.

1. Run: ```
software-center
``` in a terminal, try to install a package, and post what comes up in the terminal here so we can see what's wrong.

2. Try *synaptic, *or APT. *Synaptic *is user-friendly, whereas apt- uses the following syntax: ```
sudo apt-get install <package> <anotherpackageifyouneed> 
```

---

### Post by AV Town Crier on 2011-10-06
Still problems. How do install adobe flash?

---

### Post by AV Town Crier on 2011-10-06
I just get error not found

---

### Post by AV Town Crier on 2011-10-06
When I go to down load I get a message box  to choose application but there is none to choose from.
All I want is to install adobe flash. It seems so difficult.

---

### Post by joshthechamp14 on 2011-10-06
sudo apt-get install -f
Try that and to install flash [http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)

---

### Post by AV Town Crier on 2011-10-06
Miracles of miracles I got it.
Thanks a million!!!!

But there is no sound? Help again
thanks

---

### Post by joshthechamp14 on 2011-10-06
Make sure ubuntu isn't on mute, when you install it, it comes on mute for some reason

---

### Post by joshthechamp14 on 2011-10-06
Do you mean there is no sound with flash??

---

### Post by AV Town Crier on 2011-10-06
No its on. When I first boot up it plays the opening sounds.
Do you know why the s-video output is in B&W in ubuntu 8 it was in color.

---

### Post by AV Town Crier on 2011-10-06
yes. On youtube.

---

### Post by AV Town Crier on 2011-10-06
> **joshthechamp14 said:**
> Make sure ubuntu isn't on mute, when you install it, it comes on mute for some reason
no it works ok at start up. no youtube sound

---

### Post by MG&amp;TL on 2011-10-06
```
sudo apt-get install ubuntu-restricted-extras
```

works for me.

---

### Post by AV Town Crier on 2011-10-06
> **MG&TL said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```

works for me.
Did it. It went thru the process and it ended with end user agreement. It said OK at bottom. I couldn't click or do anything so I exited terminal. But still no sound.

---

### Post by AV Town Crier on 2011-10-06
> **AV Town Crier said:**
> Did it. It went thru the process and it ended with end user agreement. It said OK at bottom. I couldn't click or do anything so I exited terminal. But still no sound.
When I go to ubunto software center it shows that adobe flash is installed. But no sound.
I'll try a reboot and let you know.

---

### Post by MG&amp;TL on 2011-10-06
Run the restricted-extras command again. You have to navigate with the TAB key and press RETURN to click. It's a CLI.

---

### Post by joshthechamp14 on 2011-10-07
> **AV Town Crier said:**
> no it works ok at start up. no youtube sound
Yes it will work at startup even if mute is on, so try again and un-mute ubuntu. I have had this same problem many times and that always fixes it.

---

