---
title: "All kinds of Flash trouble with FF5 and Natty 64 (details inside)"
date: 2011-07-28
forum: General Help
---

### Post by 3602 on 2011-07-28
[S]Hello all,

Uh,

I'm having trouble with Flash.

Here's the thing.
With the Flash-Aid program, it gives three options (well, five), right, and I got problems with every one of them.

**Adobe stable from repos (32-bit with wrapper):**

[LIST]
[*]YouTube videos play fine with 1080p full-screen being perfectly smooth
[*]Most other videos have black or white box-like artifacts on them that disappear when I make it full-screen
[/LIST]
**Adobe 64 Beta from Adobe Labs:**

[LIST]
[*]YouTube videos play mostly fine with 1080p full-screen being quite choppy
[*]No artifacts anywhere, ever
[*]Crashes Firefox now and then (this Flash is involved in every crash report)
[/LIST]
**Gnash:**

[LIST]
[*]Poor performance everywhere (even regular 360p videos)
[/LIST]

Some information that might help.
```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200 Series
OpenGL version string: 3.3.10750 Compatibility Profile Context

```
I'm running *fglrx* 11.5 installed from Jockey then updated from X Updates PPA.
Firefox has hardware acceleration ON (turning it OFF changes nothing in terms of box artifacts).

Thank you very much.[/S]

...Why don't I just use Chromium.
Sorry for your time and thank you all very much.

---

