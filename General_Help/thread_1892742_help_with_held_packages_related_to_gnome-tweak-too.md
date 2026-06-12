---
title: "help with held packages related to gnome-tweak-tool"
date: 2011-12-08
forum: General Help
---

### Post by lotusflyer on 2011-12-08
Hi Guys,

Hoping to get some help with a held packages problem related to gnome-tweak-tool

sudo apt-get install gnome-shell-extensions-user-theme

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-shell-extensions-user-theme : Depends: gnome-shell-extensions-common but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

sudo apt-get remove --fix-broken
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.


How do I chase down this problem? And fix it?

Google, my usual support desk is failing me ...

-george

---

### Post by wolfen69 on 2011-12-08
Is [this]("https://extensions.gnome.org/extension/19/user-themes/") what you're looking for? Going to [https://extensions.gnome.org/](https://extensions.gnome.org/) is pretty much considered the "official" way of getting extensions now. You just click on the "off" button on the web page to install them. There's no need for installing by way of apt-get any more.

But in reference to your original problem, it probably just means what it told you, in that dependencies can't be met for some reason. Check out the site I mentioned.

---

### Post by lotusflyer on 2011-12-08
Hey Thanks,

I am wondering if I should worry about the nine packages being held back? Is there a way to fix this? How can I find out which packages they are?

Thanks!

George

---

### Post by wolfen69 on 2011-12-08
> **lotusflyer said:**
> Hey Thanks,

I am wondering if I should worry about the nine packages being held back? Is there a way to fix this? How can I find out which packages they are?

Thanks!

George

I know in the early days of gnome shell, things like a weather extension, or app menu had to be done by adding them to /usr/share/gnome-shell/extensions. And I had to change themes by adding my theme to ~/.themes and changing settings in gconf-editor. Those days are pretty much over now. Personally, I wouldn't worry about the packages being held back, since there's probably not much you can do about it. (someone will probably correct me....)

---

### Post by lotusflyer on 2011-12-08
> **wolfen69 said:**
> I know in the early days of gnome shell, things like a weather extension, or app menu had to be done by adding them to /usr/share/gnome-shell/extensions. And I had to change themes by adding my theme to ~/.themes and changing settings in gconf-editor. Those days are pretty much over now. Personally, I wouldn't worry about the packages being held back, since there's probably not much you can do about it. (someone will probably correct me....)


OK thanks

---

