---
title: "Where is the login screen application"
date: 2012-08-28
forum: General Help
---

### Post by MrC11 on 2012-08-28
Hello guys,

I installed ubuntu 12.04 but, I want to run it in kiosk mode.
My problem is where is the "Login screen" application. I need this one.

Can someone tell that to me?

Greetz,

MrC

---

### Post by MrC11 on 2012-08-28
This is a little screen of the application I need.

[IMG]http://cdn.instructables.com/F5K/GYD7/GB4CYISP/F5KGYD7GB4CYISP.MEDIUM.jpg[/IMG]

---

### Post by MG&amp;TL on 2012-08-28
That doesn't really exist anymore, probably because we have a new login manager.

What exactly do you want to do with it?

---

### Post by MrC11 on 2012-08-28
Log in as restricted user. And selecting Kiosk Mode as the default session.

---

### Post by MG&amp;TL on 2012-08-28
> **MrC11 said:**
> Log in as restricted user. And selecting Kiosk Mode as the default session.

I don't know what Kiosk mode is, or if it still exists, sorry. However, if you want to change the default session, see: [http://askubuntu.com/questions/62833/how-do-i-change-the-default-session-for-when-using-auto-logins](http://askubuntu.com/questions/62833/how-do-i-change-the-default-session-for-when-using-auto-logins)

For a restricted user, just make one in users and groups, with or without a password. If you want to hide other account's presence from the login screen, see: [http://askubuntu.com/questions/92349/how-do-i-hide-a-particular-user-from-the-lightdm-login-screen](http://askubuntu.com/questions/92349/how-do-i-hide-a-particular-user-from-the-lightdm-login-screen)

Sorry about the linkage, but sometimes it's easier.

---

### Post by MrC11 on 2012-08-28
I am a rookie with ubuntu. Don't know that code xD

---

### Post by MG&amp;TL on 2012-08-28
> **MrC11 said:**
> I am a rookie with ubuntu. Don't know that code xD

Which code?

---

### Post by MrC11 on 2012-08-28
Look this is what I also need:

[IMG]http://www.instructables.com/file/FNZBFRWGB4CYISM/imagenotes.jpg?size=medium[/IMG]

That you got 2 seconds too chose between the accounts. And then changing to the kiosk session.

ps. This is kiosk mode [I follow this tutorial]

[http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/?ALLSTEPS](http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/?ALLSTEPS)

---

### Post by MG&amp;TL on 2012-08-28
Right...okay, once you've done the kiosk mode as shown in your guide (The X session is especially important), you can do the following:

1. Press Alt-F2 and type: 

```
gksu gedit /etc/lightdm/lightdm.conf
```

2. In the window that comes up, replace the text already there with this text (copy/paste):

```

[SeatDefaults]
autologin-user=Scholar
autologin-user-timeout=2
user-session=Kiosk
greeter-session=unity-greeter
```

3. Save and quit.

This should do what you want. Although lightdm is quite new, so there's really no telling what it could do.

---

