---
title: "Unity customization using CCSM doesn't work"
date: 2012-01-01
forum: General Help
---

### Post by John Abruzzi on 2012-01-01
Hello All,

I use Ubuntu 11.10 inside Windows using VirtualBox. When opening CompizConfig Settings Manager and trying to change some Unity feature like "Never hide launcher" or "Launcher icon size", it doesn't take any effect. Do you know how can I solve this issue?

Thanks in advance.

---

### Post by howefield on 2012-01-01
If it is the same issue I had, updating guest additions worked and a logout/login was required.

Sounds obvious but you never know.

---

### Post by John Abruzzi on 2012-01-01
I've already done this procedure, but changes in the Unity Plugin still have no effect.

---

### Post by vpharry on 2012-01-01
update your system and then try... had the same issue but the update fixed it..:D

---

### Post by John Abruzzi on 2012-01-01
I've just checked for updates and there are no updates to install. I don't know if the problems is in the CCSM or in thr Unity plugin.

---

### Post by vpharry on 2012-01-01
Try>  unity --replace. If its still not working try running > unity --reset and then change the ccsm settings. If you updated from 11.04 you are probably missing libdconf0. Install it and you should be fine. [libdconf0]("http://packages.ubuntu.com/libdconf0")
Please note that if anything fails restart your system. I am not too sure of these commands so please backup your system before trying anything

---

### Post by Paddy Landau on 2012-01-01
> **vpharry said:**
> ... please backup your system before trying anything
It's in a VM, so the OP can simply snapshot the system.

The unity --replace and --reset commands will reset your Compiz settings, so you will lose any customisations you made to it.

---

### Post by vpharry on 2012-01-01
@Paddy: thats what i want him to do.... reset everything and try again if it works... cant think of any other solution

---

### Post by John Abruzzi on 2012-01-01
Tried commands unity --replace 			 		 	 	 unity --reset, but behavior is the same, it seems that CCSM Unity parameter changes have no effect.

---

