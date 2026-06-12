---
title: "login screen users order"
date: 2009-12-29
forum: General Help
---

### Post by toineurlings on 2009-12-29
How do I change the order of the users in the log-in screen? Because I want to set myself at the top so I only have to push enter for logging in.

---

### Post by toineurlings on 2009-12-31
does nobody knows?:-s

---

### Post by john newbuntu on 2009-12-31
I have never tried this.  But edit the /etc/gdm/custom.conf file.  Set AutomaticLogin to your name and AutomaticLoginEnable=false
[http://projects.gnome.org/gdm/docs/2.14/configuration.html](http://projects.gnome.org/gdm/docs/2.14/configuration.html)
Do this at your own risk.

---

### Post by toineurlings on 2009-12-31
Anyone tried this allready?

---

### Post by balta on 2011-04-09
Hi there!
I know the thread is more than one year old but I have the same issue and the file does not help (ubuntu 10.10 x64)
Here's the file's content:
```
[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=false
TimedLogin=balta
AutomaticLogin=balta
TimedLoginDelay=30
DefaultSession=gnome
```
*balta* being my account name which is not the one selected by default, even though it was the first one to be created and is alphabetically the first...
Even stranger is the fact that I used to be the first, then, one day, with any apparent reason, got to second, and last, place.
Any help would be greatly appreciated.
Thanks!


EDIT: Well it seems that [here]("http://askubuntu.com/questions/5218/where-is-the-order-of-names-in-gdm-login-screen-stored") and [here]("http://askubuntu.com/questions/4324/how-can-i-change-the-order-of-the-users-in-the-login-screen") the question has already been asked and (un)solved.
If anyone has a solution for this it will still be greatly appreciated!
Thanks.

---

### Post by IvarSnaaijer on 2011-07-13
I found something here

[http://library.gnome.org/admin/gdm/stable/configuration.html.en#greetersection](http://library.gnome.org/admin/gdm/stable/configuration.html.en#greetersection)

I added the following to the file /etc/gdm/custom.conf 

[greeter]
Include=Ivar

But I probably need to restart gdm and that is not an option now.

---

### Post by ZOMGxuan on 2011-10-01
I looked through the askubuntu questions that balta linked to, tried to follow some of their advice.

Apparently, the login screen orders users based on how frequently they login, with the most frequent being on top.

Strangely, it seems like this only counts if you login in manually by typing in your username, rather than clicking your name. After you do this several times, your name should appear at the top of the login list.

---

