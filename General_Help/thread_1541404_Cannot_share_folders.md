---
title: "Cannot share folders"
date: 2010-07-29
forum: General Help
---

### Post by startling on 2010-07-29
I'm using Intrepid 8.10. 

I've been reading about sharing folders and see that there should be a sharing option when I right-click on a folder. Trouble is, on my system there is no such option! Nor is there anything under System > Preferences or System > Administration.

I've tried running Nautilus as root. I've tried creating a folder in the root of the file system (in case there was a problem with parent directories denying permission). But whatever I do, I cannot get the sharing files option. I'm happy to post screenshots if it'll help.

---

### Post by davidmohammed on 2010-07-29
... never run nautilus as root.  Strange things can happen.

copied from this [website]("http://howto.landure.fr/gnu-linux/ubuntu-8-10-intrepid-ibex/additions-to-a-default-ubuntu-8-10-intrepid-ibex-install") the stuff below - hopefully this will fix your issue.  Are you aware that 8.10 is no longer supported? What you are doing is better implemented in later versions - suggest strongly you should upgrade.


Sharing folders on the local area network
To enable your users (yourself included) to share folders with other Windows or Linux computers, you need Samba:

/usr/bin/sudo /usr/bin/apt-get install samba
Then add your own user (and other ones if needed) to the sambashare group:

/usr/bin/sudo /usr/sbin/adduser $USER sambashare
Once you are done, close your session and open it again to be able to share a folder. Sharing a folder can be accessed by right-clicking on the folder to share, and choosing "Share options" in the context menu that shows.

---

### Post by startling on 2010-07-29
Thanks for your prompt reply David.

Samba is already installed on my machine.

(And thanks for the advice about root Nautilus. Are you suggesting it's flaky and that I'd be better using Terminal as root to perform file and directory operations? Or was it general advice to be careful?)

---

### Post by davidmohammed on 2010-07-29
... its not flaky - but its easy to get yourself into a real tangle.  Just a warning to be careful!

If you create a folder in your home directory (not as root) - and right click - do you see the sharing option?

---

### Post by startling on 2010-07-29
Creating a folder in my home directory wasn't as simple as I thought it should have been. The Create Folder option in the right-click menu was greyed out. So I did sudo mkdir folder and then chowned the ownership to my user name. But still there was no right-click and share option.

---

### Post by davidmohammed on 2010-07-29
... sounds like you've got a messed up home folder.

Can you create another administrator user account that can create folders (not as root) and see the share option?

---

### Post by startling on 2010-07-29
I created a new admin user and logged in with that. I created a folder in the home directory but when I right-clicked on it there was exactly the same problem - no mention of sharing.

---

### Post by Morbius1 on 2010-07-29
Do you have the following package installed:
> nautilus-share

---

### Post by startling on 2010-07-29
Thanks Morbius1, that worked!

I have no idea why my installation of 8.10 didn't include that package but after installing it and restarting nautilus, Sharing Options appeared in my menu.

---

