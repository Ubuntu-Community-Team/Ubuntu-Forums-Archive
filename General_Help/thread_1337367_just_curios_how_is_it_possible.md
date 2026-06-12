---
title: "just curios: how is it possible?"
date: 2009-11-25
forum: General Help
---

### Post by Nailox on 2009-11-25
well then... as far as i know the root pass is the very first pass when u install ubuntu, i have a clear memory of that pass, i have changed the pass several times... now i can install new things with my latest pass, but... when the site launchpad asks me for my root pass and i enter it, it says incorrect- i try my latest pass - the same. or when other apps like netwok manager asks me its the same again. so i guess i made my sys ultra secure by accident - even i dont know the root pass :) but how is this possible ?

---

### Post by mkvnmtr on 2009-11-25
On a default Ubuntu install there is no root password. Why would anyone ask you for your root password?

---

### Post by sedawk on 2009-11-25
The password you give during installation is the password of the "primary user". That is not the root user.
The primary user is a normal user who can execute commands with root priviliges using the "sudo" mechanism.
Normally you never set a password for root on ubuntu.

When applications asks you for a password it is normally
the one of the primary user and internally they use
sudo to execute something with root privileges (e.g.
the update-manager, network manager, etc.).

---

### Post by Nailox on 2009-11-25
I see. thanks for clearing that.

---

### Post by cariboo on 2009-11-25
When setting up a Launchpad account, you have to use your email address and create a password for that account, which should be separate from the user password when you installed Ubuntu.

---

### Post by lisati on 2009-11-25
As others have pointed out, Ubuntu usually sets up what might be called a "primary user", who has admin responsibilities for the computer, and who is not "root". Generally when the primary user wants to do something with "root" privileges, they would use the "sudo" command. More information on "sudo" and "root" can be found here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

+1 to Cariboo907's comments: passwords required for web sites are independent of any password(s) required for running your own computer. Web sites asking for your **root** password (or any other password that you'd use on your own computer, for that matter) are a cause for concern. *After checking that you're at a legitimate website, use the password that you created for that website. And **do not** under any circumstances give your passwords out willy-nilly.* Edit: See here for one example of why some discretion is required: [http://en.wikipedia.org/wiki/Phishing](http://en.wikipedia.org/wiki/Phishing)

---

### Post by prshah on 2009-11-25
> **Nailox said:**
> when the site launchpad asks me for my root pass and i enter it, it says incorrect- 

I think you may be confusing the "root" password with the "keyring" passwords. In Gnome, passwords for various programs and services (for example UbuntuOne) are stored in a "keyring". This means that you have to remember only one password (the keyring password). Are you using UbuntuOne? That uses launchpad to login, and also stores the launchpad password in the keyring.

---

### Post by Nailox on 2009-11-25
yes i know about phishing - the apps Im talking about are all ubuntu related like launchpad and one.ubuntu.com The thing is I keep getting the same message:" the application evolution wants access to the default keyrign but its locked..." i enter my current pass and the window reappears again and again.. i just don't get it. i want to use evolution mail and empathy.

---

### Post by prshah on 2009-11-26
> **Nailox said:**
> yes i know about phishing

I am not talking about phishing.

---

### Post by lisati on 2009-11-26
> **Nailox said:**
> yes i know about phishing - the apps Im talking about are all ubuntu related like launchpad and one.ubuntu.com The thing is I keep getting the same message:" the application evolution wants access to the default keyrign but its locked..." i enter my current pass and the window reappears again and again.. i just don't get it. i want to use evolution mail and empathy.

That's not the root password, that's the keyring password. I'm on Vista at the moment (rendering a rather large video project), so I'm not in a good position to try to duplicate the problem.


edit: just spotted this thread which describes something similar: [http://ubuntuforums.org/showthread.php?t=1218990](http://ubuntuforums.org/showthread.php?t=1218990)

---

