---
title: "checkgmail giving 404 error?"
date: 2010-10-31
forum: General Help
---

### Post by josephellengar on 2010-10-31
I can't quite figure this out.  I have changed nothing about the configuration of my checkgmail except for the icons.  And yet, whenever I click on the subject of an email, it gives me a 404 error.  When I use the links (delete, spam, archive, mark read) it does what it is supposed to do, but it does not allow me to view the content of a message.  Does anybody have any idea of what could be causing this strange behavior?  Gnome.  10.04.  x64.

---

### Post by josephellengar on 2010-11-01
bump

---

### Post by Cajuin on 2010-11-01
I have the same problem, it started a couple of weeks ago.

---

### Post by josephellengar on 2010-11-01
Was the program updated in that time?  Do we know the version numbers?

---

### Post by Aviendha09 on 2010-11-02
Same here, started yesterday.

---

### Post by Tesko Value on 2010-11-03
Yep me too, Thought I'd messed something up. Looks like a problem. I tried using other things but I reckon Check Gmail is the best.

---

### Post by DanaLou on 2010-11-03
I had some issues a few hours ago with google talk, and gmail. Couldn't access either, but after 10 minutes or so, all started working again. 

I don't think it's Ubuntu since I've had intermittent issues here when using Windows, so it's likely a google problem.

---

### Post by Tesko Value on 2010-11-03
[http://checkgmail.sourceforge.net/](http://checkgmail.sourceforge.net/)

Theres a fix available from here :) woohoo!

---

### Post by Tesko Value on 2010-11-03
Ah no there isnt. boohoo

---

### Post by josephellengar on 2010-11-03
> **Tesko Value said:**
> Ah no there isnt. boohoo

No, didn't work for me either.

---

### Post by MyR on 2010-11-04
This bug is present in the latest 1.14-pre-svn.

Problem for me also started a couple weeks ago.

No checkgmail update brought this upon us.  Google likely changed something, as they do from time to time.

checkgmail needs to be updated to work with the change in google.

---

### Post by stevo1977 on 2010-11-09
I, too, am experiencing this problem.  In addition, this morning it stopped recognizing my password and won't check mail.

I thought I'd try "checkgmail -update" again, just to see if that fixed anything.  After updating and replacing the /bin file, I got this message:

"Restarting checkgmail . . .
Unable to find gmail_ik . . . full message text won't work :("

I googled "Unable to find gmail_ik" but came up with nothing.  Anyone know what this is about?

Cheers,
stevo

---

### Post by Aviendha09 on 2010-11-09
Are the project's maintainers even aware of this problem?

---

### Post by taro_curly on 2010-11-10
The developers seem to have fixed this problem. Running "checkgmail -update" should do the trick. Ah, things are good again! :-)

---

### Post by Aviendha09 on 2010-11-10
Good, it worked. Phew!

---

### Post by stevo1977 on 2010-11-10
Hey, alright!  Speedy and effective work, mysterious developers!  My sincere thanks.

Cheers,
stevo

---

