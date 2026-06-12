---
title: "Maildir permissions issues"
date: 2009-06-29
forum: General Help
---

### Post by Icky_Ev on 2009-06-29
I'm sure this has an easy answer. ;) I've googled it and seen people have similar problems, but none of the fixes worked (or made sense) 

Background: running PostFix/Maildir on private LAN, no internet connection, no SALS or authentication of any kind, just straight passing notes. Working great EXCEPT I can't email anyone other then myself. 

Dreaded mailer daemon beast kicks this at me:

"maildir delivery failed: create maildir file /blah/blah/blah ect ect
PERMISSION DENIED"

I'm guessing I need to give MailDir permission (chown? yes? No? Maybe) to write wherever it dang well pleases. 

I tried chmoding a test user file and it was only an on-and-of fix and not one I care to use anyway. 

There has to be a way to set up MailDir to have write privs... right? Gotta be. >_> 

Help? :KS

---

### Post by baseface on 2009-06-29
read the chmod man page.

---

### Post by Icky_Ev on 2009-06-29
> **baseface said:**
> read the chmod man page.

That was my first thought. The man pages generally make no sense to me whatsoever and man chmod is no exception. 

Is chmod really applicable considering I'm trying to raise the permissions (I think....) of an app and not the directories it's trying to write to?

---

### Post by baseface on 2009-06-30
jesus christ.
[http://www.google.com/search?hl=en&q=how+to+read+man+pages&aq=f&oq=&aqi=g1](http://www.google.com/search?hl=en&q=how+to+read+man+pages&aq=f&oq=&aqi=g1)

---

### Post by Icky_Ev on 2009-06-30
> **baseface said:**
> jesus christ.
[http://www.google.com/search?hl=en&q=how+to+read+man+pages&aq=f&oq=&aqi=g1](http://www.google.com/search?hl=en&q=how+to+read+man+pages&aq=f&oq=&aqi=g1)

I'm not sure what the attitude is for. You assume I haven't already tried to educate myself on how to read man page. I'm sure some users find the man pages very helpful. For myself they may as well be written in sanskrit. 

Previously my experience with people on this forum has been very positive. But I knew it was a matter of time before I ran into my first "lrn2play newb" jerk. I'm almost reassured now that I haven't wandered into some internet paradise that upset everything I thought I knew. 

As it stands after much tinkering I was able to construct an inelegant solution to what is apparently a common but not-widely-addressed-for-ubuntu-problem. I don't like the solution but it'll suit for the interim.

---

