---
title: "Options along bottom of gdm have vanished"
date: 2010-06-11
forum: General Help
---

### Post by josephellengar on 2010-06-11
All of the options along the bottom of my gdm have vanished- you know, the bar with the option to change session, language, turn off, restart, etc.  That whole bar is no longer there.  Does anybody know how I can turn it back on?  :confused:

---

### Post by josephellengar on 2010-06-12
bump

---

### Post by josephellengar on 2010-06-13
bump.  Please, anybody have a solution?  It's impossible for me to log in to KDE like this.

---

### Post by josephellengar on 2010-06-13
Okay, I've spent about an hour googling this and nobody seems to have an answer.  Would my best bet be to just switch to KDM?  I'd hate to do that just because it would mean installing all of the KDE bloatware and whatnot, but I will if I have to, to get back the bar along the bottom.

---

### Post by josephellengar on 2010-06-13
Oh, and the options do not reappear when I choose a user.

---

### Post by chemicals on 2010-06-13
What i would do, is log into kde, then try installing gnome 

sudo apt-get install ubuntu-desktop 

should do the trick. It wont double install, but may install the bits your missing and kick start it.

---

### Post by josephellengar on 2010-06-13
Thanks for replying.  But how do I log into kde without the options menu?

---

### Post by chemicals on 2010-06-13
Sorry, i assumed you could log in to something. 

Im not sure how to do it, but you can log into a command shell somehow. maybe try that?

---

### Post by josephellengar on 2010-06-13
> **chemicals said:**
> Sorry, i assumed you could log in to something. 

Im not sure how to do it, but you can log into a command shell somehow. maybe try that?

Well, I can log into gnome and only gnome.  The menu along the bottom that lets you select the session is gone so I cannot log into kde.  I'll try doing this from gnome.  When I log into just a shell I get no internet, so that won't work.  I'll report back in a few minutes with the results.  Thanks for your help.

---

### Post by chemicals on 2010-06-13
Ah well try this from the terminal

sudo apt-get install kubuntu-desktop

---

### Post by josephellengar on 2010-06-13
> **chemicals said:**
> Ah well try this from the terminal

sudo apt-get install kubuntu-desktop

I have kde installed.  It's impossible to log into because I have no sessions option in gdm.

---

### Post by chemicals on 2010-06-13
yes, but try installing it again. It wont install it twice, but it may fix the problem if youve managed to delete sometihng you need

---

### Post by josephellengar on 2010-06-13
> **chemicals said:**
> yes, but try installing it again. It wont install it twice, but it may fix the problem if youve managed to delete sometihng you need

Oh, yeah good point.  I tried it with gnome and the bar did not reappear, so now I'll try with kde, see if that's enough.

---

### Post by rahilm on 2010-06-13
What happens if you try re-installing gdm??
like 
sudo apt-get purge gdm

then it will show that some apps have to be removed with it, take a note of them and then install them again.

---

### Post by MooPi on 2010-06-13
Possible solution is to boot to gnome and un-install GDM. ```
sudo apt-get purge GDM
```
Then reboot to recovery console by using the shift key during boot. While in recovery re-install GDM and reboot.
When you reinstall all dependencies should be met.

---

### Post by josephellengar on 2010-06-13
> **MooPi said:**
> Possible solution is to boot to gnome and un-install GDM. ```
sudo apt-get purge GDM
```
Then reboot to recovery console by using the shift key during boot. While in recovery re-install GDM and reboot.

That worked.  Now the options show up when I type in my username.  Thank you so much.  I'll mark this thread solved.  No idea what happened.  I was still able to change my theme in gdm and it worked properly.  Must have been some ook from when I upgraded or something.  Thank you!

---

