---
title: "AptOnCD not reflecting packages in /cache/archives/"
date: 2011-01-09
forum: General Help
---

### Post by N3RVE_deact on 2011-01-09
I ran into some complications with my ubuntu 10.10 install and couldn't boot into the desktop. I decided to use a live CD to get access to my downloaded cached packages and copied them to my windows partition, now I've re-installed ubuntu and manually restored the apps into the /archives/ directory, I've installed a lot of apps from the directory already but AptOnCD has refused to properly reflect the apps I have there, is there something I'm overlooking?  

[IMG]http://i54.tinypic.com/ea5lvk.png[/IMG]

---

### Post by ajgreeny on 2011-01-09
I couldn't get aptoncd to work in maverick properly.  It would produce the iso file, but then never would load it to restore anything, so I gave up with it, and simply copied all the .deb files in /var/cache/apt/archives on one machine to the same place in the other machine, which does exactly the same thing, and is hardly any more work.

I never used aptoncd to burn CDs as it seemed a waste when an iso file worked just as well until maverick.  I've searched for any bugs but found none, so again gave up on it, and now do it manually when I need to.

PS: Please add pictures as attachments, not in-line with your text; it makes the post very hard to view.
Just click the paperclip in the toolbar of the thread entry box, or reply box, navigate/browse to the pic, click "upload" and it's all done.

---

### Post by N3RVE_deact on 2011-01-11
Thanks for responding. I've been experiencing multiple issues with AptOnCD on ubuntu 10,10 too. I'll also remember to post screen shots as attachments.

---

