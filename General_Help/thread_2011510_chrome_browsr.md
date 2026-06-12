---
title: "chrome browsr"
date: 2012-06-27
forum: General Help
---

### Post by tobythedog on 2012-06-27
hi just installed chrome browser from googles site seemed to install ok however wont launch , i then tried to remove it but no option to remove in software center , how can i remove it . i also installed chromium from software center which works ok however i cannot get any browser to work with flash on 12.04 , is there a fix for this please and how can i remove the google chrome .

---

### Post by MG&amp;TL on 2012-06-27
> **tobythedog said:**
> hi just installed chrome browser from googles site seemed to install ok however wont launch , i then tried to remove it but no option to remove in software center , how can i remove it . i also installed chromium from software center which works ok however i cannot get any browser to work with flash on 12.04 , is there a fix for this please and how can i remove the google chrome .

Do you mean that chrome doesn't show up in the software centre, or that you can't find an option to remove stuff in general?

---

### Post by sondraparkin on 2012-06-27
what is the link that you downloaded it from?
stupid question: did you download it for linux?

there are repos in ubuntu for google chrome that you can download instead of downloading it from the web site. The one you downloaded might not be accurate for your OS, whereas installing from the repo would work

```
$ sudo apt-get install google-chrome-stable
```

to uninstall:
what is the process that you installed it?

---

### Post by U202E on 2012-06-27
dpkg or apt can uninstall programs on ubuntu...
and google chrome seems to have problems on LXDE, which is your desktop environment if you use lubuntu.

---

### Post by tobythedog on 2012-06-27
i got it from googles website downloaded it from there , it was 32 bit linux debian version when opened it started the lubuntu software center and installed through that. the software center only has a listing for chromium , no listing for chrome so cannot remove it.

---

### Post by Frogs Hair on 2012-06-27
I installed via the .deb from the chrome website on Ubuntu and it doesn't appear in the software center even though it was installed with the USC. Chrome does appear in the synaptic package manager though and can be removed there or from the terminal. The installed package is as written above google-chrome-stable.

---

### Post by craig10x on 2012-06-27
Right..just add synaptic package manager (download it from ubuntu software center if you haven't already) and once you have it, just search for chrome and you will see your installed google chrome stable...then just have it remove the program...

By the way, are you sure you have flash installed?  take  a look in synaptic package manger and see if adobe flash player is installed....if not install it...or if it is, try re-installing it...

---

### Post by pbrane on 2012-06-27
if you installed google-chrome for the google web site it should have installed as a deb. you can check to see if it is installed with:
```

dpkg -l | grep chrome | awk '{print $2}'

```
I'm sure you installed to correct version; 64bit or 32bit?

---

### Post by MG&amp;TL on 2012-06-27
> **craig10x said:**
> Right..just add synaptic package manager (download it from ubuntu software center if you haven't already) 

The OP is running Lubuntu. We have our own software centre, and synaptic is installed by default. Just FYI. :)

---

### Post by kc1di on 2012-06-27
> **tobythedog said:**
> i got it from googles website downloaded it from there , it was 32 bit linux debian version when opened it started the lubuntu software center and installed through that. the software center only has a listing for chromium , no listing for chrome so cannot remove it.

Hi tobythedog,

chrome should work ok you can see if you can launch it from a terminal. the command is 
```
google-chrome
```

you will have to make a .desktop file before it will show up in the menu.  
My I recommend that you use chromium-browser instead of chrome. it can be install from the repository in the software center.
you can unistall chrome with this command from a terminal

```
sudo apt-get remove chrome
```

---

### Post by marinara on 2012-06-27
pretty sure the package is not named chrome

---

### Post by craig10x on 2012-06-27
> **marinara said:**
> pretty sure the package is not named chrome

Right..but if he types the word chrome in the package manager, it will come up on the screen...as google chrome stable....the search is more clever then you might realize (lol)....
he can remove it from there, or using terminal commands as previously mentioned...both work fine...

---

### Post by 5HourButt on 2012-07-14
> **tobythedog said:**
> hi just installed chrome browser from googles site seemed to install ok however wont launch , i then tried to remove it but no option to remove in software center , how can i remove it . i also installed chromium from software center which works ok however i cannot get any browser to work with flash on 12.04 , is there a fix for this please and how can i remove the google chrome .


On the chance this might help anyone trying to de-install. I had an issue with Chrome and here is how I un-installed it from the command line using the terminal. 

sudo apt-get remove google-chrome-stable

---

### Post by tobythedog on 2012-07-17
great the     sudo apt-get remove google-chrome-stable    run in terminal did the trick , thanks very much for all the help

---

### Post by daemoncycler on 2012-08-12
Hi,
can I hijack this thread?

I am running Lubuntu 11.10 & was also having issues with Shockwave plugin on Google Chrome.  Followed most of the advice given in this thread without much luck.

On the Adobe website it was suggested to enter **about:plugins** in browser bar which takes you to [COLOR="Navy"]chrome://plugins/[/COLOR] where you can enable Flash.  Flash was already enabled - so I disabled it.

Voila, of course now the msgs for Shockwave are gone. I expected some issues with Chrome @ this point.  I thought the purpose of Flash/Shockwave was to enrich the browsing experience.  A day later & I cannot tell that anything has changed.  Except perhaps the browser is a bit faster than it was before.  All the little icons are still showing up.  The beautiful planets on the Gmail page are vibrant as ever.

So my question is what does shockwave/flash do?  Are they the same thing?  Will I ever miss it?

thanks

p.s.  I did uninstall google-chrome-stable thru Synaptic & re-install it with GDebi just in case the version I originally installed from the web was incorrect.  GDebi did install an earlier version = 18.0.???? which didn't have shockwave problems, however I did have to constantly reload the page to get all the content to appear. The Update Manager immediately pushed it right back up to version 21.0.1180.75 & then shockwave issues are back.

---

