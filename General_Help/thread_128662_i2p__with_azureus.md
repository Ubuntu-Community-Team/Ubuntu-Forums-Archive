---
title: "i2p?  with azureus???"
date: 2006-02-12
forum: General Help
---

### Post by kerinin on 2006-02-12
is there a best-practice method to install i2p?  i've tried using the java windows installer as recommended on the i2p site but it didn't do a very good job.  my primary concern is using i2p with azureus, and the azureus plugin gives me an error saying that i2p has not been installed on the system.

has anyone managed to get i2p and azureus to play well with each other, and if so would they mind writing up a quick howto?

thanks a million

---

### Post by bobpaul on 2006-07-17
In Azureus
Tools: Options: Plugins: I2P Network

enter the path to your i2p installation. If you installed as user, it will be ~/i2p I think. If you installed with sudo then it is something like /usr/local/i2p

I see there's options in azureus without the pluging about accepting peer traffic etc from TOR and i2p. I'm not sure this plugin is needed anymore.

---

