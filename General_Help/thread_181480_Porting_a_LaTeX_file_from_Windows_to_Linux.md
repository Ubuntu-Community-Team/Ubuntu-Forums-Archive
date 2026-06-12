---
title: "Porting a LaTeX file from Windows to Linux"
date: 2006-05-24
forum: General Help
---

### Post by sergiodlc on 2006-05-24
Hi:

I have begun editing a LaTeX file in a Windows PC and now I'm working in Ubuntu with Kile. There's a complete mess around accented characters.

Can anyone help me to convert my file properly?

What do I have to do, to modify the inputenc package directive or is something I have to configure in Kile?

Regards,

Sergio

---

### Post by ltmon on 2006-05-24
I'm not sure of this exactly, but have you tried "dos2unix" on the command line?  It might fix these problems...

On the command line (working from memory here):
```

dos2unix infile.tex > outfile.tex

```

Cheers,

L.

---

