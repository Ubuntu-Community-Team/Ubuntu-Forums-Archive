---
title: "Can't change language at login window?"
date: 2010-12-01
forum: General Help
---

### Post by abcuser on 2010-12-01
Hi,
I have two languages English and Slovenian in Ubuntu 10.10. I would like to change language at login window, but this does not work for me. Changing the language at logon window and nothing happens it stays in Slovenian.

The only way to change to English is to:
1. System | Administration | Language Support
2. In Language tab move Slovenian language down the list that Slovenian language becomes grayed out
3. Click on Apply System-Wide
4. Text tab. English (United States) from drop down menu and Apply System-Wide
5. Logout
6. At login window select English.

To get back to Slovenian.
1. System | Administration | Language Support
2. In Language tab move Slovenian language to the first place in the list that Slovenian language becomes visible (not grayed out)
3. Click on Apply System-Wide
4. Text tab. Slovenian from drop down menu and Apply System-Wide
5. Logout
6. At login window select Slovenian.


Is there any easier way? If I remember correctly, in previous version language change was done using login window, but this does not work any more. I have contacted my friends and some of them have the same problem like me and some of them can change language at login window.

Any idea what is wrong with my system? How to make it possible to change language on the fly with only logout/login window settings?

Thanks

---

### Post by nervoso on 2010-12-05
bump - I have the same problem.

---

### Post by abcuser on 2010-12-07
It looks this is some kind of bug. I have reported a bug in Launchpad.

nervoso, if you have the same problem, can you please click on link
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/686665](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/686665)

and click on link "This bug affects x people. Does this bug affect you?" and then select "Yes it affects me".

More people having the same problem, better change to someone look at the bug report and try to fix the problem.

---

