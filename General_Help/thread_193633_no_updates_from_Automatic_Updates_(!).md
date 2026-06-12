---
title: "no updates from Automatic Updates (!)"
date: 2006-06-10
forum: General Help
---

### Post by rpesq on 2006-06-10
Hi,

Original installed 64bit Dapper, had driver/app issues with it, so I installed 32bit dapper.  Running 32bit Dapper for several days.  I lalways keep a separate partition for /home.

Since 32bit dapper was installed, several days ago, I have not had *1* automatic update notice.  _None, zero_. 

So I manually launch the updater window today, and see quite a number of updates available.

Can anyone explain why the automatic updates are (apparently) not working, and how to get them to work again?  Thanks in advance.

---

### Post by Dr. Nick on 2006-06-10
Open system - prefrences - sessions then look at startup tab.

Do you see update-notifier listed?
If not try adding it and see if that helps.

---

### Post by rpesq on 2006-06-10
Hi,
Appreciate the reply, but I double-checked and that is already enabled.

---

### Post by blackjack6.21.91 on 2006-06-10
Open the update manager and see if you have any wierd preferences goin on.

---

### Post by rpesq on 2006-06-10
Hi,
Not sure what you mean....  I manually open the Update Manager, and I see a Window that says 20 updates are available, with a button for 'check' and 'Install Updates'.  No place to see any 'preferences'.

---

### Post by rpesq on 2006-06-10
I may have solved this.  I customized the gnome panels (got rid of the top panel, tried to add everything I wanted to the bottom panel...), and hence removed the 'notification area', and did not know that I needed to add that feature to the bottom panel.  So that is probably why I never saw an update notification.  I re-added that feature, so hopefully I will see the updates in the future(!)

---

### Post by Dr. Nick on 2006-06-10
[quote=rpesq]I may have solved this.  I customized the gnome panels (got rid of the top panel, tried to add everything I wanted to the bottom panel...), and hence removed the 'notification area', and did not know that I needed to add that feature to the bottom panel.  So that is probably why I never saw an update notification.  I re-added that feature, so hopefully I will see the updates in the future(!)[/quote]

 umm yeah thats probably it lol. You have to have the notifacation area for update manager to show up. Glad you figured that out as that had not crossed my mind.

---

