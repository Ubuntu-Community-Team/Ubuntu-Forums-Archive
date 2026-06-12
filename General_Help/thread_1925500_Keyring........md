---
title: "Keyring.......?"
date: 2012-02-14
forum: General Help
---

### Post by Tucker1 on 2012-02-14
Hi people

I am relatively new to Ubuntu but really like it and have it now on two laptops. 

But, one thing that I find a bit of a pain is when I load up a website that requires a password, this Keyring box pops up wanting a password, which when entered seems to do pretty much nothing!

I now just close it down and log in as normal. 

So, what is it? and how do I turn it off? 

I've tried looking at the setting to stop it bugging me but cannot see anyway to get rid of it and it doesn't seem to serve any real purpose.

---

### Post by mcduck on 2012-02-14
Is it really a keyring password, or the "security device" password confirmation from your web browser?

The keyring will most likely be used to store your wireless network password, and passwords for instant messaging accounts etc. While any web site passwords would be stored in your browser instead....

Anyway, you can just use the "Passwords and Encryption Keys" -tool to check what information is currently stored in your keyring. That should make it pretty obvious what program is actually trying to access the keyring.

---

### Post by Krytarik on 2012-02-14
> **mcduck said:**
> While any web site passwords would be stored in your browser instead....
Not so with Chromium/Chrome*, which I presume the OP is using; and as it checks the "default" keyring for possibly already stored login credentials as soon as it detects a login box, it triggers the password query for that if it isn't already unlocked, for example, by the "login" keyring; please see this guide how to do the latter:

[http://www.tuxgarage.com/2011/07/gnome-keyrings-to-serve-and-protect.html](http://www.tuxgarage.com/2011/07/gnome-keyrings-to-serve-and-protect.html)

* luckily, I must stress; in contrast to Firefox/Thunderbird, which are happily annoying me with their "Software Security Devices" :P

Regards.

---

### Post by Tucker1 on 2012-02-14
Thanks

Yes I am using Chrome. 

I've entered the only password that closes the Keyring window, but I cannot seem to unlock it. 

The 'automatically unlock' option stays greyed out when the right password is entered. 

I can't see which if any of those links download a file for Chrome.

Where am I going wrong?

---

### Post by Krytarik on 2012-02-14
> **Tucker1 said:**
> The 'automatically unlock' option stays greyed out when the right password is entered. ... Where am I going wrong?
Because you might be auto-logging in!? The "login" keyring isn't unlocked then.

---

### Post by Tucker1 on 2012-02-14
Aah yes I am.

So basically with the auto login, I presume I have to unlock it the once each time and that should be it?

---

### Post by Krytarik on 2012-02-14
> **Tucker1 said:**
> So basically with the auto login, I presume I have to unlock it the once each time and that should be it?
Yup. :P

Unless you disable Chrome's password saving feature, of course.

---

### Post by Tucker1 on 2012-02-14
Thanks.

Remembering all my passwords sounds like far more effort.... ;)

---

### Post by Krytarik on 2012-02-14
> **Tucker1 said:**
> Remembering all my passwords sounds like far more effort.... ;)
Yeah, of course; plus, you'd also have to type them! :P

---

