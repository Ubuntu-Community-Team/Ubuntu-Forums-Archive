---
title: "question about the conky-colors.c"
date: 2010-01-01
forum: General Help
---

### Post by thungmail on 2010-01-01
There is a fragment of the code from conky-colors.c
```
if (clocktype == 3) 
{
     fprintf(fp,"${voffset -12}${goto 28}${font Arial       Black:size=38}${color2}**${time %%H}**${color}${font}${voffset -28}${font Liberation Sans:style=Bold:size=11}${color2}${time :%%M}${time :%%S}${color}${font}\n");

}
```

What **time %%H** does in and can we use date %%r instead.Any comments are welcome here. Thanks
Tuan

---

