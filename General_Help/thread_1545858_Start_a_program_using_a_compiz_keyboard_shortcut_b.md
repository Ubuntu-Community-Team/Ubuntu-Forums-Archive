---
title: "Start a program using a compiz keyboard shortcut but w/o LIBGL_ALWAYS_INDIRECT?"
date: 2010-08-04
forum: General Help
---

### Post by Zorgoth on 2010-08-04
This is what I do right now for this problem:

bash -c "unset LIBGL_ALWAYS_INDIRECT && my_command"

I could assign whatever value I want to LIBGL_ALWAYS_INDIRECT, but what do I have to do is unset it without creating a pointless bash process?  Is that possible?

---

