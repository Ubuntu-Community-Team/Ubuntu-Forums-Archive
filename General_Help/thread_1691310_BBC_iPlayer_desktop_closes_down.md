---
title: "BBC iPlayer desktop closes down"
date: 2011-02-19
forum: General Help
---

### Post by cpeachey on 2011-02-19
BBC iPlayer desktop closes down as soon as it opens.
I have tried installing this several times on different instals of Ubuntu 10.10. Each time the install of iPlayer (from the BBC iPlayer website) goes OK right to the end when the desktop window opens and shows you the program you are trying to download...and then the window closes. (it's visible for about 2seconds)
Any ideas please?
Chris

---

### Post by WorMzy on 2011-02-19
Could you try running the application from a terminal (Applications -> Accessories -> Terminal), post the output (if any) here, and it may help us identify the source of the problem.

---

### Post by cpeachey on 2011-02-20
chris@Server:~$ sudo '/opt'/'BBC iPlayer Desktop'/bin/'BBC iPlayer Desktop'
[sudo] password for chris: 
Unknown desktop manager, only Gnome and KDE are supported
.
When I ran this a window came up asking me to agree to Adobe Air. (which I did) That window closed and nothing else happened.
The second time I ran......

chris@Server:~$ sudo '/opt'/'BBC iPlayer Desktop'/bin/'BBC iPlayer Desktop'
[sudo] password for chris: 
chris@Server:~$ 

Nothing came up at all.
Chris

---

### Post by aeiah on 2011-02-20
you shouldnt really be running bbc iplayer as root. 

have you tried installing adobe air on its own? ive never used the iplayer linux client (in fact, i didnt know one existed). i use do get_iplayer though:
[http://www.infradead.org/get_iplayer/html/get_iplayer.html](http://www.infradead.org/get_iplayer/html/get_iplayer.html)

---

### Post by markling on 2011-04-26
I've had the same problem.

The BBC say you have to install the latest versions of Flash and Air:

[http://iplayerhelp.external.bbc.co.uk/help/downloading/air_linux](http://iplayerhelp.external.bbc.co.uk/help/downloading/air_linux)

But if you tried installing iPlayer Desktop on what they are now saying was a beta version of Air (v 1.x...), then iPlayer Desktop won't work.

In this case, you can upgrade flash
But you can't simply upgrade Air.
You have to uninstall Air and all applications that rely on it. That means uninstalling iPlayer Desktop.

Then you have to install the latest version of Air
And only then reinstall the latest version of iPlayer.

-------------
| WARNING >>>
-------------

Don't download Adobe Air through the Ubuntu Software Centre. It gives you an old unstable version that will cause BBC iPlayer Desktop to fail.

You have to get it from the Adobe website:

[http://get.adobe.com/air/](http://get.adobe.com/air/)

and

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

(download the .deb versions).

------------------
| FURTHER HELP >>>
------------------

[http://www.adobe.com/support/documentation/en/air/1_5/AIR_1_5_linux_release_notes.pdf](http://www.adobe.com/support/documentation/en/air/1_5/AIR_1_5_linux_release_notes.pdf)

[http://blogs.adobe.com/flashplayer/2008/12/tips_on_resolving_application.html](http://blogs.adobe.com/flashplayer/2008/12/tips_on_resolving_application.html)

-----------
| RANT >>>>
-----------

There are two PROBLEMS with this.

1. Technical

If you try and install Air through the Ubuntu Software Centre, you are given version 1.x... - the old version that doesn't work properly.

If you are not blessed with the magical power of other-wordly perception, you may have had to learn this the hard way - as I did: you trust the Software Centre to give you the latest version... grrrrrr.

2. BBC and Doctor Who

I've been waiting a whole year to catch the repeats of the last series of Doctor Who before the start of the new series this weekend.

I downloaded those I missed to the iPlayer Desktop. But I can't watch them because Ubuntu Software Centre gave me an old, unstable version of Air, and neither the BBC nor Adobe cared to warn me that I didn't have the right version.

Not only can I not watch the missed Doctor Who episodes I downloaded to iPlayer Desktop, but now I can't see them at all. The BBC has since removed them from the iPlayer website because of its tight-pants distribution policy.

Once I uninstall iPlayer Desktop, I lose those episodes I've downloaded and can't download them again because they are no longer there.

Boo Hoo.

Why can't Adobe and the BBC care to ensure their users get the right software in the first place?

---

### Post by markling on 2011-04-26
So I just uninstalled Air and iPlayer Desktop.

I then reinstalled Air using the latest .deb from the Adobe site.

I then went to the BBC wesbite and clicked to download the latest version of iPlayer Desktop.

But a little Adobe window on the BBC site came up and said you need to install Air before you can install iPlayer Desktop. 'Do you want to install Air?', it said.

But I just bleedin' installed Air!

(But oh go on, if you insist...)
<YES>!I will install Air...
So I click the button to install Air.
The progress bar ticks and then the little Adobe window on the iPlayer download page says, "A download error occured. Try to download again!".

But I've already got bleedin' Adobe Air, for crying out loud!

---

### Post by markling on 2011-04-26
You have to reset your machine after installing Air or BBC iPlayer won't realise you've already got it.

How old fashioned!

BUT! There is a happy ending to this sorry tale.

The iPlayer desktop has miracuously kept the programmes I had already downloaded. And despite Adobe saying you had to delete all content from iPlayer Desktop before you reinstall.

I just clicked on my missed episode of Doctor Who - And it worked!

I can watch Doctor Who!

Sadly, the iPlayer says another programme I had downloaded, 'The Great Estate, the Rise and Fall of the Council House', is no longer available. WHY? It's not like they're going to make a killing with DVD sales on this programme, is it? Bleedin' tight-pants rights holders...

---

