---
title: "HELP! Does Adept keep a log of installations/removals?"
date: 2006-03-13
forum: General Help
---

### Post by MJN on 2006-03-13
I'd be very grateful for some help here....

I used Adept to install Xine however I immediately changed my mind and proceeded to remove it... However before my eyes I then started seeing Adept scrolling through loads of other packages that it was also removing! I interrupted the flow out of sheer panic..

I don't discount user error on my part however finger pointing is not going to help me here. My fundamental question is: Does Adept keep a running log of everything it's done? If so, where is it? I want to look through it, see what got removed, put it back in...

..then the finger pointing can start! :-?

Mathew

---

### Post by aysiu on 2006-03-13
Your best bet is to do these two things:

1. Install the *kubuntu-desktop* meta-package ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

2. Not use Adept. Synaptic Package Manager will warn you if it's about to install a bunch of packages.

---

### Post by MJN on 2006-03-13
Hi aysiu,

Thanks for the prompt response.

If you'll forgive my apparent misttrust, I'm reluctant to do much until I can ascertain exactly where I'm at (I use this server to host website, mail etc for myself and a couple of others). Notwithstanding this, can you tell me what 'kubuntu-desktop' is and what position it'll get me?

It's the 'backend' packages, the more subtle ones if you like, that I'm concerned about - I can only assume 'kubuntu-desktop' is not going to cover those.

If I can get my hands on a log showing what got removed then that'll stand me in good stead... Surely it is logged right? Everything else seems to be!

Thanks again,

Mathew

---

### Post by aysiu on 2006-03-13
You can poke around in /var/log and see what you find.

*kubuntu-desktop* includes as its dependencies all the packages that come standard with Kubuntu.

---

### Post by MJN on 2006-03-13
You were right - **/var/log/dpkg.log** specifically.

In it I had the following:

