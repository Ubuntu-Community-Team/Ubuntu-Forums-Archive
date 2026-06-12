---
title: "I installed additional input languages but ibus doesn't detect it?"
date: 2011-01-28
forum: General Help
---

### Post by cat0752 on 2011-01-28
I'm on Ubuntu 10.10

I installed 2 new languages I wanted to use on my system.  Japanese and Thai.  

After installing the two languages I changed the "Keyboard input method system" to ibus.

Then I went into System >> Preferences >> Keyboard Input Methods (which is the ibus preferences screen)

When I choose "input methods" and try to add a new language that I installed, I only have Japanese as being listed.  I can successfully switch to Japanese and use it without a problem.  However it doesn't even show Thai language as being an option to use.

I installed the languages through the System >> Administration >> Language Support, Install / Remove Languges option.  In the "Install / Remove Languages" screen both Japanese and Thai have a check mark by them indicating they are installed.  And when I look at the details for each language there is a check mark by the "input methods" indicating everything was installed for them to be used not only for displaying that kind of language correctly but also for using it as an input method.

I've uninstalled the thai language, rebooted and installed it again hoping maybe it was just some little glitch, but that had no effect.

Can anyone help me figure out what to do about this?  Maybe I'm just missing something.  I was using Thai before on ubuntu 9.10 and it seemed to work ok.

---

### Post by cat0752 on 2011-01-31
Bump.

---

### Post by cat0752 on 2011-02-01
Bump

---

### Post by heypaisa on 2011-07-28
Try either,
```
sudo apt-get install ibus-m17n
```
or 
```
sudo apt-get install ibus-table-thai
```

More info here,

[http://ubuntuforums.org/showthread.php?t=1496180](http://ubuntuforums.org/showthread.php?t=1496180)

[https://bugs.launchpad.net/ubuntu/+source/language-support-input-th/+bug/704250](https://bugs.launchpad.net/ubuntu/+source/language-support-input-th/+bug/704250)

---

