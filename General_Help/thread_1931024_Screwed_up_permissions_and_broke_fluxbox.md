---
title: "Screwed up permissions and broke fluxbox"
date: 2012-02-24
forum: General Help
---

### Post by illmatik on 2012-02-24
Hi guys,

Ubuntu newbie trying to find my way around. I'm on Ubuntu Server 10.4.

I learned the hard way today that one mistake in a command while in sudo can be costly

I meant to run this command:

sudo chown -R justin ./*

But what I actually ran was

sudo chown -R justin /* 

I caught my mistake fairly quick and ctrl + C'd but the damage was already done. After a few hours of manually repairing permissions, I'm left with one thing that still seems to be broke: Fluxbox

This is a remote server, so I VNC in and use Fluxbox occassionally. Now when I VNC in, I just get a purple background and fluxbox never launches. Obviously the problem is permissions are screwed up, but I don't know where exactly they need to be repaired. 

Here is my vnc4server log:
[http://pastebin.com/D9pMjHc5](http://pastebin.com/D9pMjHc5)

Any help would be appreciated. Thanks!

---

### Post by Paddy Landau on 2012-02-25
I'm not sure how to fix your problem, but I would:

[LIST=1]
[*]Purge fluxbox.```
sudo apt-get purge fluxbox
```
[*]Install fluxbox.```
sudo apt-get install fluxbox
```
[/LIST]
Try that and let us know if it worked.

---

### Post by illmatik on 2012-02-25
Thanks for the advice. I ended up figuring it out.

I repaired all the permissions in my home folder, but failed to fix the hidden folders/files. Running sudo chown -R justin /home/justin/ did the trick and fixed everything.

Lesson learned :)

---

### Post by Paddy Landau on 2012-02-26
Excellent!

To help others who may have the same problem, please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