```
      2006-03-13 19:02:34 remove adept 1.0 1.0
2006-03-13 19:02:34 remove akode 4:3.4.3-0ubuntu1 4:3.4.3-0ubuntu1
2006-03-13 19:02:44 remove konq-plugins 4:3.4.3-0ubuntu1 4:3.4.3-0ubuntu1
2006-03-13 19:02:45 remove akregator 4:3.4.3-0ubuntu3 4:3.4.3-0ubuntu3
2006-03-13 19:02:45 remove ark 4:3.4.3-0ubuntu1 4:3.4.3-0ubuntu1
2006-03-13 19:02:45 remove arts 1.4.3-0ubuntu1 1.4.3-0ubuntu1
2006-03-13 19:02:46 remove artsbuilder 4:3.4.3-0ubuntu1 4:3.4.3-0ubuntu1
2006-03-13 19:02:47 remove firefox 1.0.7-0ubuntu20 1.0.7-0ubuntu20
2006-03-13 19:02:54 remove gkrellm 2.2.7-2ubuntu1 2.2.7-2ubuntu1
2006-03-13 19:02:55 remove gtk2-engines-gtk-qt 0.60-1ubuntu5 0.60-1ubuntu5
2006-03-13 19:02:55 remove gwenview 1.2.0-0ubuntu4 1.2.0-0ubuntu4
2006-03-13 19:02:55 remove k3b 0.12.2-0ubuntu2 0.12.2-0ubuntu2
2006-03-13 19:02:56 remove k3b-mp3 0.12.2-0ubuntu2 0.12.2-0ubuntu2
2006-03-13 19:02:56 remove k3blibs 0.12.2-0ubuntu2 0.12.2-0ubuntu2
2006-03-13 19:02:56 remove kdepim-wizards 4:3.4.3-0ubuntu3 4:3.4.3-0ubuntu3
2006-03-13 19:02:56 remove kaddressbook 4:3.4.3-0ubuntu3 4:3.4.3-0ubuntu3
2006-03-13 19:02:57 remove kamera 4:3.4.3-0ubuntu2.2 4:3.4.3-0ubuntu2.2
2006-03-13 19:02:57 remove kdemultimedia-kappfinder-data 4:3.4.3-0ubuntu1 4:3.4.3-0ubuntu1
2006-03-13 19:02:57 remove kappfinder 4:3.4.3-0ubuntu6 4:3.4.3-0ubuntu6
2006-03-13 19:02:57 remove karm 4:3.4.3-0ubuntu3 4:3.4.3-0ubuntu3
2006-03-13 19:02:57 remove katapult 0.2-0ubuntu3 0.2-0ubuntu3
2006-03-13 19:02:58 remove kate 4:3.4.3-0ubuntu6 4:3.4.3-0ubuntu6
2006-03-13 19:02:58 remove kaudiocreator 4:3.4.3-0ubuntu1 4:3.4.3-0ubuntu1
2006-03-13 19:02:58 remove kubuntu-konqueror-shortcuts 0.1-0ubuntu2 0.1-0ubuntu2
2006-03-13 19:02:58 remove konqueror 4:3.4.3-0ubuntu6 4:3.4.3-0ubuntu6
2006-03-13 19:02:59 remove knetworkconf 0.6.1-3ubuntu6 0.6.1-3ubuntu6
2006-03-13 19:02:59 remove kde-systemsettings 0.0svn20050613-0ubuntu3 0.0svn20050613-0ubuntu3
2006-03-13 19:02:59 remove kcontrol 4:3.4.3-0ubuntu6 4:3.4.3-0ubuntu6
2006-03-13 19:03:00 remove kcron 4:3.4.3-0ubuntu1 4:3.4.3-0ubuntu1
2006-03-13 19:03:01 remove kde-guidance 0.4.0-0ubuntu4 0.4.0-0ubuntu4
2006-03-13 19:03:01 remove kdm 4:3.4.3-0ubuntu6 4:3.4.3-0ubuntu6

``` 
I've now reinstalled them all and all appears well. As you can see it stopped at kdm (I knew that as soon as that had gone I'd be in the dark - literally)

Looking at the list, how on Earth could that be due to an error on my part? Or is Adept to blame? All I did was ask for 'Xine' to be removed. Ironically, I've even installed Adept again - better the devil you know, at least until I've got some breathing space to take a look at Synaptic.

Any ideas?

Thanks for your help - you've been a life saver.

Cheers,

Mathew

---

### Post by aysiu on 2006-03-13
My guess is that all those packages are dependent upon *xine* being installed. If you uninstall *xine*, you probably end up uninstalling all those packages as well.

The problem is really that Adept doesn't warn you about what's going to be uninstalled.

In Synaptic Package Manager, after you click **Apply**, it gives you a list of what's to be removed and what's to be installed.

---

### Post by MJN on 2006-03-13
That sounds feasible.

I've just given Synaptic a go and it seems world's apart - plenty more info about each package, categorised repositories, more configurable.... and that's having only checked it out for a couple of minutes!

Thanks again,

Mathew

---

### Post by MJN on 2006-03-13
Update: Looks like I'm not the only one to have had something like this:

[http://www.ubuntuforums.org/showthread.php?t=77629]("http://www.ubuntuforums.org/showthread.php?t=77629")

Perhaps I ought to look at reporting it as a potential bug...?

(Bear in mind I was only removing Xine so it's hardly something that the entire installation, or KDE at least, should be dependant on - not least given I'd only *just* installed it!)

Mathew

---

### Post by Jucato on 2006-03-13
Some packages become linked in some ways. It's not really a bug I think. Maybe xine became linked with these apps, which were link to main KDE libraries, which are linked to the whole system. Probably not a bug, but maybe a need for better package management.

And I encourage you to use Synaptic instead of Adept (or until Adept becomes mature enough). Synaptic also has that log/history that you're looking for. No need to dig around /var/log. :D

---

