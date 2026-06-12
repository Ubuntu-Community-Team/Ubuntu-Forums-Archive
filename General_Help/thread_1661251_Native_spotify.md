---
title: "Native spotify"
date: 2011-01-06
forum: General Help
---

### Post by TheLegendJoe on 2011-01-06
Hey- Sorry about the nooooooby question, but I only started using Ubuntu (10.10) yesterday-

Can someone help me install this? I keep getting this error and have no idea what to do-

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
joe@ubuntu:~$ 

after following these instructions [linky]("http://ubuntuper.wordpress.com/2010/10/04/native-spotify-in-ubuntu-premium-only/") :lolflag:

:)

---

### Post by howefield on 2011-01-06
The command in your link appears to be incorrect.


It should be

> sudo sh -c 'echo "deb [http://repository.spotify.com/](http://repository.spotify.com/) stable non-free" >> /etc/apt/sources.list.d/spotify.sources.list' && gpg --keyserver wwwkeys.de.pgp.net --recv-keys 4E9CFF4E && gpg --export 4E9CFF4E |sudo apt-key add - && sudo apt-get update && sudo apt-get install spotify-client-qt spotify-client-gnome-support


Once installed, you'll find the icon to start it in Application > Sound & Video > Spotify.

---

### Post by stoneage on 2011-01-06
Sounds like you have two package managers open at the same time.

Close Synaptic and use the Terminal.

---

### Post by TheLegendJoe on 2011-01-06
> **howefield said:**
> The command in your link appears to be incorrect.


It should be



Once installed, you'll find the icon to start it in Application > Sound & Video > Spotify.

Thanks :D Its worked :)

---

### Post by howefield on 2011-01-06
> **TheLegendJoe said:**
> Thanks :D Its worked :)

Imagine that, another lucky guess ;)

Just one thing, if you ran the above command more than once including running it from the link you provided, you may have multiple instances of the spotify repository in your sources list.

Not that there is any risk or damage in that, but if you want to check, go to System > Administration > Synaptic Package Manager > Settings menu > Repositories > Other Software tab and deselect all bar one instance of the lines that contain spotify in them.

---

