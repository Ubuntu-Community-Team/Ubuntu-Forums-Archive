---
title: "bibble5 symbol lookup error: /usr/lib/libkdecore.so.5: undefined symbol"
date: 2011-01-24
forum: General Help
---

### Post by daryl314 on 2011-01-24
Hello,

After a recent package update (kubuntu 10.10 i386), bibble5 (raw photo editing software) stopped working.  When I try to run it, there is a lot of output text with this on the final line:

./bibble5: symbol lookup error: /usr/lib/libkdecore.so.5: undefined symbol: _ZN9QListData11detach_growEPii

I poked around a bit on the forums, and it seems that most people had issues with LD_LIBRARY_PATH when they had this kind of issue.  However, when i try to echo my library path using ```
echo $LD_LIBRARY_PATH
``` nothing is displayed.  Does anyone have other thoughts about what I could check?

Thanks!

---

