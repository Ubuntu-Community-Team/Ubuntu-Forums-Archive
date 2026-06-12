---
title: "Set motd to display update message only for admin"
date: 2010-05-18
forum: General Help
---

### Post by archknight on 2010-05-18
I am trying to make it so the updates part of the motd only display for users who are in the root group. I have been messing with the /etc/update-motd.d/90-updates-available file. I tried doing something like 
```

if id | grep 'groups=0(root)' >/dev/null; then echo "update stuff"; fi;

```
This line works fine at the terminal. However, I learned by experimentation that the motd message is created by root and so this doesn't help differentiate between the users. When I have it display the result of whoami, it always says root. Does anyone else have any suggestions? How can I get the message of the day to display info that is specific to the user logging in? If I can even get the motd to do something like "Hello, NAME" where the user name is inserted, I can work out the rest on my own.

---

### Post by archknight on 2010-05-19
I would appreciate any help I could get with this problem...

---

### Post by archknight on 2010-05-20
*bump*

---

### Post by archknight on 2010-05-20
Perhaps I should add that I am running 64bit Ubuntu 10.4 Lucid Lynx.

---

### Post by archknight on 2010-05-21
Can someone at least point me in the right direction?

---

### Post by archknight on 2010-05-22
bumping once again...

---

### Post by gmargo on 2010-05-22
The /etc/update-motd.d/90-updates-available file only tracks the updates.  As you know, it has nothing to do with when the message is displayed.  

The "motd" message display is controlled by /etc/pam.d/login (and /etc/pam.d/ssh for ssh logins).  See the pam.d(5) man page for the file format.  I don't see an obvious way to control the motd display based on user id.  (Personally I despise the message since IMO no eye candy should ever delay a root login.)

---

### Post by dcstar on 2010-05-22
> **archknight said:**
> Can someone at least point me in the right direction?

You can alter/add the motd scripts to do basically anything you like, a simple Google search would have found things like this:

[http://www.linuxjournal.com/content/tech-tip-periodically-update-your-motd-update-motd](http://www.linuxjournal.com/content/tech-tip-periodically-update-your-motd-update-motd)

---

### Post by archknight on 2010-05-23
Thank you so much, gmargo, for the information. I didn't even know pam.d existed and none of the searching I did about motd even mentioned it. This is exactly the right direction that was I was asking for. I am still not sure how to make it work but I got something to work with now.

dcstar, I appreciate you taking the time to reply. However, I have already done plenty of googling and even read the page you specifically linked. I am well aware how to display almost any information I want in the motd. If you had taken the time to carefully read and consider my original post, you would have realized that I was in fact asking how to get information on the person logging in when commands like "id" and "whoami" fail to work. That link does not provide any useful information in this regard. 

I admit that I am very green when it comes to Ubuntu and so I wish to show respect to someone with as many posts on these forums as you have. However, I do not appreciate it when someone ignores what I say and assumes that I didn't put in the least amount of effort before asking a question on the forums. Do you think there is someone who would frequently bump a thread over the course of several days instead of spending ten minutes using google? (though, it only took seconds to find that particular link) It is responses like yours that drive people away from the forums or make it so I won't post a question here until I have spent days going through documentation, searching online, looking through old forums posts, and experimenting with scripts before asking any question that an experienced user may be able to answer in an instant. I know you may think that easy questions like this may be a waste of your time, but from my perspective, I have wasted a far greater amount of time and have frustratingly made little to no progress.

I apologize if I sound ungrateful. I really do appreciate you taking the time to reply. I can't stand having no replies to a thread for days on end. I rather have a reply that isn't helpful than nothing. You and gmargo are right now my two favorite people on the forums for just saying something at all. In fact, it is because I am so appreciative that I want you to reflect on your actions and how they affect others. So, thank you for the response.

---

