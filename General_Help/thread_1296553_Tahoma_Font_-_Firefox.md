---
title: "Tahoma Font - Firefox"
date: 2009-10-20
forum: General Help
---

### Post by jim78 on 2009-10-20
Hi,

Can anyone help me out with getting firefox to use the tahoma font? I've got it installed in Jaunty and it works fine, but Firefox looks terrible since I installed it. It seems to work for some thing and not for others.

---

### Post by winotree on 2009-10-20
You might try adding this
```
/* global font */
* {
  font-size: 8pt !important;
  font-family: Tahoma !important; 
}
```to your **user.Chrome.css** inside Firefox profile.  Just be sure to add it below the line
```
/*
 * Do not remove the @namespace line -- it's required for correct functioning
 */

@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); /* set default namespace to XUL */
```of course changing the *8pt* font to something suitable for your setup.  Now -- this should change the font throughout all of Firefox.  You did, of course change it in your settings, too, which should have changed it throughout your system...  :)

---

### Post by winotree on 2009-10-25
Hmm -- it seems the advice I gave you, that apparently worked so well for me in the past, is no longer valid since one of the recent Koala 9.10 updates.  I took that line of code out and will wait until the final version comes out before making a decision, unless I find a decent solution first.   :|

---

### Post by winotree on 2009-10-25
Take a look at this thread [http://ubuntuforums.org/showthread.php?p=7094387](http://ubuntuforums.org/showthread.php?p=7094387) and see if it'll help.  :|

---

