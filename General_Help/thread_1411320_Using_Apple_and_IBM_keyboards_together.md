---
title: "Using Apple and IBM keyboards together?"
date: 2010-02-19
forum: General Help
---

### Post by janthes on 2010-02-19
Hi all,

Is there a way to use Apple and IBM keyboards together?

My situation is this, I have Ubuntu Karmic on a PC (acting as a simi-headless fileserver) which I 'ssh -X' to on my MBP. When I 'gnome-session', X11 launches on my my Mac, I can see the desktop, it responds to the Mac's touchpad, everthing is great, but typing produces wrong characters. Can I install the Mac keyboard drivers using apt and linux knows what keyboard I'm using? If not, will those drivers interfere with my IMB keyboard?

TIA

---

### Post by tgalati4 on 2010-02-19
According to:

man gnome-session

There are some switches:

SYNOPSIS
       gnome-session  [--autostart=DIR]  [--default-session-key=KEY]  [--fail&#8208;
       safe|-f] [--debug]

The --default-session-key refers to a configuration file:

       --default-session-key=KEY
              Sets the GConf key from which  applications  running  a  default
              session  should  be  read  to  KEY.  If  not  specificed, /desk&#8208;
              top/gnome/session/default_session will be used.

You will have to do some research to figure out how to set a mac keyboard setting with a special session key and then use that key when you log in.

Try running:

gnome-session --debug

See what errors come up.

Try running:

gnome-session --failsafe

This should give you a simple text console from which to troubleshoot.

---

