---
title: "Quanta 3.5 - file modified problem"
date: 2006-01-25
forum: General Help
---

### Post by robodesign on 2006-01-25
Hello!

I have installed Ubuntu 5.10 and I enabled multiverse and universe.

I updated everything to the latest available version. I also installed Kubuntu metapackage because I, of course, want to play with KDE too (and I also need Konqueror for web development testing).

Now ... I wanted Konqueror 3.5 (because it properly renders the famous [Acid 2 test](http://www.webstandards.org/act/acid2/)). 

On [Kubuntu.org](http://www.kubuntu.org) I found an announcement about [KDE 3.5 packages being available](http://kubuntu.org/announcements/kde-35.php). I added the repository and I installed KDE 3.5.

All peachy and working properly.

Except ... Quanta :(. When I save a file it always complains about the file being modified (which is wrong). This bug has been reported in [KDE Bug Tracking System](http://bugs.kde.org/show_bug.cgi?id=118015).

> ------- Additional Comment #7 From András Man&#355;ia 2006-01-17 14:29 ------- 
The bug is in Kubuntu's kernel + kdelibs combination. I checked with 
Kubuntu and I can reproduce with it. The problem is the kernel's 
inotify support is broken and the original KDE 3.5.0 release does not 
have a check to see if you have broken inotify or not. The solution: 
- upgrade to a kernel which does not have the bug 
- upgrade kdelibs to a version where inotify is disabled (you may 
compile from source the 3.5 branch) 
- bug the ubuntu developers to do the above ;-)

How to easily do any of the suggested solutions? Where can I get a kernel that doesn't have the bug? Or what else to do?

I'd really like to keep KDE 3.5 and not downgrade to 3.4.

Thank you very much.

P.S. Sorry if this is not the appropriate forum to post this thread (I am not sure which is *the* one).

---

