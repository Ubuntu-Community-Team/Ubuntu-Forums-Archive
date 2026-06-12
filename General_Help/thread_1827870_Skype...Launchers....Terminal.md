---
title: "Skype...Launchers....Terminal"
date: 2011-08-18
forum: General Help
---

### Post by MHawk on 2011-08-18
If I place LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype  in launchers, I get:
failed to load child process
"LD_PRELOAD=" (No such file or directory)

If I write the same LD_PRELOAD  line into the terminal, skype works. What am I not understanding about using the launchers?

Using Ubunto 11.04 in a Dell D600

Thanks.

---

### Post by blind2314 on 2011-08-18
> **MHawk said:**
> If I place LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype  in launchers, I get:
failed to load child process
"LD_PRELOAD=" (No such file or directory)

If I write the same LD_PRELOAD  line into the terminal, skype works. What am I not understanding about using the launchers?

Using Ubunto 11.04 in a Dell D600

Thanks.

You have to export the environment variable after setting it.

```
LD_PRELOAD=foo;export LD_PRELOAD
```

---

### Post by MHawk on 2011-08-18
Thanks for the reply. I have tried various forms of export in the launcher. The result is the same as before. BTW, I have the same problem with lucid on a Dell D610. Entering LD_PRELOAD foo worked with Karmic on the same Dell D600. Maybe I need a better understanding of the mechanics of LD_PRELOAD.

---

### Post by MHawk on 2011-08-18
MHawk;11164600]Thanks for the reply. I have tried various forms of export in the launcher. The result is the same as before. BTW, I have the same problem with lucid on a Dell D610. Entering LD_PRELOAD foo worked with Karmic on the same Dell D600. Maybe I need a better understanding of the mechanics of LD_PRELOAD.[/QUOTE]

---

### Post by plucky on 2011-08-18
> **MHawk said:**
> MHawk;11164600]Thanks for the reply. I have tried various forms of export in the launcher. The result is the same as before. BTW, I have the same problem with lucid on a Dell D610. Entering LD_PRELOAD foo worked with Karmic on the same Dell D600. Maybe I need a better understanding of the mechanics of LD_PRELOAD.

Try this in a launcher 

```
bash -c 'env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'
``` for 32-bit Ubuntu

Or

```
bash -c 'env LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype'
``` for 64-bit Ubuntu.

Good Luck

---

### Post by MHawk on 2011-08-19
> **plucky said:**
> Try this in a launcher 

```
bash -c 'env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'
``` for 32-bit Ubuntu

Or

```
bash -c 'env LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype'
``` for 64-bit Ubuntu.

Good Luck
Doesn't work with this either. But now I don't get the failed to execute statement. Click on the launcher and nothing happens.  I'll keep digging.
Thanks.

---

### Post by Zarquan314 on 2011-09-05
To put this command i used 2 files, a .sh file and a launcher.  The .sh file (I called skype.sh) contained this:

for 32 bit
```
#!/bin/bash
LD_PRELOAD=foo;export LD_PRELOAD
bash -c 'env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'
```and for 64 bit
```
#!/bin/bash
LD_PRELOAD=foo;export LD_PRELOAD
bash -c 'env LD_PRELOAD=/usr/lib32/libv4l/v4l2compat.so skype'
```

and the launcher has this in its command line

```
sh /(path)/skype.sh
```You can also have this run on startup by adding it to startup applications in system settings.

---

### Post by MHawk on 2011-10-31
I never got the problem solved by any of the above attempts. However, changing to a uvc compatible wecam DID fix things. Thanks for all the sugguestions.

---

