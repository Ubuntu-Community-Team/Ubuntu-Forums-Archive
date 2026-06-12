---
title: "Problem with timezone shortform in +%Z in french"
date: 2011-04-12
forum: General Help
---

### Post by dlublink on 2011-04-12
Hello,

Assuming your system supports fr_CA.UTF-8, run the following command :

```

LC_ALL=fr_CA.UTF-8 date +%c

```

Here is the output :
```

mar 12 avr 2011 17:14:15 EDT

```

The output should be :
```

mar 12 avr 2011 17:14:15 HAE

```

mar is short for mardi ( french for Tuesday) and avr is short for avril ( french for april )

EDT is short for Eastern Standard Time.

Being in french, I should get the timezone in french : HAE ( Heure Avancée de l'Est ).

Why is it returning EDT and not HAE ?

Tested on Ubuntu 10.04 LTS Server, Ubuntu 8.04 LTS Server and Ubuntu 10.10 Desktop.

Is this a bug or a feature ?

Thanks,

David

---

### Post by dlublink on 2011-04-12
[http://pubs.opengroup.org/onlinepubs/009695399/functions/strftime.html](http://pubs.opengroup.org/onlinepubs/009695399/functions/strftime.html)

%Z returns the abbreviation and says nothing of translating to the current language.

So it looks like strftime is behaving correctly.

David

---

