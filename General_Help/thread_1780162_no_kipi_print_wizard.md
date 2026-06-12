---
title: "no kipi print wizard"
date: 2011-06-11
forum: General Help
---

### Post by labatts on 2011-06-11
I have no idea if this is simple ignorance on my part, or if I am actually missing something,  However, I have kubuntu 11.04 installed on two computers.  Both computers have DIgikam installed with the kipi plugins.  

Unfortunately, there is no Print wizard.  The options are print and print assistant.  (I am assuming print assistant is not the same thing.  I have seen screenshots online of 'print wizard', and it looks much better than what I have.)

Ultimately, what I am after is an easy way to print multiple photos onto one page.  The existing options seem clunky at best.  

If someone could point me in the right direction, I would greatly appreciate it.

---

### Post by ajgreeny on 2011-06-11
Have a look at photoprint which I use on gnome, though I don't think it is specifically a gnome application.  It needs libgtk2.0-0, bit that's abouit all that seems to be specific and the whole list of dependencies is not very long.

---

### Post by labatts on 2011-06-11
Thanks for the response.  Funny you should mention Photoprint, because that is what I was using before.  I switched to Kubuntu with this last release (from gnome) and it suddenly does not work.  I noticed that there is a picklist for the correct print driver right underneath the selection for printer (the selection is correct.  The wierd thing about it was that my print driver was not an option (even though it is installed and working).  

So, when I try Photoprint, one of two things happen:  either it crashes, or it prints on only 1/2 the page (this happens when I try to pick an incorrect, yet close driver.

That is a different issue, but I would gladly take that application if there were some easy solution.  Dinking around on thier website proved unfruitful.


Edit:  Seems the Photoprint issue is not new:  [http://ubuntuforums.org/showthread.php?t=539453](http://ubuntuforums.org/showthread.php?t=539453) .  Given that I had support under 10.10, but not now, this does not seem like a good longterm solution.

---

### Post by labatts on 2011-06-13
Okay, the good news is I got photoprint to work using a PPA found at [http://ubuntuforums.org/showthread.php?p=10551371](http://ubuntuforums.org/showthread.php?p=10551371) .  I had to change the PPA to lucid (they haven't updated it and im in Natty) and then it worked fine.  

It would be nice, though to be able to use the actual Kipi print wizard.  If anyone knows anything about this, please let me know.  (as I said, it is not showing up, even though I have the kipi stuff installed).

Thanks for the help, ajgreeny.

---

