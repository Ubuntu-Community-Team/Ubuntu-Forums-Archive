---
title: "gwibber problems"
date: 2010-05-07
forum: General Help
---

### Post by bashphoenux on 2010-05-07
In one of the threads I learnt that deleting the keyrings and setting the password to blank will help me escape the password pop up for the social broadcaster and so I did the same,
now a new problem, every time I refresh the timeline the "Broadcast Accounts" (preferences) appears not one but 3 and this keeps pilling up as the update continues every 10 minutes, ITS REALLY IRRITATING that every time I refresh the timeline 3 windows appear and I have to close all of them pls look into it as soon as possible.
And on another note: I posted a thread on it but I didn't seem to get a single response...
in GWIBBER it doesn't show the MAIN TIMELINE FOR MY IDENTI.CA account. it just shows me the replies that people have posted to my status update....
if it is possible get a new social broadcast client for Ubuntu GWIBBER certainly doesn't appeal not at its current form.
Thanks sorry for the caps here and there it is to emphasize how frustrated I am !

---

### Post by dino99 on 2010-05-07
sudo dpkg-reconfigure gwibber
sudo dpkg-reconfigure gwibber-service

sudo apt-get update 
sudo apt-get install -f

---

### Post by bashphoenux on 2010-05-07
I would love to know what the first 2 commands do ?
and the third command I got this:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
install: invalid option -- 'f'
Try `install --help' for more information.

---

### Post by dino99 on 2010-05-07
no spoon feeding on my end  :lolflag:

---

### Post by bashphoenux on 2010-05-07
ok after doing those 4 commands Gwibber isn't opening any more :O

---

### Post by wolferl on 2010-05-07
Hi. I'm new to Ubuntu (moved from Mandriva and OpenSuSE), so it's my 1st post here.
 
About Gwibber.....yesterday night I had my first problem with Lucid: gwibber could not add any account I tried to. It didn't hung, just simply did nothing after I wrote the user/pw and clicked 'add'. I tried with twitter and identi.ca with the same (no) result. Instead, although I do not have a flickr account, I made a try and apparently it worked. I even reinstalled gwibber...no changes. My netbook's gwibber works flawlessly instead.
 
Any idea?

---

### Post by bashphoenux on 2010-05-08
sorry mate I never faced such a problem,
try running gwibber from terminal and see if you get any error while clicking on the add button if so try posting it, some one can make sense of the error message

---

### Post by wolferl on 2010-05-08
Aha, now I know a little more about the problem: for some reason it has something to do with passwords!
Yesterday I tested GMail notifier and although I could add my email account (user+pw) whenever I close the session, open again and launch Gmail notifier, for some reason it does not keep my pw and I must reenter it again.
I suspect something like that happens to me with gwibber...that explains why it does not happen to me with Flickr (in gwibber)...because when adding flickr you do NOT need to enter a pw.
Anyway I still need to find a solution.
 
Ok. I edit here.
 
Problem solved. In the end it was not a problem of Gwibber but a problem with password management. My user was configured to be able to enter the session without a password > that deactivated the (normally) required process of saving the passwords, in short: the password daemon was not active and no pw was saved. As far as I have checked, it affected gwibber, gmail notifier and Ubuntu One service.
Maybe this can be useful for some other users. Any more ideas will be welcome.

---

