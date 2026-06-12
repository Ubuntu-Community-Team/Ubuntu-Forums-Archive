---
title: "Xubuntu Users &amp; Logins?"
date: 2011-12-02
forum: General Help
---

### Post by JonBest on 2011-12-02
Hi all, I am new to forum and fairly new to Linux as a whole :)

My issue is that I have just installed Xubuntu on an old IBM Thinkpad R40 and it is running very well. However when I boot up it automatically logs on without asking for any password.

I managed to find the user management section but noticed that under my username password settings the checkbox saying "do not ask for logon password" or words to that effect is already unchecked & on the main users screen it says password required at logon (or words to that effect....sorry i'm at work and it isn't in front of me...)but it never asks for it.

If I logout it then takes me to the logon screen and I need to enter the password to log back in but this never happens when I first boot?

The reason I want to be able to login properly is because when I run Google Chrome it asks for the keyring default password because I use Chrome Sync. I had read that if you login properly to begin with this step isn't required.

Should I be looking at other settings? It seems odd that this isn't straightforward to setup?

Thanks for any help you can offer :confused:

---

### Post by JonBest on 2011-12-02
After more digging around I managed to resolve this. Here is what I did if others have this issue:

Open a terminal and enter:

sudo thunar     press enter

go to the following location:

/etc/lightdm and open lightdm.conf

Edit the following line:

autologin-user=(your custom username)     to

autologin-user=false

Now when you boot up you will see the login screen and can enter your password to continue.

ps. this did solve google chrome sync keyring asking for a password once I selected "do not ask after login" or words to that effect the next time I ran Google Chrome.

Hope this helps others.

Jon

---

