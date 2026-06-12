---
title: "What is the default password for Lucid?"
date: 2011-04-12
forum: General Help
---

### Post by Macfunky on 2011-04-12
I have Tango Studio installed on a usb stick which i wish to install alongside my current Maverick install. I booted up into it but when i click on the "install tango studio" icon i get asked for a password. I have searched google and i have not been able to find anything about this. It doesn't appear anywhere on their website and before someone says to ask on their forums i can't as their forums are not in english. 

I used start up disk creator to make the usb install but couldn't boot into it at first. I did some searching and found out that creating a usb install in maverick isn't backwards compatible. There was a simple solution which got me into the live mode, pressing tab, typing in live and then enter. I wonder if this is the reason why i am being asked for the password when i get into the live desktop? I have never had to put in a password before. I have tried a few generic passwords but no joy so i don't know what to do. Is there a default password that Ubuntu uses that would work for me so i could finally get it installed?

---

### Post by pqwoerituytrueiwoq on 2011-04-12
there is no default password as far as i know you are asked to set one during install
did you try a blank pass?
try google translate

---

### Post by WorMzy on 2011-04-12
The install script is probably invoking sudo, which requires your password -- the one you use to log in, which you set during the install procedure. There is no other password.

---

### Post by rvchari on 2011-04-12
> **Macfunky said:**
> I have Tango Studio installed on a usb stick which i wish to install alongside my current Maverick install. I booted up into it but when i click on the "install tango studio" icon i get asked for a password. I have searched google and i have not been able to find anything about this. It doesn't appear anywhere on their website and before someone says to ask on their forums i can't as their forums are not in english. 

I used start up disk creator to make the usb install but couldn't boot into it at first. I did some searching and found out that creating a usb install in maverick isn't backwards compatible. There was a simple solution which got me into the live mode, pressing tab, typing in live and then enter. I wonder if this is the reason why i am being asked for the password when i get into the live desktop? I have never had to put in a password before. I have tried a few generic passwords but no joy so i don't know what to do. Is there a default password that Ubuntu uses that would work for me so i could finally get it installed?

any new program you install or any system change you make needs permission. hence sudo is automatically invoked when you click on install button. in the password frame type in your login password. it should work.

---

