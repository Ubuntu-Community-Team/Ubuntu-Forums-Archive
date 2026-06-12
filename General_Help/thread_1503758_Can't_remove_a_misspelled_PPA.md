---
title: "Can't remove a misspelled PPA"
date: 2010-06-07
forum: General Help
---

### Post by r.masters on 2010-06-07
I was using add-apt-repository to add a PPA for the redshift f.lux clone (ppa:jonls/redshift-ppa) but mistyped *jon**i**s* for *jon**l**s*.

I've tried using ppa-purge to remove it but this does not work as it hits a 404 when trying to find a package list (as the user does not exist). Is there another way to remove this PPA from my list? I can't find a file similar to sources.list where they're stored.

---

### Post by DougieFresh4U on 2010-06-07
Maybe try going to  'System>Administration>Software Sources'
Then go to 'Other Software'
Look for your 'wrong' ppa there and remove it

---

### Post by darkdragn on 2010-06-07
I think that apt-add-repository adds the ppa's entry as a file in /etc/apt/sources.d/ If you just remove the file, with the corrosponding name, it should take care of it... If i'm wrong, it'll be an entry at the end of /etc/apt/sources.list, >_<.

---

### Post by r.masters on 2010-06-07
DougieFresh4U: Worked perfectly, thanks!

darkdragn: Found the files in /etc/apt/sources.**list**.d/ - even after removing the PPA from the Software Sources dialog they were still in that directory.

---

