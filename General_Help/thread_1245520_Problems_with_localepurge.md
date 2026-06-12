---
title: "Problems with localepurge"
date: 2009-08-20
forum: General Help
---

### Post by johnpatcher on 2009-08-20
Hi,

I hope that I'm posting in the right category, actually I couldn't find another which fits better.

Basically I have a common problem: I want my Ubuntu in English, while some locales (time, date, units) should be German, because I'm used to them.

I have found some information about that, but so far I couldn't figure out what to do.

During the installation of Ubuntu using the Desktop-CD I selected English as language. The next thing I have done (just after the installation of Ubuntu) was to remove all unnecessary locales with localepurge.

I guess that there went something wrong :(. I just selected the locales "de_DE", "de_DE@euro", "de_DE.UTF-8" as well as "en_GB" and "en_GB.UTF-8".

Afterwards I have run the command "sudo localepurge", which has produced the following output:
```

johnpatcher@callisto:~$ sudo locale-gen 
Generating locales...
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NG.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.

```

What the heck? Why are there so many locales I haven't chosen, while there aren't any of my german locales which definitely have been chosen?

What have I done wrong?

Btw: What would be the next step to do in order to get an Ubuntu in English, but with German locales for time, date & units?

---

