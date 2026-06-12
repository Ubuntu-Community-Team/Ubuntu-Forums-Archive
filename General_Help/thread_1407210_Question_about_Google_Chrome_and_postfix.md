---
title: "Question about Google Chrome and postfix"
date: 2010-02-15
forum: General Help
---

### Post by tomdkat on 2010-02-15
I'm running Ubuntu 9.10 64-bit and when I ran a software update just now, I noticed a postfix update was downloaded along with a lsb update and an update of Google Chrome for Linux.

After the update completed, I went to Synaptic Package Manager to remove postfix because I don't have a need for running a mail server on my system.

When I selected postfix for removal, I was informed that Google Chrome would be removed as well.  Of course, this caught me completely by surprise.

A web search didn't provide any info on this so I'm posting here to see if anyone knows anything about this.

Does Google Chrome for Linux depend on postfix?

Thanks!

Peace...

---

### Post by Yfrwlf on 2010-02-15
"Yes", because it's marked as a dependency.  Of course you meant does it *actually* need it.  Why would they mark it as such if it didn't...

It seems very odd that it would want Postfix, fully agreed.  Should monitor Postifx for any activity perhaps.  I think it's a great question for the Google Chrome boards though.

---

### Post by onyxwolf on 2010-02-16
Same here. I've found your post on the chrome forums. Below is a link so others can easily find it, though it hasn't been answered yet. Maybe they'll answer if more people have this question, so give it a +1 at:

[http://www.google.com/support/forum/p/Chrome/thread?tid=623c013ee6fc1045&hl=en&fid=623c013ee6fc104500047fbf29656ba9]("http://www.google.com/support/forum/p/Chrome/thread?tid=623c013ee6fc1045&hl=en&fid=623c013ee6fc104500047fbf29656ba9")

---

### Post by TrombaMarina on 2010-02-17
Looks like a mistake that's been fixed.  Just have to wait for the fix to be released:

[http://code.google.com/p/chromium/issues/detail?id=35639](http://code.google.com/p/chromium/issues/detail?id=35639)

I wish I had read that before applying the "upgrade" and kept my old version of chrome until a new version came out that didn't require all that stuff.

The ticket lists the following packages (for those of you, like me, who plan to uninstall them as soon as the next version of chrome arrives):
alien heirloom-mailx libqt4-gui libqt4-sql-sqlite librpm0 librpmbuild0 librpmio0 lsb lsb-core lsb-cxx lsb-desktop lsb-graphics ncurses-term pax postfix rpm

---

### Post by rajeev1204 on 2010-02-24
THis is a silly bug and to get around this problem,instead of the gui installer use sudo dpkg -i --force depends google.....deb




rajeev

---

### Post by Yfrwlf on 2010-03-01
I wonder how you accidently add dependencies like that though...seems very very silly indeed.

---

