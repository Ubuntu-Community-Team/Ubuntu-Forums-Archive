---
title: "Problem with 10.04 Language"
date: 2010-10-20
forum: General Help
---

### Post by vishnu.vyasan on 2010-10-20
Hi Guys,

I am running on my 10.04 LTS version. Yesterday i have installed an other langauge [malayalam which is an indian language].  I could see all my UI have been changed to the local langauge and has option to log in using local langauge and English. 

Then i uninstalled the local langauge, but much of my *Nautilus* still in local langauge. I am having only one langauge in the langauge support. Then afte much trouble i found the /etc/locale file where the Lang was english us utf8 and Language was the local language. 

I cahanged the langauge to English which fixed my* nautilus but my chrome browser and some other apps UI still having the local lang. Its now a mix of local lang and English.*

What should i do to revoke back to english. At login time i can still see my local langauge in the langauge selection.

---

### Post by Brandon Williams on 2010-10-22
From the system menu, open the 'Language Support' dialog. Click 'Install / Remove Languages', deselect all languages that you want to remove, and then click 'Apply'. Wait for it to finish, and then back in the main 'Language Support' dialog, make sure that the language you want to use is at the top of the list. Click 'Apply System-Wide' to make sure this takes effect across your whole system. You might also need to change the language selection on the 'Text' tab.

---

