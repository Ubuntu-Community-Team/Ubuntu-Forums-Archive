---
title: "Users Spontaneously Losing Administrator Priveliges"
date: 2010-05-31
forum: General Help
---

### Post by bearcdp on 2010-05-31
Hi all,

I just got a fresh Ubuntu 10.04 install on a system, added Lubuntu (the poor thing's 10 years old), and added a second user and gave him sudo/admin rights via the Users and Groups app. All was working fine, but now the initial user can't make any system changes. The initial user can still execute sudo and gksudo, but not much else.

In the Network Connections applet, the initial user can't edit the "Auto eth0" connection, the "Edit" and "Delete" buttons are just greyed out.

In User and Groups, I can click "Advanced Settings" or "Change" on another user, but nothing will happen. If I click "Add User" as the initial user, it will give the "Not authorized" popup.

I had a second user that I'd given adminstrator/sudo access to. So to change the network settings I logged in as this user for the first time, and was able to change some things. However, after a reboot I had the same problems with this new account.

I haven't done anything with this install besides install openssh-server, add some firewall rules with ufw, and add the Lubuntu desktop. Anyone have any ideas for a solution? Most of my google results turned up basic stuff like corrupted sudoers file (mine is still in pristine, default condition), and not being part of the admin group (which both users still are). The behavior also persists regardless of whether I use gnome or Lubuntu for my session.

---

### Post by sisco311 on 2010-05-31
Hi and welcome to the forums!

It looks like something is wrong with policykit. What's the output of:
```
pkexec echo
```?

Does the authentication window pop up?

---

### Post by bearcdp on 2010-06-01
Hi Sisco, thanks so much for the quick reply and warm welcome.

Unfortunately I didn't have the opportunity to try pkexec, as the machine started refusing to even boot. I'm guessing the policykit issue was a symptom of a deeper problem, so I just did a quick reinstall and all is fine now. I ran "pkexec echo" and it asked for Authorization and everything went fine. There was no output on the terminal. Thanks for that tip! I'll be keeping that one in my back pocket in case similar problems arise in the future.

I'm hoping that installing Lubuntu didn't have something to do with it. I'm looking to free up some RAM & cycles. Does installing the Lubuntu desktop over the regular GNOME Ubuntu distro still give you that speed increase despite having the GNOME stuff hanging around, and has anyone noticed any significant instability? It makes sense to keep the standard Ubuntu desktop since I know it works, but maybe it'd be better to have a clean Lubuntu install?

---

