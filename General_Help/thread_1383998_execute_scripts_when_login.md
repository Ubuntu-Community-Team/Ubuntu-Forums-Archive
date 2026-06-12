---
title: "execute scripts when login"
date: 2010-01-17
forum: General Help
---

### Post by tanveer on 2010-01-17
Hi all,

What I want to achieve here with your help is I have installed rkhunter, unhide and chkrootkit and which I want to execute through a script. Now what I want is after successful login and starting all startup applications it will launch a terminal and run the script there.

Should I just put the script in ~/.bash_profile for the user? 

Thanks in advance.

---

### Post by Monicker on 2010-01-19
That sounds like an odd way to run rkhunter.  A better method would be to just have cron job run it periodically.

You could look into using .bash_login or the sessions options in the gui.  I still feel either would not be an optimal method for running rkhunter.

---

