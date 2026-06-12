---
title: "GDM Login Language Selection Does Not Take Affect"
date: 2010-05-02
forum: General Help
---

### Post by distrachi on 2010-05-02
Clean installed Ubuntu 10.04 64-bit, default language Chinese.

When I choose Language:English at the bottom of the login screen (GDM?), after I login everything is still in Chinese. Except the only difference is that I can't type in Chinese characters, the little keyboard icon for typing in Chinese that was on the top left of screen is not there anymore.

The only way I can change languages is via System --> Administration --> Language Support. By dragging English above Chinese on the order list the next time I login everything is in English. Except the problem is that all user accounts change to English. Even if they select Chinese on the bottom of the login screen.

I could not find any information using Google. I hope I'm not the only person having this problem.

---

### Post by heldal on 2010-05-02
You're not alone. It's probably a bug. Lucid only uses the system settings for language on the desktop regardless of which language is chosen in the gdm2 login dialogue. The only effect from choosing a different language is a question about renaming certain directories (Videos, Music, Photos etc) accordingly. Menus and the environment ($LANG, $LANGUAGE) remain set as specified in /etc/environment and /etc/default/locale.

[https://bugs.launchpad.net/ubuntu/lucid/+source/gdm/+bug/407300](https://bugs.launchpad.net/ubuntu/lucid/+source/gdm/+bug/407300)
[https://bugs.launchpad.net/ubuntu-translations/+bug/553162](https://bugs.launchpad.net/ubuntu-translations/+bug/553162)

There's a number of bugs in launchpad referring to inconsistencies with language/locale.

---

### Post by distrachi on 2010-05-03
thanks heldal. Makes me feel a bit better that other people are affected by same problem. I've added myself to the affected list of Bug #553162 and subscribed.

---

### Post by tiepolo on 2010-09-17
Hello,

I corrected it by reinstalling gdm

sudo aptitude reinstall --purge gdm

Paolo

---

### Post by pietrucha23 on 2011-05-02
I have the same kind of problem. Changing user's session language in GDM does not change anything, except the way Avant Window Navigator (AWN) displays the date info. All the rest (menu, apps, notifier) is in the system's default language. It even didn't ask to change the directories names.
  All the language packages are where they should be - bilingual spell checking in Evolution, Empathy etc. works.

Paolo's reinstall trick doesn't work.

I'm running Ubuntu 10.04 64-bit with all the latest updates.

  Any suggestions?

Cheers,
   Piotr

---

