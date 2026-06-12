---
title: "Multiple locales and priority"
date: 2010-01-08
forum: General Help
---

### Post by mirix on 2010-01-08
After running sudo dpkg-reconfigure locales" I am in the following situation:

$ locale -a
C
es_ES.utf8
gl_ES.utf8
POSIX
pt_BR.utf8
pt_PT.utf8

Where gl_ES is the default language for the system. However, translation to gl_ES is still deficient and English is the reinforcement language. I am configuring a computer for someone who does not understand English.

The question is, is there a way to configure the system to use pt_PT, pt_BR and es_ES (in this order) as reinforcement languages and, only those missing, use English?

I think that before this was done by adding these lines to /etc/environment:

LANGUAGE="gl_ES.UTF-8:gl:pt_pt.UTF-8:pt:pt_br.UTF-8:pt:es_ES.UTF-8:es:en"
LANG="gl_ES.UTF-8"

However, I believe this would not work in Ubuntu Karmic. Is there another way to accomplish this? Does it make any sense at all?

---

