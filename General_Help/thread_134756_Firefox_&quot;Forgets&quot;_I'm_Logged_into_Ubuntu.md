---
title: "Firefox &quot;Forgets&quot; I'm Logged into Ubuntu Forums"
date: 2006-02-22
forum: General Help
---

### Post by ronmarley1 on 2006-02-22
Here's a good one.  I just reformatted and reloaded Breezy.  After reloding Firefox 1.5.0.1, this happens (by the way, I'm writing this from my XP box :mad: ): I go to this forum and log in.  I check the box that reads "Remember Me?"  I get the redirect page that says, "Thanks for logging in..." and then I get sent back to the forum page.  At that point, it's as if I'm not logged into the site.  If I go to Tools, Clear Private Data and then log in again, it remembers me.  Then, as soon as I click on a posting, it forgets I'm logged in again.  If I go to reply to a post, it asks me to log in again, I do, I get the "Thanks for logging in..." and then it goes back to the vBullitan Message asking me to log in before I post.  The really sad part is that it worked before I reloaded Breezy and works on Windows.  Any ideas?
Thanks...

**[COLOR="Red"]SOLUTION![/COLOR]**  On a hunch, I did this, and it fixed it!
open a shell and delete the file "default.keyring" in $HOME/.gnome2/keyrings/
you'll loose all the passwords but can set a new default keyring password next time nautilus asks you.

---

### Post by kaamos on 2006-02-22
Do you have cookies enabled?

---

### Post by ronmarley1 on 2006-02-22
Thanks for the quick reply.  I do have cookies enabled (that was my first guess), and I even added an entry that always allows cookies for the ubuntu forum page.  Could it be a rights issue to the folder where the cookies are stored?

---

### Post by kaamos on 2006-02-22
Strange. Well, that sounds like a possible reason.. Did "sudo chown ronmarley1:ronmarley1 ~/.mozilla/firefox -R" do any good?

---

### Post by evilgold on 2006-02-22
Sounds like a cookie problem. How/where did you install firefox? Try installing a different browser (konqueror, opera, ect) and see if the same thing happens.

---

### Post by ronmarley1 on 2006-02-22
Hi kaamos and evilgold,
I thought I'd cut some corners and install Firefox uxing Automatix.  That's gotta be it.  I'm gonna remove it and reinstall manually.  Thanks for the replies.

PS, kaamos, I tried the code you added, but that did not help.

---

### Post by Jason_25 on 2006-02-22
Did you make sure to click "remember me" before logging in?

---

### Post by alfonz on 2006-02-22
hmm check to see if you have clear private data on close enabled and open about:config 

scrool down privicy sanitize section and make sure it isn't set to false

privacy.sanitize.promptOnSanitize  userset  boolean   false <--

setting this to true will prompt you on exit if you want to clear private data


you might have to run FF as root for this 

```
gksudo firefox
```

---

### Post by ronmarley1 on 2006-02-22
I checked "Remember Me?"  and even if I run it as root, it still "forgets" I've logged in.  I checked the about:config setting and it seems right.  I'm gonna reinstall.

---

### Post by ronmarley1 on 2006-02-22
Welp, I reinstalled and it's still the same.  Everything works fine (I can log into other gated sites and it seems to remember me).  I gotta figure this out, so I can keep posting to this forum...  wish me luck...

---

### Post by suRoot on 2006-02-22
FWIW, I have the same problem.  I also installed FF 1.5 with Automatix.

---

### Post by soongwoo on 2006-02-22
I have same problem, too. in old FF and new FF.
I install Firefox 1.5.0.1 not with Automix.
It does not matter whether "Remember me" check box is clicked or not.

soongwoo

---

### Post by ronmarley1 on 2006-02-22
There's another thread going on this.  I'm glad it's not just me!  Here's the link to the other thread: [http://www.ubuntuforums.org/showthread.php?t=134620&highlight=cookies](http://www.ubuntuforums.org/showthread.php?t=134620&highlight=cookies)

---

