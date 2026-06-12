---
title: "Running a script/ patch"
date: 2010-12-01
forum: General Help
---

### Post by joeheim on 2010-12-01
Hi there,
 
the following script/patch should fix a problem with backlight issues (Fn-F5/F6 does not work) on a Sony Vaio VPC z-series.
But obviously my knowledge is not good enough to get it working/ running.
The patch is from the following website: [https://bugzilla.kernel.org/show_bug.cgi?id=22722](https://bugzilla.kernel.org/show_bug.cgi?id=22722)
 
 
> commit a33950b5baa848ff7851b9efd4c5e2eaafd370f2
Author: Mattia Dongili <malattia@linux.it>
Date: Thu Nov 18 22:20:36 2010 +0900
 
Input: fix typo in keycode validation supporting large scancodes
 
Check the input_keymap_entry keycode size (u32) instead of the device's
(void*).
Fixes: [https://bugzilla.kernel.org/show_bug.cgi?id=22722](https://bugzilla.kernel.org/show_bug.cgi?id=22722)
 
Cc: Mauro Carvalho Chehab <mchehab@redhat.com>
Cc: Dmitry Torokhov <dtor@mail.ru>
Signed-off-by: Mattia Dongili <malattia@linux.it>
 
diff --git a/drivers/input/input.c b/drivers/input/input.c
index 7f26ca6..5edc41a 100644
--- a/drivers/input/input.c
+++ b/drivers/input/input.c
@@ -753,7 +753,7 @@ static int input_default_setkeycode(struct input_dev *dev,
if (index >= dev->keycodemax)
return -EINVAL;
 
- if (dev->keycodesize < sizeof(dev->keycode) &&
+ if (dev->keycodesize < sizeof(ke->keycode) &&
(ke->keycode >> (dev->keycodesize * 8 )))
return -EINVAL;

 
Thanks

---

