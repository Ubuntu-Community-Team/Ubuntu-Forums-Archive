---
title: "proview 465 monitor HELP"
date: 2006-03-08
forum: General Help
---

### Post by neoroses on 2006-03-08
Hi just installed ubuntu on my bros computer which has a Proview 465 LCD monitor and it is constantly blury and is compleatly un-usable?? any ideas????? :( thanks :D

---

### Post by somerville32 on 2006-03-08
Hello,

 It appears that your x-server is misconfigured. You can reconfigure it by typing:

```

dpkg-reconfigure xserver-xorg

```

It may seem very confusing but most of the arguments should be auto-detected and you'll simply have to hit enter. However, make sure you read everything and ask it to try and auto-detect when asked. Also, if you still have the owners manual for your monitor, make sure that the settings for the monitor are set correctly and are inside the limits defined by your manual.

After you've completed this, type the following:

```

sudo killall gdm
sudo gdm

```

The above will make sure all instances of your display manager are killed before restarting it. If the issue continues, try reconfiguring it again. Also, I'm sure there are individuals on Ubuntu's IRC channel (irc.freenode.net/#ubutnu) that would be happy to help you.

Thank you and best of luck,

Cody A.W. Somerville

---

### Post by neoroses on 2006-03-08
thank you very much, however can this be  done through the command line? as the visual is so bad it is un readable :( you krnt make anything out

---

### Post by somerville32 on 2006-03-08
Yes, you can run this from the shell.

---

