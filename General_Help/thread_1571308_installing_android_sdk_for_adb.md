---
title: "installing android sdk for adb?"
date: 2010-09-09
forum: General Help
---

### Post by hortstu on 2010-09-09
I'm trying to install these tools so I can get root on my HTC evo. I'm not a developer so I don't need all the dev software. I just need adb so I can move some files. I have no idea what I'm doing or what the prerequisites are for the sdk software. Can anyone explain the process to me or show me a link to an idiots guide.

Thanks.

---

### Post by Calash on 2010-09-09
Once you download the kit just extract it to your home folder.  In the terminal navigate to the android-sdk-linux-86/tools folder (name may vary depending on setup)

You will need to put a ./ before the commands

example

```

./adb shell
./ddms

```

---

### Post by hortstu on 2010-09-09
thanks,  I won't need eclipse or anything else?  It's just a matter of putting it in the rught folder? I extracted it on my desktop and that didn't seem to work.

> **Calash said:**
> Once you download the kit just extract it to your home folder.  In the terminal navigate to the android-sdk-linux-86/tools folder (name may vary depending on setup)

You will need to put a ./ before the commands

example

```

./adb shell
./ddms

```

---

