---
title: "Can`t change language for ubuntu unity-desktop"
date: 2012-08-06
forum: General Help
---

### Post by vasilbelarus on 2012-08-06
I live in Belarus, so my PC has two languages russian and english. My wife doesn`t now english well so she preferrussion as default language for her unity-desktop. I want to use english language as default for my unity. 
I tryed to change language in user settings(clic on panel my name-button, then "users"), here in my account setting I change language from russian to english, but after logout/login and even restart nothing change. When I go to my account preferences again the russian language still selected.
So I want to now^
1. Is it bug? 
2. Is this problem specific to my installation or you (other users) have the same problem?
3. How to change language for my ubuntu unity-desktop?
Thanks.
My system info: AMD Athlon(tm) II X2 260 Processor × 2 ,  2Gb memory, almost default ubuntu 12.04 with latest updates. Unity 3D(Nvidia proprietary driver).

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-08-06
It is not enough to just simply add a language of your choice.

If you open System Settings > Language Settings > Language, you will see a list of all the available interface languages. You need to arrange that list by dragging and dropping the languages in it. For example, if you want your Ubuntu in Russian, then you need to drag Russian to the top of the list. Then log out and back in and it should be alright.

Also, please make sure you don't confuse Language setting with Regional format setting.

---

### Post by vasilbelarus on 2012-08-06
> **&#1058 said:**
> It is not enough to just simply add a language of your choice.

If you open System Settings > Language Settings > Language, you will see a list of all the available interface languages. You need to arrange that list by dragging and dropping the languages in it. For example, if you want your Ubuntu in Russian, then you need to drag Russian to the top of the list. Then log out and back in and it should be alright.

Also, please make sure you don't confuse Language setting with Regional format setting.
Sorry, I forget to write above, I tried this wariant too, but nothing changed. There is the option apply system-wild, but I want only my desktop to be in english.

---

### Post by vasilbelarus on 2012-08-06
Bug reported [https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/1033485](https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/1033485)

---

### Post by jemadux on 2012-08-06
i had the same problem . just open the language support and drag and drop your prefenced language on top ... and aplly the system wide

---

### Post by vasilbelarus on 2012-08-06
I want to change language for user specific settings (not system wide)

---

### Post by vasilbelarus on 2012-08-06
> **jemadux said:**
> i had the same problem . just open the language support and drag and drop your prefenced language on top ... and aplly the system wide
If you have the same problem please confirm that this bug affects you at [https://bugs.launchpad.net/ubuntu/+s...r/+bug/1033485]("https://bugs.launchpad.net/ubuntu/+source/language-selector/+bug/1033485")
Thanks!

---

### Post by jonyrijo on 2012-10-23
SOLUTION. I had the exact same problem and then I tried changing the language in user accounts settings to just English, no US or UK and then it worked. I just restarted the pc and it was in English. hope this helps

---

### Post by vasilbelarus on 2012-10-26
Bug on launchpad closed - the fix was made. So, if somebody has that problem - you should only update your system, then all will be fine.
:) Good luck

---

