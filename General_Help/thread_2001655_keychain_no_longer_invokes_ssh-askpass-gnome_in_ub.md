---
title: "keychain no longer invokes ssh-askpass-gnome in ubuntu 12.04"
date: 2012-06-11
forum: General Help
---

### Post by el_baby on 2012-06-11
Hi,

I've been using the following piece of code within both .bashrc and .profile to prompt me for my ssh passphrase at first login and launch ssh-agent.

```

if  which keychain > /dev/null ; then
	eval `keychain --eval --agents ssh id_rsa id_dsa`
	return 0
fi

```

Having installed **ssh-askpass-gnome**, whenever I logged into the graphical interface via xdg I got prompted for my passphrase (because .profile is run at GUI login).

However, after I upgraded from 11.10 to 12.04 I never get asked the passphrase until I open a terminal (because the same code is also in .bashrc).

I filled my .profile with ```
echo "I've been here" >> /tmp/login.log
``` and it clearly gets to the 'eval' and runs it, but the prompt doesn't show.

I don't know if this is a bug in **keychain** (don't confuse with gnome-keychain), in ssh-askpass-gnome or something else, but I can't make it work like it worked in 11.04 and 11.10.

FWIW, in a 12.04 clean installation happens the same thing.

---

