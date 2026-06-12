---
title: "Virtual Box Questions"
date: 2010-08-07
forum: General Help
---

### Post by maknib on 2010-08-07
Hey guys it's me again

I have windows installed through virtual Box now but i have some questions.

When i make it full screen it goes full screen but Windows stays in the middle of the screen small and doesn't adjust to the full screen. Can you make windows completely take up the full screen

Can i access folders on my ubuntu drive ? i have a file in downloads i want in windows but don't want to reinstall it

---

### Post by neoargon on 2010-08-07
For that you have to install virtualbox guest addons . For that , start windows in virtualbox ,click on device menu . click on install "guest addons"

It is better you install guest addons when windows is booted in safe mode . for that, press F8 while windows is booting

---

### Post by maknib on 2010-08-07
> **neoargon said:**
> For that you have to install virtualbox guest addons . For that , start windows in virtualbox ,click on device menu . click on install "guest addons"

It is better you install guest addons when windows is booted in safe mode . for that, press F8 while windows is booting

ok thanks, i'm trying that now it's asked me to download a cd image  so lets see

---

### Post by maknib on 2010-08-07
ok so i installed the guest services addon and now the full screen is opening full screen.

i'm still confused on how to access some folders from ubuntu within windows

---

### Post by neoargon on 2010-08-07
> **maknib said:**
> ok so i installed the guest services addon and now the full screen is opening full screen.

i'm still confused on how to access some folders from ubuntu within windows

For that you will have to use shared folders feature of virtualbox . While running windows in virtualbox, click on devices menu . Then click on shared folder . Then add whatever the folder you wish to see in windows.

---

