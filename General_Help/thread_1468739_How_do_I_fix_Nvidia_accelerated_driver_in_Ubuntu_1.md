---
title: "How do I fix Nvidia accelerated driver in Ubuntu 10.04?"
date: 2010-05-01
forum: General Help
---

### Post by jacatone on 2010-05-01
After installing Ubuntu 10.04, kept getting this popup advising me of an Nvidia accelerated graphics driver 96. After installing it my highest resolution is 640x480 and I get the following error:

"It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead? Yes/No"

How do I get this thing to a 1024x768 resolution? Thanks.

---

### Post by Kir_B on 2010-05-01
Try the following code:

```
[COLOR=Black][**sudo nvidia-settings**]("http://ubuntuforums.org/archive/index.php/t-528224.html")[/COLOR]
```Hopefully, it will give you the necessary options to change the resolution to something that's more acceptable for you.

I hope that helps you, or someone else. Kirby   :)

---

