---
title: "Changing primary username and usergroup results in error in login?"
date: 2011-12-28
forum: General Help
---

### Post by Deathshiver on 2011-12-28
I began with Linux (Fedora) a few months ago and just installed Ubuntu on my laptop the other day. Like a new user, I named my primary user account after the computer name so it comes out as something like mypc@Mypc. I've already gone through recovery mode, remounted the disk as read/write, and modded the username and groupname to reflect what I would like the username to be by running the following commands:

```
mount -o remount,rw /
usermod -l Myusername -m -d /home/MyUsername mypc
groupmod -n Myusername mypc
```

The commands ran without issue, but after rebooting I found I was unable to log in. I could see the login screen and my real name and type my password. After hitting return, a black screen with text would appear momentarily, but disappear too fast for me to read the text in it. When it vanished I would be back at the login screen as though I had not typed my password yet.

I've managed to fix the issue by renaming both the username and groupname back to the way they were. This leads me to believe that the names definitely influence the issue.

I have two questions for more experienced Linux/Ubuntu users. First, why does renaming the primary user and group cause me to be unable to log in? Second, how can I get more time to see the black screen (Which I presume has the error text I need to read) or how can I change the user and group name without causing an issue?

Thanks.

---

### Post by Deathshiver on 2011-12-29
Bump, I could really use some help.

---

