---
title: "Java, Sun's EULA == Broken Package"
date: 2010-03-23
forum: General Help
---

### Post by donsy on 2010-03-23
Attempting to install sun-java6-jdk from a terminal session with apt-get, I was greeted with a screen containing Sun's EULA. The problem was that nowhere on that screen was a button or link or anything where I could click and accept it. There was an <OK> at the bottom but nothing happened when I clicked on it repeatedly. So I tried just hitting the <Enter> key, then <Ctrl-D>, and that didn't work either. I finally gave up and closed the terminal which killed the process and broke the package. I was able to repair the package in Synaptic but my question is: if this happens again in the future with another package, how do I accept the EULA?

---

### Post by NoBugs! on 2010-03-23
Have you tried setting the theme to back to default? I've noticed some themes may cause problems with Java windows.

---

### Post by donsy on 2010-03-23
> **NoBugs! said:**
> Have you tried setting the theme to back to default? I've noticed some themes may cause problems with Java windows.

This happened during the install with apt-get, what theme do you mean?

---

### Post by Arand on 2010-03-23
It's an ncurses interface, use the tab key to jump down to the OK button, use enter to activate it.
- Arand

---

