---
title: "More levels in XKB"
date: 2009-07-13
forum: General Help
---

### Post by kubaz on 2009-07-13
Hi,

it may possibly be the craziest XKB question ever... I create a very sophisticated XKB layout which uses four non-standard modifiers - ISO_Level3/5_Shift and two others, which I managed to successfully map to Mod2,3,5 and Lock. I created 18 levels of keys (higher than Level8 is written explicitely as the numbers 9 to 18 ) which are triggered by different combinations of these modifiers. Up to level 18 everything works right. However, when I add level 19 and higher, keys don't send the supposed key in that level, they send Alt_R instead. For example, if this is the definition of the symbols for key:

```
key <AB01> {
        type= "MANY_LEVELS",
        symbols[Group1]= [  a, b, c, d, e, f, g, h, i, j, k, l, m, n, o, p, q, r, s, t, u, v, w, x, y, z ]
    };
```then the symbols a, b, ..., r work properly, but instead of s, t, ... I get (at least xev says so) Alt_L.

If you don't know the answer, could you please tell me with whom could I consult this issue?

Thank you,

Jakub Marian

---

