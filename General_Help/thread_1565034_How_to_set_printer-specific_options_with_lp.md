---
title: "How to set printer-specific options with lp?"
date: 2010-08-31
forum: General Help
---

### Post by M_F_R on 2010-08-31
The lp man page states the following:
> Aside  from  the  printer-specific  options  reported by the lpoptions(1) command, the following generic options are available [...]

But how are the printer-specific options set?

lpoptions outputs the following (among many other) options for my specific printer:
> StapleLocation/Staple: *None UpperLeft UpperRight LeftW RightW UpperW CenterW
RIPunch/Punch: *None LeftJP2 LeftUS2 LeftUS3 LeftEU4 LeftNEU4 RightJP2 RightUS2 RightUS3 RightEU4 RightNEU4 UpperJP2 UpperUS2 UpperUS3 UpperEU4 UpperNEU4

but neither setting -o Staple=UpperLeft or -o StapleLocation=UpperLeft, when calling lp, has any effect.

Both stapling and punching does work when using the printer GUI. 
I guess the GUI at some point calls lp. Is there any way to see which variables it passes on to lp?

Any help is much appreciated!

---

