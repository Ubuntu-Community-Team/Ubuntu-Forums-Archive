---
title: "Unlock keyring window"
date: 2011-02-27
forum: General Help
---

### Post by DeMus on 2011-02-27
Hi, I use Mint 9 64-bits and when I switch on my computer I am logged in automatically. I am the only user of this desktop so why log in manually?
Now, every time I surf to a website where I have to log in, I get the Unlock Keyring window. When I don't fill out the details there but just click "Cancel" the window disappears and the info I have typed on this website (and which is stored by Google Chrome)before is filled out and I can just log-in.
I just don't want to have the keyring window show up every time. What can I do about this? How do I prevent the window from showing up?

---

### Post by CharlesA on 2011-02-27
Autologin doesn't unlock the keyring. If you don't want that window to show up, you can set a blank password for the keyring, but it's not really recommended.

---

### Post by DeMus on 2011-02-27
> **CharlesA said:**
> Autologin doesn't unlock the keyring. If you don't want that window to show up, you can set a blank password for the keyring, but it's not really recommended.

It's strange since with all previous installations it worked fine. Only with this one something is different and the window shows up.
When I fill out the details will they be remembered so I won't have to type them again, or does it only work with a blank password?

---

### Post by CharlesA on 2011-02-27
I don't use the keyring, so I'm not quite sure, but I don't think the password is remembered. I've seen people get around it by just setting a blank password and leaving it that.

---

### Post by moore.bryan on 2011-02-27
"Dirty" method: delete ~/.gnome2/keyrings and when it asks for a password, save the keyring using "unsafe storage."

---

### Post by DeMus on 2011-02-27
Thank you for the answers, but can somebody please explain to me why it worked in previous installations (Ubuntu, Suse, Fedora, Mandriva, Mint) and now it doesn't anymore?
Is there something I did do wrong? 

CharlesA how come you don't use the keyring? Is it something I can switch off, and if yes, how?

---

### Post by CharlesA on 2011-02-27
> **DeMus said:**
> Thank you for the answers, but can somebody please explain to me why it worked in previous installations (Ubuntu, Suse, Fedora, Mandriva, Mint) and now it doesn't anymore?
Is there something I did do wrong? 

CharlesA how come you don't use the keyring? Is it something I can switch off, and if yes, how?
I think it's still installed, but I haven't stored any passwords there as far as I know. I don't connect via wireless, and I don't really know of any thing else that can be stored in the keyring.

I think that it'll prompt for the password if the user password doesn't match the keyring password, have you changed passwords lately?

---

### Post by DeMus on 2011-02-27
> **CharlesA said:**
> I think it's still installed, but I haven't stored any passwords there as far as I know. I don't connect via wireless, and I don't really know of any thing else that can be stored in the keyring.

I think that it'll prompt for the password if the user password doesn't match the keyring password, have you changed passwords lately?

No, I have never changed passwords. I have one and I use it for years already.
I can't recall if I ever saved a password in that window, guess not, but I'm not sure. Can I un-install it completely so I will not get the window again?

---

### Post by CharlesA on 2011-02-27
If you don't use it, I guess you could remove it. I'm not sure what all actually uses the keyring, but if you run into anything that depends on it, you'll get a list of the programs that need it.

---

