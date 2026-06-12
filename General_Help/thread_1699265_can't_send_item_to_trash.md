---
title: "can't send item to trash"
date: 2011-03-03
forum: General Help
---

### Post by adasilva on 2011-03-03
Hi everyone. I saw that many people have had this problem before but I still can't figure out what's going on. When I attempt to delete a file using Dolphin, it says "The trash has reached its maximum size! Cleanup the trash manually." But next I have 2 problems:

1. When I right click on the Trash icon in the left panel of the dolphin window, the "Empty Trash" option is light gray and cannot be selected.

2. I opened a terminal, changed directory to ~/.local/share/Trash/files and deleted everything there. But I still can't add new files to trash. So I opened a new terminal as su (gksudo /usr/bin/x-terminal-emulator) and checked the trash of other users, which was also not full. Then I looked for the root trash, but couldn't find it:
```

# cd /root/.local/share/
# ls -al
total 12
drwx------ 3 root root 4096 2010-10-24 20:31 .
drwx------ 3 root root 4096 2010-10-24 20:31 ..
drwx------ 3 root root 4096 2010-10-24 20:31 webkit

```

I don't know if this matters, but I was using gnome until I recently installed kde.

---

### Post by dwitkin on 2011-03-22
I'm having a similar issue. It appears to have to do with Dolphin. When I run Nautilus, I can delete a given folder but when I try to do it via Dolphin, I get the "The trash has reached its maximum size! Cleanup the trash manually." error.

I've followed tutorials on the Ubuntu site to make sure all of the trash cans are empty (root, my user, etc.) but to no avail. I also looked in Dolphin config (Dolphin Settings -> Configure Dolphin -> Trash) and my max trash size is 5 GB. Feels like a bug.

---

### Post by dwitkin on 2011-03-23
Minor update: I've come up with a workaround. Go to Dolphin Config (Dolphin Settings -> Configure Dolphin -> Trash) and set the When Limit Reached field to "delete biggest files from trash". This workaround still suggests Dolphin believes there is trash somewhere that hasn't been deleted, but I can't find it...


> **dwitkin said:**
> I'm having a similar issue. It appears to have to do with Dolphin. When I run Nautilus, I can delete a given folder but when I try to do it via Dolphin, I get the "The trash has reached its maximum size! Cleanup the trash manually." error.

I've followed tutorials on the Ubuntu site to make sure all of the trash cans are empty (root, my user, etc.) but to no avail. I also looked in Dolphin config (Dolphin Settings -> Configure Dolphin -> Trash) and my max trash size is 5 GB. Feels like a bug.

---

### Post by SeijiSensei on 2011-03-23
> **adasilva said:**
> I don't know if this matters, but I was using gnome until I recently installed kde.

I wonder if this might be the problem.  Did you install Kubuntu, or did you install KDE on top of GNOME by installing kubuntu-desktop?  Try creating a new user and see if that account has the same problems.  If not, there's probably some funky interaction between the two desktop environments that's hiding in dot-files in your primary user account.

I've used native installations of Kubuntu since 8.04, and I've not encountered your problem.

---

### Post by adasilva on 2011-03-30
"Did you install Kubuntu, or did you install KDE on top of GNOME by installing kubuntu-desktop?"

Yes, I did install KDE on top of gnome. I will try to make a new user and see if that helps. I won't get a chance to mess around until the weekend, but wanted to say thanks for the replies!

---

### Post by kio_http on 2011-04-02
Which version of KDE are you running?

---

### Post by velayo on 2012-04-14
I have the same problem.  Running ubuntu, installe kubuntu files over the ubuntu 12.04 installation.  Can't seem to find the where the files are.

---

### Post by ferd on 2012-10-16
I found this today in the Digikam - KDE UserBase Wiki. 

"The trash has reached its maximum size!  Cleanup the trash manually"

If you receive this error message and emptying the Trash doesn’t help, then the following command may solve the problem:

rm ~/.local/share/Trash/metadata

It worked for me and the trashcan is filling and emptying as it should.

---

