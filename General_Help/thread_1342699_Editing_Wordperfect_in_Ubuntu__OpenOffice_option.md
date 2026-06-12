---
title: "Editing Wordperfect in Ubuntu?  OpenOffice option?"
date: 2009-12-01
forum: General Help
---

### Post by rpaskudniak on 2009-12-01
Greetings, all.

Now that I have gotten my desired Windows partitions to automount, I want to actually *use* what's inside them.

One preface: Due to a weirdness when I installed XP on this box, my Windows boot drive always comes up as F:, rather than C:.  Now if all installations addressed their libraries as %System%\...\lib<something>, it might have made no difference.  But most simply grab the boot drive as the home directory.  Hence, most apps have their libraries installed explicitly under F:  Of course, wine knows nothing about this quirk and can't find anything addressed in drive F:.

Why is that relevant? Because someone is sure to suggest I run Wordperfect under wine and I tell you it gives me a screenload of errors about missing libraries.  My guess is that it sees the DLLs addressed in drive F:, which does not exist in the eyes of wine.

Now, on to my actual question:

**_How do I edit Wordperfect file (.wpd) in my ntfs partitions?_**

What does _not_ work so far:
[LIST]
[*]I have already ruled out wine->wpwin9.exe, as explained above.
[*]I have successfully opened the .wpd file with OpenOffice Writer but it has no option to write back a .wpd file.
[/LIST]

Supplementary questions: 
[LIST]
[*]Is there an add-on to OpenOffice to process .wpd files?
[*]Is there a free version of Wordperfect-9 (or higher) for Ubuntu?
[*]*Sheesh!* Can't this guy ask a simple single question in his posts? :grin:
[/LIST]
Thanks much!

BTW, I have plenty of questions about wine but I will take up those in another thread.

---

