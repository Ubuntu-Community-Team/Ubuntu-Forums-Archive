---
title: "change login screen background"
date: 2012-02-04
forum: General Help
---

### Post by m.mohan100 on 2012-02-04
Can anyone help me to change login screen backgroung in ubuntu11.10? How can I add pictures into /usr/share/backgrounds/?

---

### Post by WthIteh on 2012-02-04
Open "/etc/lightdm/unity-greeter.conf" file and in the "[greeter]" section change background like this:
```
background=/path/to/some/image/file.jpeg
```

---

### Post by m.mohan100 on 2012-02-04
How can I locate the image if the image is in my user a/c?
I think ubuntu can't locate the image without my permission. So, where can I place the image file? How can I place the image file outside the location:  /home/<user account>?

---

### Post by grahammechanical on 2012-02-04
Do what I do. Use Simple LightDM Manager.

[http://www.ubuntugeek.com/simple-lightdm-manager.html]("http://www.ubuntugeek.com/simple-lightdm-manager.html")

You may be interested to know that in 12.04 the static background wallpaper that each user selects becomes the background for their log-in screen. It does not work when the slide show is selected. So, I use Simple LightDM Manager to customize my log-in screen.

It might also interest you to know that the logo we see is actually a separate file called logo.png and Simple LightDM Manager can set another logo file as the logo. So, we can customize the logo as well.

Simple LightDM Manager does its stuff by copying your image file to its own folder and naming it file.png and then editing the LightDM configuration script to point to its own folder and not /usr/share/backgrounds/

Regards.

---

### Post by dagroves on 2012-02-04
> **grahammechanical said:**
> Do what I do. Use Simple LightDM Manager.

[http://www.ubuntugeek.com/simple-lightdm-manager.html](http://www.ubuntugeek.com/simple-lightdm-manager.html)

You may be interested to know that in 12.04 the static background wallpaper that each user selects becomes the background for their log-in screen. It does not work when the slide show is selected. So, I use Simple LightDM Manager to customize my log-in screen.

It might also interest you to know that the logo we see is actually a separate file called logo.png and Simple LightDM Manager can set another logo file as the logo. So, we can customize the logo as well.

Regards.

+1 to this, it is the easiest and quickest way to do this!

---

### Post by fragos on 2012-02-04
Another GUI option is Ubuntu Tweak found at [http://ubuntu-tweak.com](http://ubuntu-tweak.com). Under the Tweaks tab use "login Settings". You will need to enter your password with the Unlock button.

---

