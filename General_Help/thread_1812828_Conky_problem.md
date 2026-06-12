---
title: "Conky problem"
date: 2011-07-26
forum: General Help
---

### Post by villalcalde84 on 2011-07-26
I am using Ubuntu 11.04 and installed conky; I'm using the configuration attached, but as I do not know very much about it I do not know how to fix this.

Every time I start ubuntu, conky shows above all other windows with a transparent space above it; every window I open appears as it is below conky (first image). To fix this I have to open the conky file and save it to reload it and then it stars again as it should (second image).

Is there something I have to change in the conky file so whenever I start Ubuntu it shows as the second picture?

Thanks!

---

### Post by fdrake on 2011-07-26
what about like this?

---

### Post by villalcalde84 on 2011-07-26
Thanks for your response fdrake, but with the changes in the file now the desktop looks like in the image, the sidebar is always hidden like if there is a windows always near it.

Is there something else that can be changed to display conky correctly at startup?

Thank you.

---

### Post by villalcalde84 on 2011-07-28
Does anyone have an idea about how to fix this?

---

### Post by Quackers on 2011-07-29
Instead of

own_window_type override

try

own_window_type normal

and see what that does.

---

### Post by villalcalde84 on 2011-07-30
Unfortunately that change did not work either, gives the same result as the last image. Its like the configuration in the file is correct, but somehow when the system starts it changes and gives the result I presented.

---

