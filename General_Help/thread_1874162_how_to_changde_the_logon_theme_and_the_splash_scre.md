---
title: "how to changde the logon theme and the splash screen?"
date: 2011-11-02
forum: General Help
---

### Post by khaled.battah on 2011-11-02
hello guys I was wondering how to change the Log on screen and the splash screen by some themes or by my own photos??
like this:
[http://ubuntu-art.org/content/show.php/Fusion-GX-v00+%5B200911-21%5D?content=115862](http://ubuntu-art.org/content/show.php/Fusion-GX-v00+%5B200911-21%5D?content=115862)
 and this for the splash screen:
[http://ubuntu-art.org/content/show.php/Oxygen_widescreen?content=92398](http://ubuntu-art.org/content/show.php/Oxygen_widescreen?content=92398)
can anyone tell me what program do i install I tryed a theme whish requered a usplash but an error ocured can you tell me what shoul I do?
I am using ubuntu 10.10 LTS

---

### Post by crossedout on 2011-11-06
You can change the Logon background using Simple LightDM Manager:

```
sudo apt-add-repository ppa:claudiocn/slm
sudo apt-get update
sudo apt-get install simple-lightdm-manager
```


Change splash screen:

Search for Plymouth-theme in the Software Center, install one and then:
```
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u
```

Manually select the one you want to use.


-Xout

---

