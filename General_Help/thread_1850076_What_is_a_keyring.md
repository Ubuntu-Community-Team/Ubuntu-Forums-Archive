---
title: "What is a keyring?"
date: 2011-09-25
forum: General Help
---

### Post by weblearner115 on 2011-09-25
Hey everyone,

Every time I boot my computer, an Ubuntu window pops up and says, "Enter password for keyring 'Default' to unlock."  What is a keyring?  Is there any way for it to unlock without me having to type my password every time?

Thanks!
weblearner115

---

### Post by haqking on 2011-09-25
> **weblearner115 said:**
> Hey everyone,

Every time I boot my computer, an Ubuntu window pops up and says, "Enter password for keyring 'Default' to unlock."  What is a keyring?  Is there any way for it to unlock without me having to type my password every time?

Thanks!
weblearner115

give your keyring the same password as your login password.

A keyring is just that, it unlocks all your other keys, such as a WIFI WPA key for example

---

### Post by weblearner115 on 2011-09-25
Yeah, I did make it the same password a while ago, but the only thing I understood about it is that I won't be able to get wireless internet if I didn't put in my password to 'unlock' it.  Does the fact that I have to 'unlock' it mean that it is like a toolbox with a padlock on it?  I'm hoping one of you can help educate me.

Haqking, you said the keyring unlocks all my 'other' keys.  What do you mean by 'other'.  And I didn't know that WPA has a key.  When you say 'key' do you mean the password you give for secured networks that are protected by WPA?  Also, is the keyring the key itself, or, like I said before, is it like a toolbox with a padlock and my password acts as a key to the lock?

---

### Post by alegomaster on 2011-09-25
> **weblearner115 said:**
> Yeah, I did make it the same password a while ago, but the only thing I understood about it is that I won't be able to get wireless internet if I don't putting in my password to 'unlock' it.  Does the fact that I have to 'unlock' it mean that it is like a toolbox with a padlock on it?  I'm hoping one of you can help educate me.

Haqking, you said the keyring unlocks all my 'other' keys.  What do you mean by 'other'.  And I didn't know that WPA has a key.  When you say 'key' do you mean the password you give for secured networks that are protected by WPA?  Also, is the keyring the key itself, or, like I said before, is it like a toolbox with a padlock and my password acts as a key to the lock?

I believe that the key ring unlocks other keys such as ssh, and openpgp, neither of them should be worried about for average people. I never enter a password for a keyring, and it lets me continue without using one.

Thats what I believe. Haqking should be able to clarify it.

Considering you are using WPA-PSK, then your key for wpa would be the password you enter to get connected to the network.

Sorry if my writing is bad, I need to get some sleep.

---

### Post by haqking on 2011-09-25
> **weblearner115 said:**
> Yeah, I did make it the same password a while ago, but the only thing I understood about it is that I won't be able to get wireless internet if I didn't put in my password to 'unlock' it.  Does the fact that I have to 'unlock' it mean that it is like a toolbox with a padlock on it?  I'm hoping one of you can help educate me.

Haqking, you said the keyring unlocks all my 'other' keys.  What do you mean by 'other'.  And I didn't know that WPA has a key.  When you say 'key' do you mean the password you give for secured networks that are protected by WPA?  Also, is the keyring the key itself, or, like I said before, is it like a toolbox with a padlock and my password acts as a key to the lock?

yeah its a keyring, a keyring holds keys, keys give you access to things.

Same thing here, WPA key is what enables you to connect to your WPA or whatever wireless security you have and unlock it for use, without the key there is no coming in.

other keys might be your email passwords stored in a evolution etc, pgp keys and so on

depends on your system

Alot of people if the only one using the system make the keyring password blank so it never asks, but i never recommend blank passwords, its like having a key but leaving the door open but depends on you really and your system

---

### Post by alegomaster on 2011-09-25
I found this after a quick google [ linky]("http://live.gnome.org/GnomeKeyring")

This should be able to help.
Remember Google is your friend.:)

---

### Post by weblearner115 on 2011-09-26
Thank you all for answering my question!  You helped me so much and I appreciate it!

---

### Post by haqking on 2011-09-27
> **weblearner115 said:**
> Thank you all for answering my question!  You helped me so much and I appreciate it!

no worries, you are very welcome.

peace

---

