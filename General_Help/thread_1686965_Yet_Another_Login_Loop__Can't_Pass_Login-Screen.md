---
title: "Yet Another Login Loop / Can't Pass Login-Screen"
date: 2011-02-13
forum: General Help
---

### Post by niXel on 2011-02-13
Just for others with this Login-Issue.

When I tried to login I saw the console for a second and then I was back on the login screen.
I am using 64 bit Ubuntu 10.10 (Maverick Meerkat) on an Thinkpad X100e.
There is enough free space available on the machine ([as here suggested]("http://askubuntu.com/questions/5956/login-problem-the-login-screen-shows-again")
Loading the recovery console, logging in as root and doing [FONT="Courier New"]startx[/FONT] did work. As root I looked for updates - but I had no luck: everything was up to date.

Starting failsave-X did not work - login loop again.

Changing rights or renaming [FONT="Courier New"]~/.ICEauthority[/FONT] and [FONT="Courier New"]~/.Xauthority[/FONT] did not work (a fix from [here]("http://ubuntuforums.org/showthread.php?p=9959525#7") and [here]("http://ubuntuforums.org/showthread.php?t=1684028")).
I also created the [FONT="Courier New"]/etc/X11/xorg.conf[/FONT] with this content:
[FONT="Courier New"]
Section "ServerFlags"
  Option "AIGLX" "off"
EndSection[/FONT]

But still no success.

I found no possibility to configure the Shared Memory Size for Video in BIOS (was fix [here]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/567029#16"))

My account is not expired and I was not using "Synergy+" (like [here]("http://ubuntuforums.org/showthread.php?t=1458838&page=2#2")).

Finally the **solution** was [renaming ~/.gnupg/gpg-agent-info-hostname]("http://ubuntuforums.org/showpost.php?p=10382382&postcount=3").
I hope it will help someone.

---

