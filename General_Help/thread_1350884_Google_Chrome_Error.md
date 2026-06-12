---
title: "Google Chrome Error"
date: 2009-12-09
forum: General Help
---

### Post by jpmelos on 2009-12-09
Hello, everyone.

I think my Google Chrome is not processing some features right. When I enter the Chess.com website, it displays incorrectly, even though my Firefox display correctly. (I'm using the new Google Chrome, released officially by Google in beta).

I'll attach the screenshots.

Thanks for any help! :D

---

### Post by jpmelos on 2009-12-11
Bump.

---

### Post by 3rdalbum on 2009-12-11
It looks fine here. What happens if you rename the Google Chrome preferences file (it's in a hidden folder in your home directory) so it generates a new prefs file?

---

### Post by soulsource on 2009-12-11
Have you considered that the website might be buggy? Many pages display "correct" with firefox although there are coding errors.

---

### Post by jpmelos on 2009-12-11
> **3rdalbum said:**
> It looks fine here. What happens if you rename the Google Chrome preferences file (it's in a hidden folder in your home directory) so it generates a new prefs file?

I don't think it's related to that... I noticed it just after installing Chrome, so the preferences were brand new.

> **soulsource said:**
> Have you considered that the website might be buggy? Many pages display "correct" with firefox although there are coding errors.

Well, it could be that... But how can one say if it's that?

---

### Post by joes7 on 2009-12-11
Try by down-grading Chrome or by downloading an older / newer version. This should fix it. Are you sure that Chrome has the right plugins?

---

### Post by jpmelos on 2009-12-12
It's already the last version. It's going to be automatically updated when there's a new version, because the installer added the repository to the list automatically.

What do you mean it has the right plugins, I think that doesn't require any plugins... That must be plain Javascript or CSS or something like that, nothing too fancy...

---

### Post by gradinaruvasile on 2009-12-12
It looks good to me. 
Chromium 4.0.270.0 (34429) dev version.
Try with the attached script i made. It will d/l and unpack/upgrade the latest Chromium dev version (generic linux, all needed stuff included) in your home folder and make a menu link for it. It is totally different from the installed version from repositories, it doesnt change it in any way. It just uses the same preferences folder/files.
You must runt the script in a terminal. No sudo. It only writes in your home folder. 
If launched a second time, will update to the latest chromium dev version (if) available.

The menu icon is about the same as the installed version's except it is named "Chromium Browser".

---

### Post by kostkon on 2009-12-12
> **gradinaruvasile said:**
> It looks good to me. 
Chromium 4.0.270.0 (34429) dev version.
Try with the attached script i made. It will d/l and unpack/upgrade the latest Chromium dev version (generic linux, all needed stuff included) in your home folder and make a menu link for it. It is totally different from the installed version from repositories, it doesnt change it in any way. It just uses the same preferences folder/files.
You must runt the script in a terminal. No sudo. It only writes in your home folder. 
If launched a second time, will update to the latest chromium dev version (if) available.

The menu icon is about the same as the installed version's except it is named "Chromium Browser".
He is obviously running Chrome and not Chromium.

Anyway, I believe it's just a rendering problem. Since Chrome passes the Acid3 Test (and Firefox doesn't) I can safely assume that the site is buggy.

---

### Post by gradinaruvasile on 2009-12-12
Uh... ok. I see. But i rather use the open source version... Especially since it seems to work better...

---

