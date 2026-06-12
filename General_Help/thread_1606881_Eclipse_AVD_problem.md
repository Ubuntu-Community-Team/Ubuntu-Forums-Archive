---
title: "Eclipse AVD problem"
date: 2010-10-27
forum: General Help
---

### Post by kmccmk9 on 2010-10-27
Hello I am trying to get Eclipse and the Android SDK working in Ubuntu. So far everything works except when you try to create a new Android project and, the build target area is grayed out. Why? I did run the android tool inside the sdk folder and created and Android 2.2 AVD. Why is it not reading it?

---

### Post by leg on 2010-10-27
Which version of Eclipse are you using. If you have downloaded the latest version (Helios) from Eclipse site it has a bug regards the AVD. If you install Galileo from the package manager it will work.

---

### Post by kmccmk9 on 2010-10-27
> **leg said:**
> Which version of Eclipse are you using. If you have downloaded the latest version (Helios) from Eclipse site it has a bug regards the AVD. If you install Galileo from the package manager it will work.

Thank You for your reply. I was using the latest version. After reading your post I tried the older version and for some reason it is still not reading the targets. Is it possible my sdk folder is in the wrong location? I had put it in the ROOT folder. But maybe it needs to go with Eclipse?

---

### Post by leg on 2010-10-29
I can't really remember any specifics other than Helios doesn't work properly. I followed the documentation from [this link]("http://developer.android.com/sdk/installing.html") and managed to get it working from that.

---

