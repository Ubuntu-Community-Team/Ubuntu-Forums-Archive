---
title: "Visual effects with open source ati driver?"
date: 2009-07-10
forum: General Help
---

### Post by lunarmelody on 2009-07-10
Hello all- 
After trying (and failing) to get fglrx running on my machine, I'm running pretty happily with the open source ati drivers.  I'm curious, however, if it is possible to run the compiz visual effects with the open source driver.  From what I've seen on the forums, the main hangup seems to be lack of 3D support from the drivers.  However, running ```
glxinfo | grep "direct rendering"
``` returns ```
direct rendering: Yes
```so should it work for me?  Trying to enable them through the Appearance window fails, giving me a popup window indicating that desktop effects could not be enabled.  

Should this work for me?  If so, does anyone know what I can do to fix it?

Thank you in advance.

---

### Post by Legace on 2009-07-10
What card do you have?

---

### Post by lunarmelody on 2009-07-10
I have an ATI Radeon HD 4670.

---

### Post by Legace on 2009-07-10
> **lunarmelody said:**
> I have an ATI Radeon HD 4670.

Nope, the open soruce drivers don't support 3D acceleration.. yet.. :)

---

### Post by masux594 on 2009-07-10
Hmm.. with an ATI 4670, u should be able to install the ATI proprietary Catalyst.. Have u tried without success?

Sysc, A

---

### Post by Legace on 2009-07-10
You should try [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) to get the FGLRX driver working. Worked for me on a 4670, but I had to unistall FGRLX after I found out that it doesn't support modelines :(

---

### Post by libra1780 on 2009-07-10
unfortunately none of the HD series has 3d support with the open-source drivers. the proprietary is doing fine, but still got a lot of bugs. i have a HD3650 and i had only to install the latest drivers found on amd homepage.

---

### Post by lunarmelody on 2009-07-11
> **masux594 said:**
> Hmm.. with an ATI 4670, u should be able to install the ATI proprietary Catalyst.. Have u tried without success?

Sysc, A

I was able to install it, but I couldn't get it working with a dual monitor setup (I posted about that [here]("http://ubuntuforums.org/showthread.php?t=1208065")).  After using it with one monitor for a few hours, the graphics glitched and I had to restart my machine in order to interact with anything, so I went back to the open source drivers.

---

