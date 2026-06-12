---
title: "Samba, sshfs, and permissions problems"
date: 2009-09-04
forum: General Help
---

### Post by panfist on 2009-09-04
I'm having an issue with a setup that I'm trying out. Maybe I'm doing it a completely wrong way. Here it is and here's what's wrong.

Behind one firewall I have an ubuntu server and a windows server. The windows server hosts a samba share which I have mounted in ubuntu. Let's say it's /home/user1/samba_share The ubuntu server hosts an SSH server which I can access from outside the firewall.

Now user2 uses ssh to get into the ubuntu server. When I ssh into the ubuntu server, I'm ssh-ing as user1@ubuntu_server. User2, ssh'd as user1, wants to ssh into the ubuntu server and mount /home/user1/samba_share over sshfs. I got it working...somewhat. Read access was not a problem. Write access was touchy. I could write to it from the command line, but not from the GUI. If I tried to copy files in using my graphical file manager, I got an error that there wasn't enough disk space, yet doing an equivalent cp command from the terminal worked perfectly fine.

My questions are: is this setup sane? What would you change to make it smarter? How must I set up the permissions to get better read/write access? Do I need to set up an account for user2 on the ubuntu server?

---

