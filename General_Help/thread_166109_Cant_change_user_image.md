---
title: "Cant change user image"
date: 2006-04-25
forum: General Help
---

### Post by TheIdiotThatIsMe on 2006-04-25
I have a weird problem with not being able to change my user image for KDE. I click on the menu, go to settings, security and privacy, then users, and I try to change the image and I get an error message stating that "Your administrator has disabled changing your user image". So I figured, okay, I'll root to that and try and change it. So I did a sudo kcontrol in the terminal, navigate back, and it gives me the same error if I try to change the root's picture (who I thought WAS the administrator), and I cant find an option to let me change the permissions. Any ideas?

---

### Post by gingermark on 2006-04-25
It might be that graphical login for root is disabled by default, and the picture is related to a graphical login. (Can you tell I'm guessing :))
However, using Kubuntu System Settings it works for me.

Try System Settings --> User Account and see if you can change the picture there.

EDIT: It works for me with kcontrol too, so I don't know what to say. I'm running KDE 3.5.2 - which version are you running?

---

### Post by TheIdiotThatIsMe on 2006-04-25
I am using 3.5.1 and unfortunately I dont think I have the Kubuntu settings as I downloaded regular KDE instead of the Kubuntu-Desktop (I use an SVN version of Amarok instead of a repo version, and the Kubuntu-Desktop required downloading their Amarok). Unfortunately I seem to have the latest KDE as in the repo?

---

### Post by TheIdiotThatIsMe on 2006-04-25
I downloaded the kde-systemsettings so I'd have the same as Kubuntu's from the repos. Unfortunately I still get the same error about the administrator has disabled changing user images.

---

### Post by TheIdiotThatIsMe on 2006-04-26
I also updated to KDE 3.5.2 and I still get the exact same error ](*,)

---

### Post by ash211 on 2006-04-29
I also get this error with both my user and root.  My Kubuntu history has been a clean install of 5.10, followed by a dist-upgrade to 3.5.1 and then another to 3.5.2

---

### Post by hermesrules on 2006-04-30
I've been having the same trouble with all versions of kubuntu since hoary, and can confirm the issue. I was hoping to find a solution and came upon this threat.

If anyone knows how to solve this, please let us know!

Thanx!

---

### Post by richbarna on 2006-04-30
I don't normally go for the pretty stuff but I saw your thread and decided to give it a go.

I changed mine with System Settings -- Login Manager --  Administrator Mode -- Click Users Tab -- Check User Name -- User Image Source = User, Admin.
Changed it to the scream logo, seems to work ok

---

### Post by hermesrules on 2006-04-30
[QUOTE=richbarna]I don't normally go for the pretty stuff but I saw your thread and decided to give it a go.

I changed mine with System Settings -- Login Manager --  Administrator Mode -- Click Users Tab -- Check User Name -- User Image Source = User, Admin.
Changed it to the scream logo, seems to work ok[/QUOTE]

THANKS! This did the trick!

---

