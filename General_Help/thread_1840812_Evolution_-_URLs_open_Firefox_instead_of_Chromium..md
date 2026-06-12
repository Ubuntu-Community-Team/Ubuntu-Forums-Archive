---
title: "Evolution - URLs open Firefox instead of Chromium."
date: 2011-09-08
forum: General Help
---

### Post by casbahdk on 2011-09-08
I have Xubuntu 11.04 installed on my AMD desktop and am experiencing problems with clicking on URLs in Evolution opening Firefox, despite Chromium being set as the default browser in the "preferred apps" panel. I have done a number of searches, but haven't found anything that worked, short of uninstalling Firefox.

---

### Post by haqking on 2011-09-08
> **casbahdk said:**
> I have Xubuntu 11.04 installed on my AMD desktop and am experiencing problems with clicking on URLs in Evolution opening Firefox, despite Chromium being set as the default browser in the "preferred apps" panel. I have done a number of searches, but haven't found anything that worked, short of uninstalling Firefox.


Not sure exaclty, may be to do with your DE

try here to see if this helps [http://live.gnome.org/Evolution/FAQ#How_can_I_set_the_default_browser_in_Evolution.3F](http://live.gnome.org/Evolution/FAQ#How_can_I_set_the_default_browser_in_Evolution.3F)

---

### Post by Bodsda on 2011-09-08
> **casbahdk said:**
> short of uninstalling Firefox.
 
Have you tried that? 
 
It may be a case of Evolution being unable to launch chromium, in which case uninstalling firefox and running Evolution from the command line should display error messages if that is the case.
 
Hope this helps,
Bodsda

---

### Post by casbahdk on 2011-09-08
Many thanks for the replies. The only solution that I could find was to uninstall Firefox.

---

### Post by casbahdk on 2011-09-17
> **haqking said:**
> Not sure exaclty, may be to do with your DE

try here to see if this helps [http://live.gnome.org/Evolution/FAQ#How_can_I_set_the_default_browser_in_Evolution.3F](http://live.gnome.org/Evolution/FAQ#How_can_I_set_the_default_browser_in_Evolution.3F)

I have reopened this thread as I have run into a situation where as a web maintainer for an organization, I need to access some control for the web domain. For some reason Chromium isn't supported, so I have had to re-install Firefox and now I have the same problem again. I tried the solution that you suggested, but it didn't change anything. Here are the commands that I used:
```
gconftool-2 --set --type=string /desktop/gnome/url-handlers/http/command 'chromium-browser'

gconftool-2 --set --type=string /desktop/gnome/url-handlers/https/command 'chromium-browser'
```

---

### Post by haqking on 2011-09-17
> **casbahdk said:**
> I have reopened this thread as I have run into a situation where as a web maintainer for an organization, I need to access some control for the web domain. For some reason Chromium isn't supported, so I have had to re-install Firefox and now I have the same problem again. I tried the solution that you suggested, but it didn't change anything. Here are the commands that I used:
```
gconftool-2 --set --type=string /desktop/gnome/url-handlers/http/command 'chromium-browser'

gconftool-2 --set --type=string /desktop/gnome/url-handlers/https/command 'chromium-browser'
```


try *chromium-bin or **chromium-bin %s *oh and i know in wirehark it sets it to simple-browser which invokes chromium

---

### Post by mobilediesel on 2011-09-17
> **casbahdk said:**
> I have reopened this thread as I have run into a situation where as a web maintainer for an organization, I need to access some control for the web domain. For some reason Chromium isn't supported, so I have had to re-install Firefox and now I have the same problem again. I tried the solution that you suggested, but it didn't change anything. Here are the commands that I used:
```
gconftool-2 --set --type=string /desktop/gnome/url-handlers/http/command 'chromium-browser'

gconftool-2 --set --type=string /desktop/gnome/url-handlers/https/command 'chromium-browser'
```

In a terminal you can also try:
```
sudo update-alternatives --config x-www-browser
```
then enter the number next to the browser you want as the default. That's what I had to do on my system.

---

### Post by haqking on 2011-09-17
> **mobilediesel said:**
> In a terminal you can also try:
```
sudo update-alternatives --config x-www-browser
```then enter the number next to the browser you want as the default. That's what I had to do on my system.


yeah but the problem is not the default browser, it is the default being handled in Evolution specifically...or did this fix it for your evolution ?

---

### Post by mobilediesel on 2011-09-17
> **haqking said:**
> yeah but the problem is not the default browser, it is the default being handled in Evolution specifically...or did this fix it for your evolution ?

It's been while since I used Evolution but the same thing happened with claws-mail that I use now. As far as I know, email programs in Linux just point to **x-www-browser '%s'** when you click on a link.

---

### Post by haqking on 2011-09-17
> **mobilediesel said:**
> It's been while since I used Evolution but the same thing happened with claws-mail that I use now. As far as I know, email programs in Linux just point to **x-www-browser '%s'** when you click on a link.


yeah as do most programs, the problem is evolution is not using the default borwaser so the URL handler for the app needs to be changed and i dont think he is having much luck.

his default is chromium but evolution is opening firefox

---

### Post by casbahdk on 2011-09-17
> **haqking said:**
> try *chromium-bin or **chromium-bin %s *oh and i know in wirehark it sets it to simple-browser which invokes chromium

Thanks for the quick replies from everyone. I have tried as you suggested. Neither of the suggestions worked. The only result is that the top is cut off just above the menus bar so none of my application windows have the resize buttons, and no frame at the bottom or sides.

---

### Post by casbahdk on 2011-09-17
OK, that was weird. Sorry for the double post, but the web browsers became unstable and wouldn't refresh, so I couldn't tell if my post had actually gone through. Anyway, I solved that little problem by running```
xfwm4 --replace
```

---

