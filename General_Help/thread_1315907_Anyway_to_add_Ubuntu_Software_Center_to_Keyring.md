---
title: "Anyway to add Ubuntu Software Center to Keyring?"
date: 2009-11-05
forum: General Help
---

### Post by jperez on 2009-11-05
Hi all,

I was wondering if there was a way to set up the Ubuntu Software Center into the keyring so that you'd enter your password once and that would be the end of it until you closed out the program and opened it up again.

My mother is trying out Ubuntu and she likes it's speed, stability, ease of use, default theme, etc., but can't stand having to enter in the password every single time she wants to add and remove a program from the software center.

In cased this makes any difference, I set her up using the Wubi installer for now.

Any help would be greatly appreciated. :D

Jesse~

---

### Post by Giblet5 on 2009-11-05
Add ```
momsaccount ALL=NOPASSWD: synaptic
``` to sudoers.

---

### Post by jperez on 2009-11-05
B0rked her sudoers; fixing at the moment.

Said there was an error in line 26, which was the line I added.  I'm looking up some documentation on sudoers.  Thanks anyway.

Jesse~

---

### Post by Giblet5 on 2009-11-05
Oops.

That should be ```
momsaccount ALL=NOPASSWD: /usr/sbin/synaptic
```

Sorry. You have to be specific with sudoers...

---

### Post by jperez on 2009-11-05
Yeah, figured it out just before looking at your post. :p

Thanks for the reply.  Now I'll know to use:

```
which **application name**
```

This way I can add whatever I need.  Thanks for the useful info and for getting me off my butt to look for more info on this.  Taught me new stuff. :D

Jesse~

---

### Post by jperez on 2009-11-05
Sorry for the double post, but it seems not to have worked. :x

I tried installing a couple games on her computer and it still asked for authentication.  I added **/usr/sbin/synaptic**, **/usr/bin/software-center** and even **/usr/bin/apt-get**.

It reads:

```
heraccount ALL=NOPASSWD: /usr/sbin/synaptic, /usr/bin/software-center, /usr/bin/apt-get
```

Am I missing something there? :-?

Jesse~

---

### Post by Tim_Magee on 2009-11-12
Jesse - I had this same thing.  Package manager works fine with the NOPASSWD flag, but the apps installer seems to have ideas above its station.  I edited the menu entry for it and changed the command used to run it to:

gksu /usr/bin/software-center

and now all is copacetic.

HTH,
Tim
[COLOR=Red]
[B]EDIT: I DO NOT ADVISE USING THE ABOVE QUOTE WORKAROUND UNQUOTE because the software center is running with EUID root.  When you use the 'website' button root's default browser will be fired up, and you will be accessing the web AS ROOT.  It's difficult to overstate what a bad thing that is.

Sorry for raising your hopes,
Tim
[/B][/COLOR]

---

