---
title: "How do you customise the default user?"
date: 2010-01-15
forum: General Help
---

### Post by nexoncore on 2010-01-15
I have searched for this on the forums but cant find it, so I will ask.

What I am trying to do is alter the default user, the one cloned when creating new accounts and the one used for guest. The reason for this is that I have the GUI "Gnome" set perfectly on my account, and want other accounts on the computer to use the same.

I already tried this with the root account by copying over my hidden gnome folders, which worked great. But how do I actually add them to the default user so when ever an account is created, it uses the new GUI look rather than default ubuntu.

---

### Post by efflandt on 2010-01-15
See **man adduser** or **man useradd**.  Default things to put in a new home directory are typically in /etc/skel if not specified elsewhere for the above commands.  Note that config files for gnome and other things are typically hidden files (beginning with dot), so in a terminal you would need to use **ls -a** to see them.  You should use **sudo** when copying things to /etc/skel.

---

