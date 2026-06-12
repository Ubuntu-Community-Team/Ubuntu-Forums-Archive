---
title: "Touchpad sensitivity"
date: 2010-06-01
forum: General Help
---

### Post by akernan on 2010-06-01
I did a clean install of Xubuntu 10.04, 64 bit, on a Dell Inspiron laptop with an ALPS touchpad.  I have problem of my cursor clicking outside a window, it's pain to type anything.  I installed gpointing-device-settings, it doesn't help.  I tried adjusting the pressure with it but it does not save my changes.  I've tried xinput and get errors.  How can I adjust the sensitivity of the touchpad?

Thanks,
Tony

---

### Post by pqwoerituytrueiwoq on 2010-06-01
try tpconfig
found it in the software center i typed in 'alps'

---

### Post by akernan on 2010-06-01
I tried tpconfig --tapmode=0 to disable tapping and I got [/B]Could not open PS/2 Port [/dev/psaux][/B].

---

### Post by akernan on 2010-06-02
> **akernan said:**
> I tried tpconfig --tapmode=0 to disable tapping and I got [/B]Could not open PS/2 Port [/dev/psaux][/B].

I figured out the problem, I needed to enter sudo tpconfig --tapmode=0.  Hopefully this will fix my problem.

---

### Post by akernan on 2010-06-02
Turning tapmode off with tpconfig did not fix my sensitivity issue.  Any ideas?

---

