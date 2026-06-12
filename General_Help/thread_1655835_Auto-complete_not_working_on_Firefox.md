---
title: "Auto-complete not working on Firefox"
date: 2010-12-30
forum: General Help
---

### Post by woodyg on 2010-12-30
A very annoying bug has been around for some time now. Auto-complete in the address field on Firefox does not work after Ubuntu resumes after screensaver. What I have to do is to minimise the browser and then maximise it again... it then auto-complete as it should. Surely I cannot be the only one noticing this? I'm on Ubuntu 10.04 and Firefox 3.6.13.

What is going on here? Ideas?

---

### Post by BigAl-SA on 2011-01-30
> **woodyg said:**
> A very annoying bug has been around for some time now. Auto-complete in the address field on Firefox does not work after Ubuntu resumes after screensaver. What I have to do is to minimise the browser and then maximise it again... it then auto-complete as it should. Surely I cannot be the only one noticing this? I'm on Ubuntu 10.04 and Firefox 3.6.13.

What is going on here? Ideas?

Can't help you, but can confirm the problem, which is not present in Kubuntu.

---

### Post by asmoore82 on 2011-01-30
I can confirm this as well, seems to effect me after suspend/resume.

I would guess that Compiz "Desktop Effects" have something to do with it.

---

### Post by woodyg on 2011-01-30
> **asmoore82 said:**
> I can confirm this as well, seems to effect me after suspend/resume.

I would guess that Compiz "Desktop Effects" have something to do with it.

Thanks for this input. You seem to be right. Do:

**System>Preferences>Appearance. Go to the Effects tab and select None.**

and the problem seems to be gone.

---

### Post by Vaphell on 2011-01-30
yes, compiz is the problem here. The bug in question is about drawing windows in an incorrect order after resume. 'Window' with suggestions is erroneously drawn below the firefox main window and that is the reason why you can't see it. If you want to have compiz effects enabled, you need to unfocus FF and focus it again (e.g. alt-tab) to have the suggestions visible/working.
Truly annoying 'feature' :/

---

### Post by BigAl-SA on 2011-05-06
Glad to see that this has been fixed with FF4 8-)

---

