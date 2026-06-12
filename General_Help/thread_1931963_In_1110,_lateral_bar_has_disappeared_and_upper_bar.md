---
title: "In 11/10, lateral bar has disappeared and upper bar is now with options as ever"
date: 2012-02-26
forum: General Help
---

### Post by Jayhawker on 2012-02-26
I have just installed 11/10 in a notebook. Everything was fine till the moment certain windows stuck to the upper bar ¿? But now, suddenly, it occurs something different: the lateral bar has disappeared and all services are, as usual in previous versions, in the upper bar: names as "Applications" and "places" have appeared in this upper bar and they display when applying the arrow. I very like this new lateral bar which now I can't dispose inexplicably. 

Please, is it a way to come back to the initial Ubuntu 11/10's look?

Thanks a lot

---

### Post by bigoops on 2012-02-26
Hmmm... Compiz Error? 

gksudo unity --reset 

in terminal, might help. This overrides the current unity config and reverts to default.

---

### Post by Jayhawker on 2012-02-26
Sorry, not quite an Ubuntu expert. Must "unity" be understood as "C".

I must inform my Ubuntu is inside Windows 7.

ANyway, I have tried your suggestion in a terminal, but nothing occurs; only a list of possible orders with gksudo, none of them meaning any possible reset. The terminal also informs --reset doesn't exist. 

What else can I do?

Thanks for your concern,  

> **bigoops said:**
> Hmmm... Compiz Error? 

gksudo unity --reset 

in terminal, might help. This overrides the current unity config and reverts to default.

---

### Post by Krytarik on 2012-02-26
> **Jayhawker said:**
> But now, suddenly, it occurs something different: the lateral bar has disappeared and all services are, as usual in previous versions, in the upper bar: names as "Applications" and "places" have appeared in this upper bar and they display when applying the arrow.
[..]
Please, is it a way to come back to the initial Ubuntu 11/10's look?
Apparently, now, you are being logged in to Gnome Classic; log out, and upon entering your login password, choose "Ubuntu" as the session option via the cog at the right of the login box (in LightDM, default in Oneiric 11.10; in GDM, via the drop-down menu at the bottom of the login box).

Regards.

---

### Post by Jayhawker on 2012-02-26
Thank You very much. It works! But the options of the cog were only three: Initially, it was in Gnome classic (you were right). There was also Gnome classic (no effects), and finally "Ubuntu 2d". I clicked this last one, and upon entering, the look were the one of 11/10 again. Nevertheless, the lateral bar has an odd behavior. Now, the basket, at the end of this lateral bar, is permanently visible, and the other buttons come behind it instead of bending, the basket included. 

Thanks anyway for your useful help and concern 


> **Krytarik said:**
> Apparently, now, you are being logged in to Gnome Classic; log out, and upon entering your login password, choose "Ubuntu" as the session option via the cog at the right of the login box (in LightDM, default in Oneiric 11.10; in GDM, via the drop-down menu at the bottom of the login box).

Regards.

---

### Post by Krytarik on 2012-02-26
> **Jayhawker said:**
> ... and finally "Ubuntu 2d". I clicked this last one, and upon entering, the look were the one of 11/10 again. Nevertheless, the lateral bar has an odd behavior. Now, the basket, at the end of this lateral bar, is permanently visible, and the other buttons come behind it instead of bending, the basket included.
Make sure the meta-package "ubuntu-desktop" is installed; this would also pull in the "unity" package (regular Unity), as a matter of dependency:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by Jayhawker on 2012-02-26
Thanks a lot. Once installed the "ubuntu-desktop", in the cog it appears one more choice: simply "ubuntu". I have selected it and after entering, all seems right. 

Thanks again. 

> **Krytarik said:**
> Make sure the meta-package "ubuntu-desktop" is installed; this would also pull in the "unity" package (regular Unity), as a matter of dependency:
```
sudo apt-get install ubuntu-desktop
```

---

