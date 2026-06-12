---
title: "Startup Applications : Ibus-daemon"
date: 2012-04-27
forum: General Help
---

### Post by nobuus on 2012-04-27
Dear all,

I would like to setup Ibus-daemon as a startup applications for system wide in the ubuntu system.
I can use the Ibus as a system administrator user (super user), but I cannot use the Ibus as a guest user.  Whenever I use the Ibus as a guest user, I have to activate "Ibus" each login time.  Would you tell me how to automatic activate the Ibus for every users in the system?

Thank you for reading!

---

### Post by nobuus on 2012-05-02
More than 100 people read my question so far, but no one answered yet.

I used the startup application setting for ibus, like the administrator user, but it is vanished whenever the guest user logout and login, again.  Does some one know how to save the startup application setting for guest user / other users, and not administrators?

---

### Post by mcduck on 2012-05-02
The reason why the setting disappears when you log out of the guest account, is that the whole guest account gets deleted on logout, and is created again the next time.

What you can do, however, is change the default settings for newly created user accounts. As you might know, all the user settings are stored in hidden files inside the user's home directory. And anything inside /etc/skel is copied into newly created user's homes, so if you just know the relevant config file and copy it there, it will apply to all new users on the system.

The way I usually dop that is that I create a new temporary user account, then modify it as I'd want all new user's accounts & desktops to be, copy all config files from that user's home into /etc/skel and then remove the temporary account.

---

### Post by nobuus on 2012-05-05
Dear mcduck,
Thank you for your reply.
Where are "all config files" and what are those names?
I am a ubuntu beginner, so would you tell me more details if can?
Thank you so much!

---

### Post by alkor.41 on 2012-09-24
I'm not very clear about this: you should google to know what is /etc/skel and what are there in the folder, and how guest account works.

---

