---
title: "LANG variable keeps getting overruled in Ubuntu 11.04"
date: 2011-05-03
forum: General Help
---

### Post by Prodoc on 2011-05-03
Hi,

Since Ubuntu 11.04 the "LANG" environment variable keeps getting overruled somewhere. The result is that the date notation in the indicator area and the GRUB boot menu is in a different language compared to the rest.

At login I have selected the language en_GB, the same language is at the top in the "Language support" dialog. However, I have set my "Regional format" to "nl_NL".

When I check "env" in the terminal LANG is set to "nl_NL" as well.
I tried forcing it to "en_GB" by adding "LANG=en_GB" in "/etc/environment" but this did not help.

Why and where is this setting overruled in Ubuntu? How can I correct this properly?

---

### Post by imigueldiaz on 2011-05-03
> **Prodoc said:**
> Hi,

Since Ubuntu 11.04 the "LANG" environment variable keeps getting overruled somewhere. The result is that the date notation in the indicator area and the GRUB boot menu is in a different language compared to the rest.

At login I have selected the language en_GB, the same language is at the top in the "Language support" dialog. However, I have set my "Regional format" to "nl_NL".

When I check "env" in the terminal LANG is set to "nl_NL" as well.
I tried forcing it to "en_GB" by adding "LANG=en_GB" in "/etc/environment" but this did not help.

Why and where is this setting overruled in Ubuntu? How can I correct this properly?

I believe that correct path on ubuntu is

```

/etc/default/locale

```

or

```

/etc/default/locales

```

Sorry, I'm not on linux now :(

---

### Post by Prodoc on 2011-05-03
> **imigueldiaz said:**
> I believe that correct path on ubuntu is
```

/etc/default/locale

```


Thank you for your reply.

This file was indeed present and contained 'LANG="en_US.UTF-8"', not the 'LANG="nl_NL.UTF-8"' I was expecting to change. I changed it to 'LANG="en_GB.UTF-8"' nevertheless but the result is still the same. LANG remains set to "nl_NL".

---

### Post by imigueldiaz on 2011-05-03
> **Prodoc said:**
> Thank you for your reply.

This file was indeed present and contained 'LANG="en_US.UTF-8"', not the 'LANG="nl_NL.UTF-8"' I was expecting to change. I changed it to 'LANG="en_GB.UTF-8"' nevertheless but the result is still the same. LANG remains set to "nl_NL".

Stupid question, I suppose you have reboot the machine.

I would check the contents of .bashrc and .bash_profile to see if they override the default locale

Best

---

### Post by Prodoc on 2011-05-03
> **imigueldiaz said:**
> Stupid question, I suppose you have reboot the machine.
Of course.
> **imigueldiaz said:**
> I would check the contents of .bashrc and .bash_profile to see if they override the default locale
Nothing in the lines of locales has been set in those files.
I've even ran a grep over all the files on the system searching for 'LANG="nl_NL.UTF8"' and 'LANG=nl_NL.UTF8' but no files with that content exists.

---

### Post by IanLiu on 2011-07-12
I was trying to localize one application by setting the LANG and LC_ALL environment variables with no success. After issuing the `printenv` command, I saw there was a ```
LANGUAGE=en_US:en
``` variable set. So I changed that variable to ```
export LANGUAGE=pt_BR:pt
``` and everything worked again.

Ian L.

---

### Post by Prodoc on 2011-07-12
That's a different issue. LANGUAGE is properly set in my case, LANG is not. Despite the fact that LANG is being set properly in different places, it keeps getting overwritten in the end somewhere.

Do note that in your case just ```
export LANGUAGE=pt_BR:pt
``` will not make it stick and it won't be system-wide. After a reboot the setting will be reset.

---

