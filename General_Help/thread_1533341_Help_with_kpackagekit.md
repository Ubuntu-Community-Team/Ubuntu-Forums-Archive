---
title: "Help with kpackagekit"
date: 2010-07-17
forum: General Help
---

### Post by Methos94 on 2010-07-17
Ok so far I like almost every aspect of my new kubuntu experience except for one very vital little portion... The package kit absolutely refuses to unpack packages. There are several ways it does this but the one I'm having the most trouble is where it pops up a window about waiting for authentification without prompting me for a password. I found a bug that looked (and I'm pretty sure is) the same as mine and it said that there was an automatic package updater trying to run in the background but I tried turning off all automatic updates and it is still going. It's entirely possible that I turned off the wrong updater or that i'm doing something else wrong entirely, I just jumped into this and stopped using windows cold turkey so please put your answers in a very 'user friendly' manner... If the there are no good ansers to my bug then i would like a how to on installing a package manually so i can try something like synaptic or adept. :confused: Please help

---

### Post by ankspo71 on 2010-07-18
Hi,
If you would like to try another package manager in Kuubntu, I highly recommend Synaptic Pacake Manager. Here is the code that you can paste into your terminal to get it: 
```
sudo apt-get install synaptic
```
You will then find a shortcut to Synaptic Package Manager in your Applications > System menu.
(Kpackagekit is nice, but Synaptic is nicer and has many more features)

Okay, now for the problem... To me it does sound like Kubuntu was trying to retrieve updates in the background while you were trying to use Kpackagekit just like you said. Has the problem gone away yet? Whenever I run into a problem like this I just reboot my computer then try installing what I needed again. 

You might be able to disable the updates in settings > system settings > Advanced (tab) > Service Manager 
(except I'm not seeing an entry for automatic updates for Kubuntu 10.10 (testing), but I thought it was there for Kubuntu 10.04)

---

### Post by iamnotloggedon on 2010-08-07
I have the same issue with my KPackageList but as it turns out the password input box is hidden behind the other windows for some reason. I just use the Window List widget to find the "Authentication is required to install a signed package" window.

I also tried installing Synaptic in the fashion listed above. It works really well and I kinda prefer it since you don't HAVE to know the name of the program you're looking for or maybe I'm just used to it since I used to have Ubuntu.

Just out of curiosity, does anybody know how to make the password input screen appear above the "awaiting authentication" window?

---

