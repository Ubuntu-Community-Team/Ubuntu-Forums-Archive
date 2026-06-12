---
title: "Wireless Is Disabled"
date: 2011-05-21
forum: General Help
---

### Post by prettymess on 2011-05-21
Okay, so I just installed ubuntu alongside Windows 7, and it's saying wireless is disabled. I clicked "enable wireless," and the box has a check mark now, but it's still saying that wireless is disabled. I restarted my computer just to see if that'd do it, but it's still not working. Any ideas?

---

### Post by sauravd07 on 2011-05-21
i think ur wireless device is not supported by ubuntu or there is some internal hardware issue...
so i wud suggest 
1> to connect via any wired net access medium and download the wireless driver from official site.Install it then it should work.
2>if no official ubuntu driver is available then goto ubuntu software center and install Ndiswrapper driver installation tool...it can install almost any wifi device.

---

### Post by prshah on 2011-05-21
> **prettymess said:**
> it's saying wireless is disabled.  Any ideas?

Do you have a hardware "switch" or toggle button to enable/disable wireless (Eg, Fn+F4 or such like?). If not, or unsure, please post some information about your hardware for more relevant troubleshooting (Eg, laptop/desktop, model#, wifi model/brand, etc).

---

### Post by I&#9829;HTML5 on 2011-05-21
Press Control-Alt-T and then enter ```
rfkill list all
```. Paste the results into a post.

---

### Post by prettymess on 2011-05-21
I figured it out; all it took was:
```
sudo modprobe -r acer-wmi
```

---

