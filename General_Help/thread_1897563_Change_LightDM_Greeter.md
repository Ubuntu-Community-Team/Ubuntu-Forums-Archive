---
title: "Change LightDM Greeter"
date: 2011-12-19
forum: General Help
---

### Post by dmoconnell on 2011-12-19
Hi. Like the title says, I'm trying to Change the LightDM Greeter from the unity-greeter to lightdm-gtk-greeter. So far all I have successfully done is make my computer not boot,( I changed the lightdm.conf greeter session) 

When I tried to change it via terminal using this command
```
sudo lightdm --greeter-session=lightdm-gtk-greeter

```
it gave me the following output 
```
Failed to use bus name org.freedesktop.DisplayManager, do you have appropriate permissions?
```

what am I missing? 
thanks 
Dm

---

### Post by dino99 on 2011-12-19
instead of using "sudo", try with "gksu" to see if that makes a difference. But why are you doing that ?

---

