---
title: "&quot;automatically unlock this keyring whenever i'm logged in&quot; doesn't work"
date: 2010-11-08
forum: General Help
---

### Post by geometrikal on 2010-11-08
Hi All,

I want to share a solution to a problem I had with my new install of ubuntu 10.10

The problem was every time I logged into ubuntu, a dialog box would pop up asking me to enter my password for the default keyring, so that the network manager applet could connect to my encrypted wireless network. Despite checking the box "automatically unlock this keyring whenever i'm logged in", every time i did log in it would still ask me for the password! A quick google came up with no real solutions except for setting the password for the 'Default' keyring to blank.

My solution was:
uninstall network manager applet from Ubuntu Software Centre
immediately reinstall network manager applet
(^^^^^ not sure if these steps are really needed ^^^^^^)

Open System -> Preferences -> Passwords and Encryption Keys
In the Passwords tab, delete the 'passwords: Default' keyring
Right-click the 'passwords: login' key and select 'Set as default'

This fixed the problem for me. I think the cause was the login keyring was not set to be the default keyring. So even though logging in unlocked this keyring, the wifi keys were stored in another keyring that was the default, meaning I had to type the password again.

Hope this helps someone!
Ross

---

### Post by jpfle on 2011-04-08
Hi geometrikal,

I had a similar problem (pop-up to unlock default keyring), and I solved it with your trick. Thanks a lot. :p

---

### Post by wxuyec on 2011-04-08
> **jpfle said:**
> Hi geometrikal,

I had a similar problem (pop-up to unlock default keyring), and I solved it with your trick. Thanks a lot. :p

Hi, my system is 10.04. why can I not find what he said.
In password tab of my dialog for the password and encryption there is just
one option asking me to input password.

---

### Post by jpfle on 2011-04-09
> **wxuyec said:**
> Hi, my system is 10.04. why can I not find what he said.
In password tab of my dialog for the password and encryption there is just
one option asking me to input password.

Hi,

In seahorse, I clicked right on my keyring "login" and chosen "default", and I removed my other keyring that was named "default".

However, I don't remember when, (before or after changing default keyring, or before or after removing old default), but I also clicked right on my login keyring, chosen "Lock", and after chosen "Unlock". In the dialog appearing, there was option about unlocking it when I log in.

---

### Post by glomerulus on 2011-05-16
Thanks geometrikal !
Much appreciated

---

### Post by beacon on 2011-06-22
I'm having the same problem, but when I go to system>preferences>passwords and encryption keys I get the message 'could not launch. So I can't even get past square one. I'd appreciate help.

---

### Post by patrick.fehr on 2011-07-27
I can confirm that this fix works, and that the uninstall/reinstall process of network-manager-gnome is indeed needed for it to work!

Thanks and regards from 2011 ^^

---

### Post by beacon on 2011-07-27
I am glad the fix works for some, but I wish someone could help me with the problem I posted some time ago. When I go to password and encryption keys, I am told that it cannot be opened.

---

