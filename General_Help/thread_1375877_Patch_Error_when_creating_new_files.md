---
title: "Patch Error when creating new files"
date: 2010-01-08
forum: General Help
---

### Post by BCven86 on 2010-01-08
Hi,

I have created a patch that, along with patching already existing files, also creates new files that didn't exist before. I have been having a problem with the patching mechanism that it fails to actually create these new files when I try to apply the patch automatically, and skips patching those files. This is not a problem with files that already exist. It works if I go in and apply the patch manually i.e. patch -p1 -i [patch file]. The patch is being automatically applied via the openembedded/bitbake toolchain, for those who are familiar. I just wasn't sure if this was a common problem or not. 

Thanks,
Bob

---

