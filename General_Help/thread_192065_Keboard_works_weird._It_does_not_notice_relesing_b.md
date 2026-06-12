---
title: "Keboard works weird. It does not notice relesing button.(so it goes like aaaaaaaa...)"
date: 2006-06-08
forum: General Help
---

### Post by sup on 2006-06-08
I upgraded to dapper last evening (via graphical interface) and today at about 14:00 GMT my keyboard started to semiwork. I was compiling ekiga at the moment and I used synaptic a bit, but I do not think I removed any important packages. I do not know if either upgrade or myseld caused the trouble.

Besides it seems that keyboard layouts change at random (so sometimes I can use native chars of m language and sometimes I have to deal with plain us layout) - which would not be that bad, it seems to sometimes not notice that I released a button until I press I again. So sometimes - I write like thiiiiiiiiiis. I think it maybe has something with special keys like ctrl or alt, because odd behaviouts often starts after pressing such keys.

Reboot does not help.

Also, when I booted this morning, a gnome message appeared that there is diference between X keyboard settings and GNOME keyboard settings - I choose to use X settinngs and not to apper the dialog again. 

I know this sounds confusing, but my system is behaving (as if it were alive) very weird and it is hardly usable (try to work in terminal with continousy pressed ENTER)

---

### Post by DFreeze on 2006-06-08
Probably a dumb question, but you're not working on a wireless keyboard, are you? 'cause it 'd be a battery issue, then.

---

### Post by sup on 2006-06-08
Latop, AC powered:-).
I doubt it is a hardware issue - it happened suddenly.

---

### Post by DFreeze on 2006-06-08
Then you have to wait for one of the more savvy Ubuntuers on the forum. Sorry I can't be of help, but I'm sure someone can.

---

### Post by sup on 2006-06-08
I hope so too. It is almost impossible to work with the computer and I have no idea what could have gone wrong...

---

### Post by sup on 2006-06-08
umph, uninstalling plptools solved my problem, as described in this bug [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39315](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39315)
actually, during my hunt after ekiga's dependencies, I installed plptools somehow...

---

