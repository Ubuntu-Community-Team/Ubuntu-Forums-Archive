---
title: "Accidently chmod 777"
date: 2009-07-11
forum: General Help
---

### Post by dbrine on 2009-07-11
Really dumb mistake on my part but I did a chmod 777 on the entire HDD instead of a directory. How do I fix this without reloading? I am using Ubuntu Server 9.04, 32 bit.

I used "sudo chmod 777 -R /

Help.... Thanks,

---

### Post by coffeecat on 2009-07-11
Sorry, but I think you may be snookered. Most system files (root owned) have 744 permissions, but there are exceptions. /etc/shadow is 740 on my desktop system and intriguingly /etc/sudoers is 440. :? So a sudo chmod 744 of root owned files is still going to leave you with many files with the wrong permissions leading to potential security implications. How do you know which ones to set differently? I don't know.

Even ~ has a couple of hidden files (~/.dmrc is one) with permissions different from the rest of /home.

---

### Post by bernied on 2009-07-11
I agree. You might be able to fix this but it could take weeks.

Much quicker to copy your important documents to somewhere safe. If you've messed about with any config files, get copies of those too. Write a list of your favourite software.

And reinstall.

---

### Post by Irihapeti on 2009-07-11
Errk, I did something very similar once, except it was to chown -r /usr  to root. I fairly quickly realised that not all the files had the same permissions/owners and I had no way of quickly finding out which ones were different. So I did a reinstall.

Since then, I've done system backups reasonably regularly and that's helped me more than once to recover quickly from a goof-up.

---

### Post by ~sHyLoCk~ on 2009-07-11
This looks ugly. 
Easy method: Reinstalll and never repeat that mistake again.

---

### Post by jonobr on 2009-07-11
This kind of a post happens about once every couple of weeks,
Most people soldier through, reposting and looking for comparisons, but in the end,
they are avoiding the inevitable.

I always think, even if you did get things working again, if you ran into any trouble in the future, you would always be thinking " I wonder is it becuase of that chmod thing I did???"

Pull the bandaid fast if your from the
%s/bandaid/plaster/ if your European

---

