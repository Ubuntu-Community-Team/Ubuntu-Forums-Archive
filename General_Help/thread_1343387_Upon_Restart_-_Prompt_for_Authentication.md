---
title: "Upon Restart - Prompt for Authentication"
date: 2009-12-01
forum: General Help
---

### Post by Buschbarber on 2009-12-01
I have been running Ubuntu for a couple of years and I recently installed Ubuntu 9.10. One of the annoying things that I now encounter at Restart is a message informing me that Multiple Users are Logged In and requiring me to enter my Password for Authentication. If I click on View, below the Password Prompt, a Blue Link appears with the words "org.freedesktop.consolekit-restart session multiple users" or something to that effect. If I click on this link, nothing happens. If I Cancel and do not type in my Password, I am Logged Off and taken to the Login Screen. If I type in the Password and hit Enter, the system Restarts.

This just started with 9.10 and was not present with 9.04 and earlier.

I am running Nvidia beta driver 195.22 if that has some relevance.

I did some Google searches on this topic but nothing has resolved the issue.

---

### Post by dcstar on 2009-12-01
> **Buschbarber said:**
> I have been running Ubuntu for a couple of years and I recently installed Ubuntu 9.10. One of the annoying things that I now encounter at Restart is a message informing me that Multiple Users are Logged In and requiring me to enter my Password for Authentication. If I click on View, below the Password Prompt, a Blue Link appears with the words "org.freedesktop.consolekit-restart session multiple users" or something to that effect. If I click on this link, nothing happens. If I Cancel and do not type in my Password, I am Logged Off and taken to the Login Screen. If I type in the Password and hit Enter, the system Restarts.

This just started with 9.10 and was not present with 9.04 and earlier.

I am running Nvidia beta driver 195.22 if that has some relevance.

I did some Google searches on this topic but nothing has resolved the issue.

[https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/282403](https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/282403)

---

### Post by Buschbarber on 2009-12-02
It is nice to know that the bug was known in early 2009, but it is Dec 2, 2009 and the problem still exists. Has there been any progress since 02/09 as far as what is causing the problem and some suggested fixes to the problem?

I made suggested edits to the org.freedesktop.consolekit.policy and that did nothing.

Just looking for some more recent suggestions.

It is no big deal to have to type in a Password, I suppose, as long as it is not a Security Risk.

---

### Post by mc4man on 2009-12-02
Actually that bug may not be what your referring to. Many of the previous authorizations that could be edited to be persistent are no longer readily available.

In this case you shouldn't be seeing the prompt unless there is another user(s) logged in.

In that regard requiring auth. to restart and /or shutdown makes sense. If this is the case here, the best solution would be to have other users log out instead of switching users.

It is however still possible to set persistent authorizations as previously as long as done judiciously and with some of them, certain limitations.

The hope though would be that a means to adjust will be returned in some form.

In this case what are you looking for?, and is this a situation as I just described?

I'd think the best setting here would be " auth_admin_keep_always ", only the admin could restart with others logged in without entering the admin password

---

### Post by Buschbarber on 2009-12-02
> **mc4man said:**
> Actually that bug may not be what your referring to. Many of the previous authorizations that could be edited to be persistent are no longer readily available.

In this case you shouldn't be seeing the prompt unless there is another user(s) logged in.

In that regard requiring auth. to restart and /or shutdown makes sense. If this is the case here, the best solution would be to have other users log out instead of switching users.

It is however still possible to set persistent authorizations as previously as long as done judiciously and with some of them, certain limitations.

The hope though would be that a means to adjust will be returned in some form.

In this case what are you looking for?, and is this a situation as I just described?

I'd think the best setting here would be " auth_admin_keep_always ", only the admin could restart with others logged in without entering the admin password

This is my personal PC and no one else has access to it. There is only one Physical user and that is me. I was advised by an IT friend that there could be two X sessions going concurrently and that could account for multiple users. I am not adept enough to know if that could be the possible cause.

What I am looking for is the reason why I am getting this Prompt and if it is unnecessary, how to get rid of it.

---

