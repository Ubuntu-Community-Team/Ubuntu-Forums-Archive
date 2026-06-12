---
title: "Problems with Flash 10 plugin in Firefox!!!"
date: 2010-03-24
forum: General Help
---

### Post by chaanakya_chiraag on 2010-03-24
I'm using Fluxbox on Ubuntu Karmic.  When I go to use SOME Flash objects, I must right-click and then double-click on the object for it to be selected.  Any ideas about how I can fix this???  It's driving me INSANE!!!!  Thanks!

---

### Post by chaanakya_chiraag on 2010-03-25
*bump*  Help please!!  Additional Info: Controls work in Youtube and Hulu, but fail with some obscure websites.

---

### Post by chaanakya_chiraag on 2010-03-26
*bump again* please help!!!!!!!!!!!!!!!!!!!

---

### Post by chaanakya_chiraag on 2010-03-29
Edit: I take that back...Youtube controls don't work after I pause the video.  I have to do the right-click hack thing...What could be going wrong???  Even weirder is the fact that Hulu controls contiinue to operate normally always.  What could be going on???

---

### Post by michaelqangeles on 2010-04-05
*Bump* . . Youtube player buttons aren't working for me either.

---

### Post by mickObrian on 2010-04-05
I had a similar problem, a temporary fix that worked for me was to disable visual effects, with the effects enabled I was unable to press the pause/play button, when I turned the effects off it worked again, I'm not sure but could someone confirm that when you enable the effects you use Compiz and when you disable them is switches you to Metacity? I believe thats the case, if you want to give it a try just go to System > Preferences > Appearance > Visual Effects and select none. I'm also wondering why this happens though.

---

### Post by PaulReaver on 2010-04-05
I don't know if it'll help but...

go to the adobe site [(here)]("http://get.adobe.com/flashplayer/") and download "APT for Ubuntu 9.04+"

double clicking the deb and put in your password.(this will add the adobe repo)
And install the latest version of flash by using synaptic.

Installing flash this way means you allways get the very latest stable version of flash.

Updating to firefox 3.6 might help as well.  it's supposed to use less ram and is more secure.

peace out

---

### Post by klytu on 2010-04-06
For 8.04 Hardy LTS users:

A solution that worked for me is to remove the package "flashplugin-nonfree", then install the package "adobe-flashplugin":
```

sudo aptitude update
```
```
sudo aptitude remove flashplugin-nonfree
```
```
sudo aptitude install adobe-flashplugin
```
Then restart firefox and hopefully you'll be able to enjoy YOUTUBE, HULU and other flash sites without difficulty.

---

### Post by chaanakya_chiraag on 2010-04-06
I'll try adding the adobe repo, although I think the package I've installed for flash (I think it's flashplugin-nonfree) downloads the adobe one anyway...Anyway, I'll give it a shot and report back.

---

### Post by charlesbw on 2010-04-06
i tried to install adobe flash plugin but I keep getting a message that the package cannot be found.

---

### Post by klytu on 2010-04-07
> **charlesbw said:**
> i tried to install adobe flash plugin but I keep getting a message that the package cannot be found.

If you are trying to follow the instructions in my previous post, you'll need to make sure the repositories for third-party software have been included in your package manager's search.

Instructions on how to do this may be found here:

_[COLOR="Blue"][https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party%20Software%20Tab]("https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party%20Software%20Tab")[/COLOR]_

---

