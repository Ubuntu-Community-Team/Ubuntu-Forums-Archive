---
title: "cant login to hotmail"
date: 2010-02-19
forum: General Help
---

### Post by sdowney717 on 2010-02-19
[http://co119w.col119.mail.live.com/default.aspx?wa=wsignin1.0](http://co119w.col119.mail.live.com/default.aspx?wa=wsignin1.0)

just get this line when logging in with a blank page.

However, I can login using opera browser, and I can login using Firefox to a different hotmail account.
It is very strange. I cleared out the browser cache and installed firefox 3.6

This is for my fatherinlaw's PC.
I just tried his account on my PC and I can login, so something is funny with his machine.
Is there another way of resetting firefox to give it a clean slate?

---

### Post by lovinglinux on 2010-02-19
Start Firefox profile manager with this command:

```
firefox -P
```

Then create a new profile and test it.

---

### Post by sdowney717 on 2010-02-20
[http://tips.webdesign10.com/how-to-use-firefox-profiles](http://tips.webdesign10.com/how-to-use-firefox-profiles)
says to use this instead
firefox -a asdf &

apparently the -P option just opens a new window
I will give it a try and see

I just tried "firefox -a asdf &" on mine and all it does is reopen firefox with the last tabs.

CAN I simply delete .mozilla directory in his home folder?? What about favorites?

---

### Post by sdowney717 on 2010-02-20
[http://gaarai.com/2009/02/23/multiple-firefox-profiles-in-ubuntu/](http://gaarai.com/2009/02/23/multiple-firefox-profiles-in-ubuntu/)

firefox -no-remote -P

this finally works and brings up profile manager

---

### Post by lovinglinux on 2010-02-20
> **sdowney717 said:**
> apparently the -P option just opens a new window
I will give it a try and see

The -P option opens a new window because Firefox is still running. Did you close Firefox before using this command? If yes, then go to System Monitor and kill any firefox process or use the command below:

```
firefox -P -no-remote
```

> **sdowney717 said:**
> [http://tips.webdesign10.com/how-to-use-firefox-profiles](http://tips.webdesign10.com/how-to-use-firefox-profiles)
says to use this instead
firefox -a asdf &

I don't know that command. I will investigate it.

---

### Post by sdowney717 on 2010-02-21
It is working with a new profile. So what happened to the old profile?

What is the way to export and import bookmarks?

---

### Post by lovinglinux on 2010-02-21
> **sdowney717 said:**
> It is working with a new profile. So what happened to the old profile?

Hard to know. Could be a file corruption, sub-optimal settings or an extension causing the problem.

> **sdowney717 said:**
> What is the way to export and import bookmarks?

Third paragraph [here](http://lovinglinux.megabyet.net/?page_id=220#Backups-1). Alternatively, you could simply copy the file *places.sqlite* from one profile to the other.

---

