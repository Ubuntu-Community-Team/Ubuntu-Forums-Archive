---
title: "Compilation error"
date: 2009-10-08
forum: General Help
---

### Post by tonysonney on 2009-10-08
I am trying to build Android. But the compilation fails with the starting error message.
[HTML]include/linux/types.h:113: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'sector_t'[/HTML]

But I cant find why? I would expect this error message following [HTML]couldnt find a header file[/HTML] Do anybody know, how could I fix this? I am using 2.6.30.

Thanks in advance

---

### Post by muteXe on 2009-10-08
Need a space after include?

---

### Post by tonysonney on 2009-10-08
> **muteXe said:**
> Need a space after include?

Thanks for the quick reply. But I dont think it is the problem with space as it has already found the file and it is complaining about the line 113 in the file types.h. If I am not wrong [HTML]include/linux/types.h[/HTML] is the path [HTML]/usr/include/linux/types.h[/HTML]

---

