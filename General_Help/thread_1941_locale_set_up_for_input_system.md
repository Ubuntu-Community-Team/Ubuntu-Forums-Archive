---
title: "locale set up for input system"
date: 2004-10-24
forum: General Help
---

### Post by macsaint on 2004-10-24
Hello

I generated locale with the command: dpkg-reconfgure locales
and added korean locales ko_KR.EUC-KR and ko_KR.UTF-8 in the selection.

My default locale is en_US, but I override in .cshrc as
setenv LC_CTYPE ko_KR.EUC-KR

In the .gnomerc, I wrote
export XMODIFIERS="@im=nabi"  
export GTK_IM_MODULE=xim

The input system has to work but it doesn't..
Another strange thing is when I change the session to korean, it works..

Is there anyone who can give a kind of comprehensive idea about it?

Thanks,
JW

---

