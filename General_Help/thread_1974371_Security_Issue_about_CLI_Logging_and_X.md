---
title: "Security Issue about CLI Logging and X"
date: 2012-05-06
forum: General Help
---

### Post by L3ct3rIII on 2012-05-06
Hello everyone.

I'm having some trouble here and hope someone can help me. 

The Ubuntu version I'm running is the Lucid Lynx, on a computer I share with two more people here. We all rather to use CLI instead of GUI (Gnome) most of time, so we've configured the computer to start on text mode already, and we want to let it this way.

Sometimes I have use GUI to download and edit videos. So I turn on the computer, on text mode, and issue a *startx* command. Since some of these videos are large, I start the download, block the account and get out. Now, here's my problem: Even blocking the account, the X process keeps running on that first CLI shell, tty1, the one that starts after boot and _stays logged on my user account_. This means anyone here that uses CTRL + ALT + F1 to get to that shell and then a simple CTRL + C will have access to my account, my docs etc.

I tried to start X and then go back to tty1 to log out, but doing this finishes X interface (and my downloads) as well.

Can someone tell me how can I change this? I don't know, maybe some way of starting X without letting my account logged on; or blocking that particular shell interface?

Thank you all for the attention.

So long.

P.S.: I've posted this on "General" because I believe that my problem is more related to configurations, CLI and X than to security itself. "All variants" because I believe this question applies not only to Ubuntu itself, and can be helpful to users from other distros too. Hope I have posted it right and on the right place.

[SIZE=2]**EDIT:**[/SIZE] Two days trying, searching and asking and I've made it. I only have to log in and use the following code:

```
sudo /etc/init.d/gdm start
```

This starts the graphical interface on the login screen, unattached to tty1.

So long.

---

