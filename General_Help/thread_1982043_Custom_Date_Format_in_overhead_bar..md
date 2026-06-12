---
title: "Custom Date Format in overhead bar."
date: 2012-05-17
forum: General Help
---

### Post by Woegjiub on 2012-05-17
I am trying to change the format of the date shown in the clock to ISO (YYYY-MM-DD), but it seems as though it only allows one to choose the preferred format of a particular country.

Could anyone point out where the custom date format option is?
My country's date format is DD-MM-YYYY, which is the opposite of what I want.

---

### Post by Woegjiub on 2012-05-17
Well, what should have worked was changing /usr/share/i18n/locales/en_AU, and altering the lines d_fmt and d_t_fmt.

However, this has no effect.

Can anyone recommend a method for changing the date format to ISO?
in xfce and kde, it is as simple as typing %Y-%m-%d into a box.
Ubuntu seems to make everything far more difficult than it should.

---

