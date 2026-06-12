---
title: "Big problem please read"
date: 2009-11-08
forum: General Help
---

### Post by BeingLostMayVary on 2009-11-08
Well the other day I updated to Kubuntu 9.10. As it happened I was messing with things today trying to get everything how I want it. Well I decided to change the login for my Kubuntu, so I went to the advanced tab and changed the user name the UID or something like that. I changed it to something that had forward slash in it at the beginning like /me. Well Kubuntu didn't like that too much after i restarted tried the new login gave me a weird error saying around can't get back to home. Well if anyone knows how to fix this maybe through recovery please help me with my stupidity and ignorance. Please!!!

---

### Post by Gforce20 on 2009-11-08
> **BeingLostMayVary said:**
> Well Kubuntu didn't like that too much after i restarted tried the new login gave me a weird error saying around can't get back to home.
Can you give the exact error message?

---

### Post by BeingLostMayVary on 2009-11-08
> **Gforce20 said:**
> Can you give the exact error message?

Yup let me boot my Kubuntu and I'll write it down.

---

### Post by BeingLostMayVary on 2009-11-08
Ok when I first boot up it gives me a prompt for my computer(world) password with ttyl above it. Heres the error it gives me though when I try to log in : 

Cannot enter home directory using /.

(then afterwards it gives me this)

xsession: warming: unable to symlink "xmp/xession-//me" to "tmp/fileN5u53"; look for session log/errors in "/tmp/xsession-//me".


Thats the end I hit okay on it and it just stays at the new karmic background with nothing else. Hope that helps.

---

### Post by BeingLostMayVary on 2009-11-09
Guessing you haven't come across this problem very often. Might there be a way to change the name of my username through recovery? That's my thought of how to fix it, but I'm not sure.

---

### Post by BeingLostMayVary on 2009-11-09
So any good ideas? I can see it if you don't want to help me because I did something foolish like this, but I'm a noob at linux still.

---

### Post by Gforce20 on 2009-11-09
Sorry, I was away from my computer and only just now got back to this thread. Here's just an idea: if GRUB gives you a "recovery mode" option, use that and enter a root prompt. Type "usermod -l newname oldname"; in this case "oldname" is "/me". See if that helps at all.

---

