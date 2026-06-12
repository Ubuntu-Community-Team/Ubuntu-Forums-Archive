---
title: "Application wants access but"
date: 2011-07-09
forum: General Help
---

### Post by Bobrm2 on 2011-07-09
This "An Application wants access to the keyring "default", but it is locked. Goes on and I've a few question about the procedure.

   The first is how do I determine WHAT application wants access. Seems to me that I need to know what is going on with programs trying to log in.

  If I knew what program is needing access, I could determine if I wanted to provide permanent, temporary, or no access. 

   How can I determine what is happening at startup, (hmmmmm startup that's a clue).

   Help and your thoughts appreciated. Well, I went into startup /system/preferences/startup. Unchecked two items I thought might require a password, and that I didn't need, but it didn't help. I still have to enter the password twice in order to log in.

Bob R

---

### Post by ajgreeny on 2011-07-09
Do you have:-
1.  Autologin setup for your username?
2.  Wireless connection to network?

If you answer yes to both questions, go to the network manager icon in the panel, Edit Connections then highlight the connection on the wireless tab, and check that **Automatically connect**, and **Available for all users** are both selected.

If not, that is often the cause of the keyring password request appearing at login/bootup.

---

### Post by Bobrm2 on 2011-07-09
AJ,
  All are set as you told me, and were so prior to this morning. It's as if there is another program waiting to log in and needing a supplied password.

---

### Post by ajgreeny on 2011-07-09
Look in **/var/log/auth.log** to see if any clues show up there.

---

### Post by goldshirt9 on 2011-07-09
have just had this exact problem.
i stopped the wireless connection to connect automatically .
rebooted 
then connect to the internet and reset to automatically connect.
all fine now.

hope this helps.:D

---

