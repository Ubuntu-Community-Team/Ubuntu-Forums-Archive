---
title: "How to select multiple directories in grsync?"
date: 2011-12-11
forum: General Help
---

### Post by DeMus on 2011-12-11
Hi,

I use grsync to make weekly back-ups from data in 3 computers, 2 Linux and 1 Windows.
What I have always done is selecting the home folder as source and then --exclude those files and/or sub-folders I don't want or don't need. These lists, especially in the Windows profile are getting extremely long.
Is there also a possibility to work the other way around? So, instead of selecting all and then --exclude items, start with nothing and then add items? Especially in the windows machine I only need data, not all Application settings, etc. In Linux this might be handy when doing a re-install of the OS so after installation you already have all settings present.
Who can help me with this "problem"?

---

### Post by yeats on 2011-12-11
(g)rsync only works with the "--exclude" method.  The alternative way to use it to achieve what you're looking to do is to set up separate rsync commands for each directory you're trying to back up.  I pretty much just use the CLI version, so I can't advise much on the GUI version about how best to do that ;-)

---

### Post by papibe on 2011-12-11
Sort of, yes.

Using the option '--include-from=' you can put all your rules on a file. To add directories start the line with a '+', to exclude a directory use the '-'.

For your situation this becomes useful when you just list a bunch of '+' entries, and then you finish the file with a '- *'. That would basically means exclude anything else not mention in the previous rules.

Note that, in my experience, it takes a few trials to get the rules right, so play and test them before the final backup.

Check this [thread]("http://ubuntuforums.org/showthread.php?t=1881554&highlight=rsync+include") with a simpler but similar situation.

Hope it helps.
Regards.

---

### Post by DeMus on 2011-12-13
> **papibe said:**
> Sort of, yes.

Using the option '--include-from=' you can put all your rules on a file. To add directories start the line with a '+', to exclude a directory use the '-'.

For your situation this becomes useful when you just list a bunch of '+' entries, and then you finish the file with a '- *'. That would basically means exclude anything else not mention in the previous rules.

Note that, in my experience, it takes a few trials to get the rules right, so play and test them before the final backup.

Check this [thread]("http://ubuntuforums.org/showthread.php?t=1881554&highlight=rsync+include") with a simpler but similar situation.

Hope it helps.
Regards.

Thank you so much. I will try that now. Will report back when done.

---

### Post by DeMus on 2011-12-13
Papibe, I did what you suggested and it works great. Thank you for this help. Now I can figure out exactly what I want to copy and what not.
Thanks again.

---

