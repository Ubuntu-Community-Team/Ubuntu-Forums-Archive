---
title: "Redshift"
date: 2012-09-10
forum: General Help
---

### Post by chrispche on 2012-09-10
I have put redshift in startup applications and it will not start on boot. So I typed redshift into a terminal window and got the following...

** (process:4255): WARNING **: Metadata for error domain "geoclue-error-quark" already registered

Started Geoclue provider `Geoclue Master'.
Using provider `geoclue'.
According to the geoclue provider we're at: 51.58, 0.20
Using method `randr'.

I'm using Gnome 3.4 and Ubuntu 12.04, any ideas anyone? I have a feeling something is missing here.

Cheers.

---

### Post by mcduck on 2012-09-10
It should work regardless of that warning, since it still managed to get your location.

Based on a quick search, it seems that installing the *geoclue-hostip* package might help with the warning message.

---

