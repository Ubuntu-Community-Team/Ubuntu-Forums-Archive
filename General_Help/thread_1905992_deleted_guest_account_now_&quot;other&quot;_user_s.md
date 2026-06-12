---
title: "deleted guest account now &quot;other&quot; user shows up"
date: 2012-01-08
forum: General Help
---

### Post by confusedndazed on 2012-01-08
Okay, I'm a complete newbie to Linux and Ubuntu. I wanted to delete the guest account so no one could use the computer without a password. Following a thread in the forum in the terminal I used the command: 
sudo apt-get remove --purge gdm-guest-session
 
After that I noticed not only did I still have the guest user, but now I had a user called "other" and when I tried to add or delete users in the desktop setting it no longer allowed me to.
I reread the thread and realized I missed an important post, so then I went back to the terminal and typed: sudo gedit /etc/lightdm/lightdm.conf
and then added the line allow-guest=false
Saved this and rebooted. This did remove the guest user, however the "other" user is still showing up (but not under my desktop settings window), and I still can't add or delete users from the desktop. This "other" user wants you type in a user name and then a password, but nothing I tried logs me in through this user.
 
How do I get rid of this "other" user and how do I regain the ability to set up and remove users from the desktop settings?
Can anyone help me? Thanks!

---

