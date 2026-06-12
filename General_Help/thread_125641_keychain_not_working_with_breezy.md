---
title: "keychain not working with breezy"
date: 2006-02-04
forum: General Help
---

### Post by robmoore on 2006-02-04
I am trying to use [keychain]("http://www.gentoo.org/proj/en/keychain/") to allow me to run backups via cron using ssh when I'm not logged. I've done this before on hoary but noticed that on breezy I always have to enter my password the first time I use a shell once I've logged in. My assumption is that when I log out the ssh-agent is nixed somehow. It's unclear to me why the behaviour of keychain has changed but I'm not able to run my cron job unless I'm logged in. Has anybody run into this?

Thanks,

Rob

---

### Post by robmoore on 2006-02-05
I've discovered that if I log in via ssh rather than via Gnome, the session is persisted. I'm puzzled as to why this would make a difference.

---

### Post by robmoore on 2006-02-05
After some further digging, I think I understand why this is happening but not how to address it.

I performed a "ps -ef | grep ssh" when logged in using Gnome and discovered "/usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session". Reading the man page for ssh-agent, I found "If a commandline is given, this is executed as a subprocess of the agent. When the command dies, so does the agent." So my theory is that keychain finds an existing ssh-agent running (which was started by X) and so another isn't created. However, when the X session ends so does the ssh-agent since the dbus-launch dies.

Now if I can just figure out how to get ssh-agent to stick around...

---

### Post by robmoore on 2006-02-05
After even more digging, I came across the --noinherit option on keychain (apparently introduced with keychain 2.5.0). This appears to do the trick but I end up with two ssh-agent processes instead of the one. I'm not sure what side-effects might result -- that is, it isn't clear to me if there was more to the decision to change keychain's behaviour to inherit an existing ssh-agent than avoiding redundancy.

---

