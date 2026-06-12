---
title: "Enter password to unlock your login keyring ???"
date: 2011-12-17
forum: General Help
---

### Post by BigBrotherWatcher on 2011-12-17
"The password you use to log in to your computer no longer matches that of your login keyring."

This message appeared during the Ubuntu single sign on process.

Is it normal? Why would that service care about my system password? Does it want to store its password?

What password do I enter into the Unlock Login Keyring prompt and what will happen when I do so?

Thanks.

---

### Post by BigBrotherWatcher on 2011-12-17
OK, evidently when signing up here it signed me up to the single launchpad as well and I didn't know it. 

**Sites you last authenticated to**

                                             Site                 Last authenticated                                                                                       
[https://launchpad.net/](https://launchpad.net/)                 2011-11-10 
                                                                    [http://ubuntuforums.org](http://ubuntuforums.org)                 2011-11-09

So trying to sign up to the single launch pad today was, to the system, an attempt to change the password since the passwords were different. (I used the old password for this forum sign in).

Still, why would any of this have anything to do with the system password and keyring?

---

### Post by 9072997 on 2011-12-17
the keyring stores ALL saved passwords on your ubuntu system and is protected by the same password as for your user. if any program wants to access or store a password it needs to access your keyring. if you change your keyring password to blank it wont prompt you for it, but people can steal your passwords. by default you unlock your keyring and log in at the same time, but this is disabled if you enable auto sign in

---

### Post by BigBrotherWatcher on 2011-12-17
> **9072997 said:**
> the keyring stores ALL saved passwords on your ubuntu system and is protected by the same password as for your user. if any program wants to access or store a password it needs to access your keyring. if you change your keyring password to blank it wont prompt you for it, but people can steal your passwords. by default you unlock your keyring and log in at the same time, but this is disabled if you enable auto sign in

Thanks, [9072997]("http://ubuntuforums.org/member.php?u=1121151") (phone #? :))

Are you saying to Ubuntu single sign on (SSO) tried to save its password on my system and I need to unlock it with my system password to permit that? Why else would the Unlock Login Keyring prompt appear?

---

### Post by BigBrotherWatcher on 2011-12-17
What a mess.

So I closed everything and rebooted and that went fine, but when trying to login to  Ubuntu One that same prompt appears when typing in the user/pw to Ubuntu One.

The system pw does not work. the Ubuntu One pw does not work.

But the user name and pw here at the froums, under the same email address, does work. I'll try to reboot again.

---

### Post by BigBrotherWatcher on 2011-12-17
So, now it is possible to login to Ubuntu One but after a successful connect I get the same prompt.

**Enter password to unlock your login keyring**

---

### Post by jockyburns on 2011-12-17
Keyring password has nothing to do with your login password (unless it is the same) When I use Evolution email client I'm asked for my keyring login password, which is the default password for my email account. This is very different to my login password for Ubuntu. (Very bad practice to use the same password for different sites/email account/ online banking etc etc. )

---

### Post by BigBrotherWatcher on 2011-12-17
> **jockyburns said:**
> Keyring password has nothing to do with your login password (unless it is the same) When I use Evolution email client I'm asked for my keyring login password, which is the default password for my email account. This is very different to my login password for Ubuntu. (Very bad practice to use the same password for different sites/email account/ online banking etc etc. )

Thanks, jockyburns. I can login to Ubuntu One from the Windows version but not from Ubuntu. That keyring prompt appears AFTER the normal Ubuntu One login prompt which appears to be successful. But the keyring prompt pop right up.

What do I type into the keyring prompt and what does it have to do with Ubuntu One? I still don't understand why Ubuntu One is asking for any additional password in addition to the Ubuntu One password.

EDIT: after entering the Ubuntu One password the keyring prompt popup, but I still don't know what it wants. Typing in the Ubuntu One password does not work and it seems that password already was working but the keyring prompt blocks it, and then after that fails, I it cancel and the Ubuntu One login prompt says "A prompt was canceled by the user" in error red.

EDIT 2: Does anyone else using Ubuntu One need to enter a password twice?

---

### Post by BigBrotherWatcher on 2011-12-17
After some more searching, the solution is as follows on 11.10:

Open Home
Ctrl H to show hidden files.
Open .gGome2
Open the keyring folder
delete login.keyrings

Reboot and fixed. You can now login to Ubuntu One and maybe a lot of other stuff.

---

### Post by Parzival on 2012-01-31
I have spent about 2 hours trying to solve this very problem. I tried the technique BigBrotherWatcher suggested and not only did it work, but it solved another problem I had as well (that being that at some point my computer stopped recognizing my wifi network so I would have to open a text file I had saved to my desktop with the router's login key everytime I wanted to connect to the internet). I was so excited to have it working that I created this account just to thank BigBrotherWatcher (but I may be back from time to time anyway).

---

