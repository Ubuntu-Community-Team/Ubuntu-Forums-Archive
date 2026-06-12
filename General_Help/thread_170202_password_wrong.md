---
title: "password wrong"
date: 2006-05-04
forum: General Help
---

### Post by eeyore on 2006-05-04
I have been having this really annoying problem on Kubuntu, which otherwise is amazing. I login just fine and work just fine, but then when I suspend or lock my system (because I'm using a laptop), when I come back the prompt for username and password does not let me log back in. It always says my password is wrong.

At that point I need to restart kdm to continue working...annoying to say the least. I'm using KDE 3.5.2 and was using 3.4.3 which came with Kubuntu and I had the same problem with both. Any ideas?

My thanks

---

### Post by Al3xanR0 on 2006-05-04
[QUOTE=eeyore]I have been having this really annoying problem on Kubuntu, which otherwise is amazing. I login just fine and work just fine, but then when I suspend or lock my system (because I'm using a laptop), when I come back the prompt for username and password does not let me log back in. It always says my password is wrong.

At that point I need to restart kdm to continue working...annoying to say the least. I'm using KDE 3.5.2 and was using 3.4.3 which came with Kubuntu and I had the same problem with both. Any ideas?

My thanks[/QUOTE]

I don't know if this will work but try it. I had a similar issue when I was attempting to su adept or Synaptic vs uisng sudo (don't ask, it is a preference I have) kdesu would render a wrong password message even after establishing root passwd. I added my uid to the /etc/sudoers file and only then would it accept the password. These may not be related, however, the "wrong password" error was a familiar one.

---

### Post by Parkotron on 2006-05-04
This is a serious bug that's been mentioned a few times on the forums (such as [here]("http://ubuntuforums.org/showthread.php?t=163942")). There is no sure fire way of getting it to accept your password. Different people claim different things work, but there's no consensus. In the meanwhile, I'd recommend using xscreensaver and disabling kscreensaver.

---

