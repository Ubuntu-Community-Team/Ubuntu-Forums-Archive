---
title: "Switching to KDE"
date: 2006-05-11
forum: General Help
---

### Post by Pyro MX on 2006-05-11
I've been using GNOME for years and now I would like something different so I said to myself "well how about trying KDE?" There's Ubuntu 6.04 coming soon so when I do the switch, I might take Kubuntu instead. But I have some questions (about Kubuntu 5.10/6.04):

A) What package manager does it use? Adept? Kynaptic?

B) Will it have a new WiFi manager soon? (Because I tryed Kubuntu 5.10 and I ](*,) to make the wireless network work... and it wasn't working after reboot)

C) Is Wine/Cedega working on it?

D) Does wpasupplicant works like GNOME's on it?

I might come up with more soon, but that's it for now! :)

---

### Post by aysiu on 2006-05-11
[QUOTE=Pyro MX]
A) What package manager does it use? Adept? Kynaptic?[/quote] The default is Adept, but I just go ahead and install Synaptic Package Manager, because I like it better.

> 
C) Is Wine/Cedega working on it? Wine and Cedega are desktop environment-independent.

---

### Post by DarkOx on 2006-05-13
Kubuntu Dapper uses knetworkmanager, which is the network manager for GNOME given a KDE front-end. It's been working fine with wpa_supplicant for me - you don't have to edit wpa_supplicant.conf or anything. You just select your network, put in your passphrase, and you're off to the races.

The only problem I've had with it was getting knetworkmanager installed, as it wasn't on the cd and the only connection I had was my wireless one. So I had to manually download the necessary packages from my windows partition. Hopefully, the packages will be on the final release cd by default.

---

### Post by sabredog on 2006-05-13
I have just made the shift to KDE also. A couple more questions.

I cannot change the icon form my network. It gives a permissions error. How can I change icons that need permission approval to do so?

Is there an equivalent to Gdesklets at all?

cheers and thanks

---

### Post by tsb on 2006-05-13
[QUOTE=aysiu]The default is Adept, but I just go ahead and install Synaptic Package Manager, because I like it better.
[/QUOTE]

I must be the only one that likes Adept better.  It searches/filters much faster than Synaptic on my notebook

---

### Post by GeneralZod on 2006-05-13
[QUOTE=sabredog]I have just made the shift to KDE also. A couple more questions.

I cannot change the icon form my network. It gives a permissions error. How can I change icons that need permission approval to do so?
[/quote]

I'm not sure what you mean by this - can you explain in more detail, please?

> 
Is there an equivalent to Gdesklets at all?

cheers and thanks

Sure - check out SuperKaramba.  It should be in the repositories.

---

### Post by Pyro MX on 2006-05-13
So now if I use WPA encryption  I can just select the network and enter the wpa passphrase? Nice! (I didn't really like editing wpasupplicant.conf and making the whole thing work). I'll try this out for sure!

---

### Post by sabredog on 2006-05-13
[QUOTE=GeneralZod]I'm not sure what you mean by this - can you explain in more detail, please?

Sure - check out SuperKaramba.  It should be in the repositories.[/QUOTE]


KDE has placed an icon on the desktop allowing one click access to my windows LAN. When using Gnome I could change the icon for this shortcut but on KDE I cannot do this as I do not apparently have sufficient permission to do so.

Cheers for the help on the gdesklets equivalent!

---

### Post by mavr on 2006-05-15
kdesu konqueror and you'll have root permission in the file manager, that will allow you to do everything u want.

---

