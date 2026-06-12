---
title: "getting started with fail2ban"
date: 2012-09-14
forum: General Help
---

### Post by hwttdz on 2012-09-14
I was looking at my auth.log and didn't feel good about the number of breakin attempts so I've decided to set up fail2ban.  So I'm sort of fiddling around with multiple terminal windows, I'm watching
1) auth.log
2) fail2ban.log
3) I've ssh-d to another server which I'm going to get banned

So I intentionally typed in the incorrect password for my user a few times (I think I'm going to revise the number of incorrect attempts downwards given that I use ssh keys most of the time anyways).  And I saw in fail2ban.log

2012-09-14 11:53:28,379 fail2ban.actions: WARNING [ssh] Ban ip_from_which_I'm_attacking_my_own_system

And then to test I've tried to log in from the remote host again, and it just port times out.  I'm not sure what behavior I want there, or even if I can change it.  Would it not be better to just reject the login attempt immediately?

Anything else I should know about setting up fail2ban?

---

