---
title: "Ubuntu 10.04, screen is black after locking screen"
date: 2010-09-27
forum: General Help
---

### Post by ryan461 on 2010-09-27
Today my ubuntu 10 workstation has been acting strange. First when locking the screen, i come back and hit my usual spacebar to activate the login window, the mouse just flickers on and off. I have to physically reboot the machine at this point. What then happened was the dual monitor setup got off. I opened the nvidia control panel and set it to the one where each monitor is seperate (forget the name). I didnt like that, so set to twin view which could never properly work. The monitors were getting odd display signals, and the refresh rate was bad. So i removed the nvidia driver and went back to using preferences > monitors. So the monitor setup is fine now, just the locking issue still occurs. The video card is an nvidia quattro of some sort.

---

### Post by ryan461 on 2010-09-27
I have two screensaver applets in my preferences. One is screensaver, the other xscreensaver. I removed xscreensaver then reinstalled it. The desktop no longer can lock period. :(

---

### Post by ryan461 on 2010-09-28
bump

---

### Post by 7h3d4rk0n3 on 2010-09-28
When you uninstalled xscreensaver, you may have uninstalled something else along with it that was dependent on it. Not sure what packages may be dependent on it though.

---

### Post by ryan461 on 2010-09-28
> **7h3d4rk0n3 said:**
> When you uninstalled xscreensaver, you may have uninstalled something else along with it that was dependent on it. Not sure what packages may be dependent on it though.

Well I have reinstalled it since, and the problem was occuring before i uninstalled xscreensaver.

---

### Post by 7h3d4rk0n3 on 2010-09-28
How often do you have your machine set to lock when it is not being used?

---

### Post by ryan461 on 2010-09-28
> **7h3d4rk0n3 said:**
> How often do you have your machine set to lock when it is not being used?

It doesnt lock when the screensaver comes up, but i lock it whenever i leave my desk; corporate policy.

---

### Post by 7h3d4rk0n3 on 2010-09-28
Hm... have you tried messing with the power settings at all? Or seeing if it does it when the machine auto locks itself after a certain amount of time (ie 5 minutes)?

---

### Post by ryan461 on 2010-09-28
> **7h3d4rk0n3 said:**
> Hm... have you tried messing with the power settings at all? Or seeing if it does it when the machine auto locks itself after a certain amount of time (ie 5 minutes)?

If the screensaver comes on with the lock, same issue. If the screensaver doesnt lock, i can hit a key and my desktop reappears.

---

### Post by 7h3d4rk0n3 on 2010-09-28
So, it's definitely an issue with the locking. Have you done all the current updates? Also, what kind of video card are you using?

---

### Post by ryan461 on 2010-09-29
> **7h3d4rk0n3 said:**
> So, it's definitely an issue with the locking. Have you done all the current updates? Also, what kind of video card are you using?

yes, everythings updated. Its an nvidia quadro FX 330

---

### Post by 7h3d4rk0n3 on 2010-09-29
Any idea what driver you are using for it?

---

### Post by ryan461 on 2010-09-29
> **7h3d4rk0n3 said:**
> Any idea what driver you are using for it?

The nvidia version 173 drivers (whats recommended in the hardware drivers applet).

---

### Post by 7h3d4rk0n3 on 2010-09-29
Hm, so it doesn't seem to be a driver issue. My only other recommendation would be to reinstall all of the packages that control the locking of the computer. A Google search should be able to tell you what packages those might be.

---

