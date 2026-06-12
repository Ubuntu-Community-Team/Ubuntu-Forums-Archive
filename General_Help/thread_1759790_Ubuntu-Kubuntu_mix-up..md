---
title: "Ubuntu-Kubuntu mix-up."
date: 2011-05-16
forum: General Help
---

### Post by jesuisbenjamin on 2011-05-16
Hello,

i use Ubuntu 11.04, using Classic Gnome environment. For the sake of trying i installed Kubuntu Plasma Desktop from Software Centre. I didn't like it, so i logged back into a Gnome Session and removed the Kubuntu-Dekstop package from Software Centre.

But after that, Kubuntu mingled with Ubuntu:
[LIST]
[*]Some programs remained installed and were set to default like K-torrent replacing Transmission as default torrent program.
[*]The splash screen when closing down or starting up (before log in) shows Kubuntu.
[*]There are random log-outs early in the gnome session.
[/LIST]

There are several Kubuntu packages installed, but i don't dare removing them without being advised to. Could you please help me clean this mess?

Thanks.
B.

---

### Post by 3Miro on 2011-05-16
Uninstalling kubuntu-desktop doesn't revert the changes. Here is what you need to do:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by jesuisbenjamin on 2011-05-16
Thanks 3Miro,

On the advice of [Lekensteyn on AskUbuntu]("http://askubuntu.com/questions/43122/ubuntu-kubuntu-start-up-messed-up-how-to-clean-up/43132#43132"), i looked into the /var/log/apt/history.log and picked up the list of packages installed with Kubuntu-Destop. After regex-cleaning the list, i removed the packages.

---

