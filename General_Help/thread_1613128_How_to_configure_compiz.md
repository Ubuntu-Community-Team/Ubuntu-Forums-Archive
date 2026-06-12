---
title: "How to configure compiz"
date: 2010-11-04
forum: General Help
---

### Post by gauravbutola on 2010-11-04
I cant set compize animations. In Lucid I could set the animations for maximize,close,minimize but in maverick I cant seem to get that working.
I do the same that I did in Lucid, Go to Effects > Animations and select check box all to get random effects.
One more thing, The flame effect is also missing there.

Thanks 
Gaurav Butola

---

### Post by JOHNNYG713 on 2010-11-04
First if you have updated compiz via a compiz PPA in your software sources remove it! Go to synaptic mark compiz and all its accessories for complete removal and press "apply", logout and back in then reinstall compiz and all its accessories, and you should be good to go!

---

### Post by wojox on 2010-11-04
And install

```
compiz-fusion-plugins-extra
```

to get your fire effect.

---

### Post by gauravbutola on 2010-11-04
I have not updated compiz, just the installation from software centre.

---

### Post by gauravbutola on 2010-11-10
after 6 days of no response, I really need to BUMP this.
help please

---

### Post by a-user on 2010-11-10
you do not need to do what [JOHNNYG713]("http://ubuntuforums.org/member.php?u=849983") said. i fact i do not recommend this, because i saw that version of compize has far more dependencies to stuff i don't want installed (like KDE).

your solution is what wojox already said.

so what do you want more?

---

### Post by mister_playboy on 2010-11-10
I would also recommend installing the CompizConfig Settings Manager and the Compiz Fusion Icon.  You can find them in the Software Center.

---

### Post by gauravbutola on 2010-11-10
> **mister_playboy said:**
> I would also recommend installing the CompizConfig Settings Manager and the Compiz Fusion Icon.  You can find them in the Software Center.
I have had all the above mentioned things already installed but still it doesn't work.
I have activated animations and animation add on plugins. But I cant enable the animations

---

### Post by shantiq on 2010-11-13
> **gauravbutola said:**
> I cant set compize animations. In Lucid I could set the animations for maximize,close,minimize but in maverick I cant seem to get that working.
I do the same that I did in Lucid, Go to Effects > Animations and select check box all to get random effects.
One more thing, The flame effect is also missing there.

Thanks 
Gaurav Butola

1.   flame effect you need effects/animation add-on ticked in then it appears


2. also just to make sure re-run to make sure everything is there

```
sudo apt-get install compiz compiz-plugins compiz-gnome compiz-core emerald compiz-fusion-plugins-main compiz-fusion-plugins-extra fusion-icon compizconfig-settings-manager
```


3.   make sure you have ticked


effects   / animations
 "        / paint fire on the screen

---

