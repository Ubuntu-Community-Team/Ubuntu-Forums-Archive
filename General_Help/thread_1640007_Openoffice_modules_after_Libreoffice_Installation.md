---
title: "Openoffice modules after Libreoffice Installation"
date: 2010-12-07
forum: General Help
---

### Post by d4ryl3 on 2010-12-07
I have a simple question. I installed Libreoffice on my Ubuntu 10.10 (through wubi), and uninstalled Openoffice afterwards.

Everything's ok. But then I continue to receive updates for openoffice modules (which are a lot btw). From the Software Center, currently installed are libreoffice modules together with (I think) their openoffice counterparts.

Now the question is, is it safe to remove the openoffice modules? Or does Libreoffice need them, too? Thank you.

And also, how do I remove them completely from the updates? Thanks again.

---

### Post by d4ryl3 on 2010-12-07
Bring
Up
My
Post

---

### Post by bodhi.zazen on 2010-12-07
You can try to remove the open office stuff. Open synaptic and search for open office -> purge any files you find.

Once you have removed the remaining files you should no longer receive updates.

The only potential problem you may have would be "dependencies".

You other options, if you have a problem, is to simply leave ooo installed and not user it or do a minimal install and add only what you need.

---

### Post by d4ryl3 on 2010-12-08
Yeah, that's my only concern actually -- dependencies. Purge? Meaning 'completely remove' them, right?

I tried using Synaptic, I marked some openoffice modules for removal, but then some of the libreoffice stuff got highlighted, too.

So then I tried using the Software Center instead, since it alerted me right then and there upon removing stuff that LibreOffice uses, which is a better approach I guess.

Oh, does ubuntu have something like "System Restore" should things get ugly? Thanks for the help.

---

### Post by bodhi.zazen on 2010-12-08
> **d4ryl3 said:**
> Oh, does ubuntu have something like "System Restore" should things get ugly? Thanks for the help.

It is called "backup"

Personally, it is trivial to re-install an OS, so what I do is keep a data partition. I only back up highly customized system files and personal data.

With the information you posted, I would just leave open office installed and use libreoffice.

---

### Post by d4ryl3 on 2010-12-09
Backups, but of course! :) Thank you, I'll keep that in mind.

---

### Post by bowens44 on 2010-12-09
> **d4ryl3 said:**
> Yeah, that's my only concern actually -- dependencies. Purge? Meaning 'completely remove' them, right?

I tried using Synaptic, I marked some openoffice modules for removal, but then some of the libreoffice stuff got highlighted, too.

So then I tried using the Software Center instead, since it alerted me right then and there upon removing stuff that LibreOffice uses, which is a better approach I guess.

Oh, does ubuntu have something like "System Restore" should things get ugly? Thanks for the help.

You should remove open officebefore installing libreoffice.

---

### Post by d4ryl3 on 2010-12-10
> **bowens44 said:**
> You should remove open officebefore installing libreoffice.

I actually did that. Some openoffice modules were left behind that's why I had to ask if I should get rid of them ;)

---

