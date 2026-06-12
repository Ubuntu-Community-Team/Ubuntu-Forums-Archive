---
title: "No unity-greeter.conf file in /etc/lightdm/"
date: 2012-06-25
forum: General Help
---

### Post by drofart on 2012-06-25
I am running Ubuntu 12.04 with gnome-shell. I have two admin user accounts. Now, I used to know that in Precise we can set different different login wallpaper to different different user, so I tried with:

 ```
sudo dbus-send --system --print-reply --dest=org.freedesktop.Accounts /org/freedesktop/Accounts/User1001 org.freedesktop.Accounts.User.SetBackgroundFile string:/usr/share/backgrounds/Green-wallpaper-27.jpg
```  but to no avail.

 Then I tried  
```
sudo xhost +SI:localuser:lightdm sudo su lightdm -s /bin/bash gsettings set com.canonical.unity-greeter background '/path/to/the/wallpaper.png'
```  

It does change my login wallpaper but for all users.  

Then I tried to locate /etc/lightdm/unity-greeter.conf but I found that it is not there.

 So where is it and how can I set different login wallpapers for different users?

Regards,
Mrinal

---

