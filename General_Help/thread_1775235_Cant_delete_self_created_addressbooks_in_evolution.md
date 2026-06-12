---
title: "Cant delete self created addressbooks in evolution"
date: 2011-06-04
forum: General Help
---

### Post by gofurygo on 2011-06-04
Hello

I recently got myself a new computer and I installed Natty (already had Maverick on my notebook) right away.

While setting up Evolution, I ran into the following problem:

I imported a csv. file (from my webmail account) --> worked fine. Since all contacts were in the "personal" addressbook, I created a few ones myself and I started to sort the contacts into those newly created addressbooks by drag and drop. This, didnt work. I ended up with 4 addressbooks containing the same amount of contacts (and the same contacts) although I sorted them differently. So I deleted all contacts again because I wanted to start from scratch... also, I tried to delete the created addressbooks... but evolution gave me a message "addressbook cant be deleted" :( ...

Does anybody know how to delete those custom addressbooks within nautilus...? And why sorting contacts cant work as desired... I really like Evolution, but imho it has "many" small annoyances...but at least it got better over the last version in maverick ;)

Thanks in advance

---

### Post by broseman on 2011-06-05
Just want to let you know, that I'm running into the exactly same issue.
Still have no idea, how to fix it, didn't even find a bug report for this -- but I can't believe that we two should be the only ones...

---

### Post by gofurygo on 2011-06-05
Hey there...

I found a "fix"...

go to /home/yourusername/.gconf/apps/evolution and delete the addressbook directory... after rebooting, all addressbooks were gone and I could start from scratch. I didnt try to delete the newly created addressbook again...so maybe this workaround just fixes half the issue...

Cheers

---

### Post by broseman on 2011-06-05
Hi.

thanks, I tried your fix, but I still have the problems (i.e. all entries are appearing in every newly created addressbook, deleting is not possible, ...)

thanks anyway!

broseman

---

### Post by broseman on 2011-06-05
Hi there, it's me again.

I found two bug reports.
A fresh on in launchpad:
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/779523](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/779523)
(Please hit the button "I'm affected")

And and old one in GNOME Bugzilla:
[https://bugzilla.gnome.org/show_bug.cgi?id=558777](https://bugzilla.gnome.org/show_bug.cgi?id=558777)

---

### Post by gofurygo on 2011-06-06
Hi again.

I basically followed this "fix": 
[http://ubuntuforums.org/showpost.php?p=4308835&postcount=2](http://ubuntuforums.org/showpost.php?p=4308835&postcount=2)

I forgot to mention to delete the addressbook in the .evolution directory as well because for some reason I didnt have that directory. So I only went for the gconf thingy... Like I said. Dont close and open evolution after you deleted those directories. You really need to reboot... see the link as well.

Cheers, hope it will work

---

### Post by broseman on 2011-06-07
I' sorry, still no luck.
But thanks again for your help!
I will continue searching (maybe for a better app ...?)

---

