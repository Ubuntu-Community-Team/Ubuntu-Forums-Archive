---
title: "permission error on login"
date: 2010-04-29
forum: General Help
---

### Post by killer 8 bit on 2010-04-29
well i just installed a fresh copy on my laptop and i updated it, i also installed OpenSSL and other odds and ends. i restarted the computer and now i cant log in to my main account! when i click on the user account it says permission denied. I can run the recovery mode and log into root but i cant log into my main account. Any help?

---

### Post by BrianIsNew on 2010-04-29
It's important to remember that Linux assumes that if you can touch the box, you own it. You have full rights to do whatever you want.

You've achieved the first step, which is booting to recovery mode. You had to be able to physically touch the box to do this.

When you drop to the root prompt, you have full permissions to do anything you please. This includes changing a user's password without knowing their old one to begin with.

From the recovery prompt, type the following (assuming your username is killer8bit)

passwd killer8bit
new password
new password
reboot

You should now be able to use that password to access your account.

---

### Post by killer 8 bit on 2010-04-29
i was able to change the password, but the thing is that even when i click on the box with my user name it says permission error and when i try to enter the password in command prompt the same error pops up

---

### Post by BrianIsNew on 2010-04-29
I was assuming you were talking about your Ubuntu account.

What is it that you're trying to log into? Where do you find this login box? What did you click on to take you there? Walk us through your steps after boot.

---

### Post by killer 8 bit on 2010-04-29
sorry for not being clear enough.

ok so when i boot up i get to the login screen for the GUI, when i get here and i try to click on my account it says permission denied.

---

