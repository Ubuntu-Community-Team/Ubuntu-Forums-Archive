---
title: "Empathy can't connect on Windows Live network"
date: 2012-05-25
forum: General Help
---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-05-25
I can't connect to my Windows Live chat account through Empathy. I keep getting an error message: "Disconnected: Network error". I've been having this problem for quite some time now. It wasn't bothering me much, so I wasn't trying to fix it. But now it got annoying. Any fixes available?

---

### Post by Haneef Mubarak on 2012-05-25
Could you give a bit more info? Have you tried restarting your system and/or your router/modem/network switch?

Some info that would help:

[LIST]
[*]What have you already tried?
[*]What is your network configuration (default/static/custom)?
[*]Can you connect to any other chat services?
[*]Anything else that you would like to add?
[/LIST]

The more detailed you are, the easier it is for the rest of us to help you, and that means your question would likely be answered sooner.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-05-25
Haneef thanks for your reply. As I mentioned, this problem has been around for months already. So yes, I did restart my computer about a few hundred times, as well as my network router :) This problem was a known bug during 12.04 development, and has been fixed at one point in past. But for some reason unknown to me, it got back on my computer and now I can't seem to fix it the way I could before. There is a post somewhere in this forum about this problem and is marked [SOLVED] by an update. For me it's not working although I have all the current updates installed.

Yes, all the other services work fine - Google Talk, Facebook. I'm not sure if I could add any other information.

---

### Post by Haneef Mubarak on 2012-05-25
Excellent. I may have a solution for you, but you might not like it.

Try it anyways. 

Uninstall Empathy.

Reinstall Empathy and try again.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-05-25
I did it just now, and unfortunately it didn't help. I'm still getting the same error message. Maybe I didn't do it the right way? Should I restart my computer between uninstalling and reinstalling Empathy? Should I also uninstall and reinstall empathy-common and nautilus-sendto-empathy ?

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-05-25
Okay, I've uninstalled empathy, empathy-common and nautilus-sendto-empathy. I also uninstalled another library related to Empathy, but I can't remember its name. Then I restarted my computer and reinstalled those four. Now I can't connect to any account at all! I get a message "Authentication failed" for every account I try to use, although I'm absolutely sure that authentication parametres are set right. What happened?

---

### Post by Haneef Mubarak on 2012-05-27
Check if your system time/date is correct. Most authentication mechanism will fail if the time/data between your computer and official time/dates are off by more than 12-24 hours.

---

### Post by derklempner on 2012-05-28
Two things:

1)Empathy is weird concerning Windows Live Messenger accounts and passwords.  If your password is more than 16 characters long, try typing just the first 16 characters of it.  It might do the trick.

2) If the above doesn't work, try the steps mentioned here:
_[COLOR="Red"][http://askubuntu.com/questions/76948/problems-connecting-msn-with-empathy](http://askubuntu.com/questions/76948/problems-connecting-msn-with-empathy)[/COLOR]_

---

### Post by na5h on 2012-05-28
> **derklempner said:**
> Two things:

1)Empathy is weird concerning Windows Live Messenger accounts and passwords.  If your password is more than 16 characters long...
I can confirm this. It also applies for the default email application on my Android phone. Using a shorter password should do the trick.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-06-05
Ah man, after several weeks of trying to solve my problem, Empathy looks to me as a very unstable piece of software. Since I posted this, I've encountered a whole array of problems with it, without even changing anything in its settings! Every single time I start Empathy, I get a different problem! Since it is set on my system to power up on logon, I haven't noticed it before, but now if I close and reopen it, a new error will occur every single time. Sometimes it just won't login to the Windows Live network, others it will return my deleted accounts (?!?!) and refuse to log in to them at that, some other times it will report that I don't have any accounts set up, and then refuse to open my accounts settings! And all this is happening only with closing and reopening Empathy, without changing anything else.

Pretty disappointing :(

---

