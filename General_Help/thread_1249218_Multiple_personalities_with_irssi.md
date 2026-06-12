---
title: "Multiple personalities with irssi?"
date: 2009-08-25
forum: General Help
---

### Post by andrew.46 on 2009-08-25
Hi,

For a variety of reasons I would like to use irssi with 2 distinct personalities. By this I mean different 2 sets of different usernames, passwords etc. The method I have used so far is to establish 2 config files:

```
$HOME/.irssi/config
$HOME/./irssi/confif_alternate
```

and run the alternate config file from an alias in ~/.bashrc:

```

alias irssi_b='irssi --config /home/andrew/.irssi/config_alternate'

```

This works well enough but I am little curious to hear if there is an easier way to accomplish this?

Andrew

---

