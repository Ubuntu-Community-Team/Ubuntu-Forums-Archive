---
title: "how to get new KDE?"
date: 2006-05-02
forum: General Help
---

### Post by topquarck on 2006-05-02
hi all; 
When I visited the kde website, I found the new kde 3.5.2 desktop. but I have a 3,4 version I installed from the ubuntu servers...

Pls if anybody can tell me how to install the newer version of KDE i will be very thankful

thanx alot

---

### Post by njf on 2006-05-02
See [http://kubuntu.org/announcements/kde-352.php](http://kubuntu.org/announcements/kde-352.php)
You only need to choose 1 of the mirrors.

---

### Post by barbarian on 2006-05-02
There is less then month til brand new Dapper release with shiny KDE 3.5.2, so I'd better wait.

---

### Post by gingermark on 2006-05-02
I would also add the 3.5 & 3.51 repositories - don't ask me why, it just seems to help avoid problems other people have had.

And do a dist-upgrade as opposed to a regular one ('sudo apt-get update' followed by 'sudo apt-get dist-upgrade')

---

### Post by crypticstatic on 2006-05-03
Is there anyway to upgrade to the latest version of KDE without doing a dist-upgrade?

I only want to update KDE and not the rest of the system.

---

### Post by uteck on 2006-05-03
[QUOTE=crypticstatic]Is there anyway to upgrade to the latest version of KDE without doing a dist-upgrade?

I only want to update KDE and not the rest of the system.[/QUOTE]
If you add the repository from the KDE site for Breezy doing a dist-upgrade will just ensure that all the KDE componets are upgraded.  Some 3.4 parts may need to be removed before the new ones can be installed, and just upgrading will not do that.

---

### Post by barbarian on 2006-05-03
[QUOTE=crypticstatic]Is there anyway to upgrade to the latest version of KDE without doing a dist-upgrade?

I only want to update KDE and not the rest of the system.[/QUOTE]

After adding external repositories you should do *apt-get dist-upgrade* anyway..

---

