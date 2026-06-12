---
title: "Broken Auto login on Jaunty"
date: 2009-07-26
forum: General Help
---

### Post by hastaspoon on 2009-07-26
While trying to fix/change the issues where the networkmanager asks access
to the keyring on startup, I somehow broke autologin.  I have the autologin
box checked in Login Window and my gdm-autologin is the same as a newly 
installed machine.  The only thing I can figure is that I messed up the 
keyring somehow.  I have dabbled with ubuntu the past few years, but just 
now fully switched all my computers to jaunty.  Anybody have any ideas how 
to fix the autologin?
Thanks for you help!

---

### Post by quixote on 2009-07-27
One thing is that you can either have autologin or auto-network-keyring-login, but not both.  The brilliant beaks at gnome are so worried about security, it's not even an option to have both.  (Yes, I'm rather cross about it :).)

So I don't know if this is the problem in your case, but maybe all that's happened is you've successfully turned the keyring login off, which automatically forces you to login on startup.  One way to test, would be to turn keyring login back on and see if that fixes your startup autologin.  If it does, then this is your problem.  You can join the club of users muttering oaths because gnome thinks it knows what we need better than we do.

---

### Post by hastaspoon on 2009-07-29
I am not sure what I did, but autologin seems to be working again.
I will check what you suggest, as I would like to know the initial cause of 
the problem so I can avoid it in the future.
Thanks for the reply!

---

