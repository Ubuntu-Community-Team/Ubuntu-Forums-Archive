---
title: "AOL mail causes 10.04 crash to login screen"
date: 2010-05-04
forum: General Help
---

### Post by shuknjive on 2010-05-04
Just upgraded 8.04 LTS to 10.04 LTS via a distribution upgrade on a Dell Latitude D600 laptop with nvidia-common driver 0.2.23 installed.  Everything seems to be working fine with the exception of AOL mail.  When I try and access my mail, the screen goes black and then the login screen is displayed.  Yahoo mail works fine.  Has anyone else had this problem?  Is there a bug report?  If so, what is the fix?

---

### Post by shuknjive on 2010-05-04
Anyone?  Anyone at all?

---

### Post by tgalati4 on 2010-05-04
Do you have noscript and adblock installed in firefox?  It could be a flash ad crashing.

---

### Post by BlueVark on 2010-05-04
I agree...it can be related to NoScript.  If you have that Firefox add-on, then disable it.

---

### Post by shuknjive on 2010-05-04
When I return from work, I'll check the extensions that are installed.  I don't recall either AdBlock or NoScript being listed in my extensions, but I'll double check.

---

### Post by shuknjive on 2010-05-04
I installed sun-java and the jre from the partner repository and I also disable the Unbuntu Firefox Modifications extension in Firefox.  That seemed to have done the trick.  When I turned the extension back on, the problem resurfaced.  Turned the extension off again, the problem went away.  I'm not sure if installing sun-java is necessary as I did not test turning the extension off prior to installing it.  I hope this helps someone.  Unfortunately, now I have lost all sound from ANY program.  I get the Ubuntu bongos at the sign in screen, but after that there is no Ubuntu theme song or any other sounds for that matter.  I've started a new post for my sound issue.

---

### Post by shuknjive on 2010-05-06
Well, I thought I had it fixed, and it resurfaced.  This time I fixed it for good.  I reinstalled 8.04LTS and tossed the 10.04LTS disk in the trash.

---

