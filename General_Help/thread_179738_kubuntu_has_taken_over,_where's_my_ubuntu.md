---
title: "kubuntu has taken over, where's my ubuntu?"
date: 2006-05-20
forum: General Help
---

### Post by Poirot on 2006-05-20
I run ubuntu and installed the KDE desktop to see what it was like. Now I have loads of other packages in my menus, many of which perform the same function as ones I already had. This is fine but I can't now remove KDE. To top it off I get the Kubuntu splash screen on booting up and shutting down. When it asks for my username and password it is ubuntu but before that and on shutting down, its kubuntu.

Can I get my nice brown ubuntu start up screens back?

Can I remove all the KDE apps in one go, i.e. remove KDE cleanly?

---

### Post by Ramses de Norre on 2006-05-20
For the splash: ```
sudo update-alternatives --config usplash-artwork.so
```


For the login manager: ```
echo "/usr/bin/gdm"|sudo tee /etc/X11/default-display-manager
```

There is a how to on removing kde on the forums, but I don't know the link now.
And for the future: if you use aptitude instead of apt-get to install it will be much easier to remove things like this (aptitude has the same syntax as apt-get and uses the same sources).

---

### Post by Poirot on 2006-05-21
Thanks, I have now got ubuntu back on shutting down but its still kubuntu when I start up. Also, when  started my machine this last time, I had to log in in a text interface and run sudo gdm to get into gnome!

What have I done?

---

### Post by Ramses de Norre on 2006-05-21
Sorry, I made a mistake, do ```
echo "/usr/sbin/gdm"|sudo tee /etc/X11/default-display-manager
```I said bin instead of sbin.

What do you mean by it's still kubuntu on start up? The splash screen? You'll need to choose the right option after the update-alternatives command.

---

### Post by Poirot on 2006-05-22
OK, thanks

Was that the cause of gdm not loading?
What does 'tee' do?

I did select the non-kubuntu option after update-alternatives, I think that is what fixed the shut down screen.

This is the situation:

On booting my machine, once I choose ubuntu in Grub I get a kubuntu screen with a progress bar. Eventually this changes to the ubuntu login screen (though not the last two times, it just stopped at the command line and I have to do 'sudo gdm').

When I log out and shut down I get the same progress bar screen but its now ubuntu when it was previously kubuntu.

---

### Post by cskeide on 2006-05-22
If you mean that usplash uses the kubuntu artwork on startup, but ubuntu on shutdown, you might have to rebuild initramfs or whatever it's called.
```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

---

### Post by Poirot on 2006-05-22
I just tried rebooting after > echo "/usr/sbin/gdm"|sudo tee /etc/X11/default-display-managerfrom Ramses de Norre. It looks like it's cleared up my problem. I think the previous > echo "/usr/bin/gdm"|sudo tee /etc/X11/default-display-manager caused the other problem. Both are fixed now, I get ubuntu progress bars on both start up and shut down.
Thanks guys.

---

### Post by Ramses de Norre on 2006-05-22
[QUOTE=Poirot]OK, thanks

Was that the cause of gdm not loading?
What does 'tee' do?

I did select the non-kubuntu option after update-alternatives, I think that is what fixed the shut down screen.[/QUOTE]

Yes that's why gdm didn't load, tee puts the output of echo (the path to gdm) into that file. And I made a mistake in the path the first time, so ubuntu couldn't find gdm.

Your problem is fixed now, no?

---

### Post by Poirot on 2006-05-23
Yes, thanks again.

---

