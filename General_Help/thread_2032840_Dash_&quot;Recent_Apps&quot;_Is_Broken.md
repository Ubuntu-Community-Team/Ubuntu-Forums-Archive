---
title: "Dash &quot;Recent Apps&quot; Is Broken"
date: 2012-07-24
forum: General Help
---

### Post by JosephBeck on 2012-07-24
I saw this issue long ago and I have no idea if it was ever fixed but ever since getting Ubuntu 12.04 when I open the dash the first thing you see is Recent Apps and it never changes. It only ever shows Ubuntu Software Center and Help even when I haven't used them in a month and have used many other applications that should show up. I don't know why it is broken and it is not a huge deal but I'd like it to operate how it was meant to operate. 

Any solutions other than reinstalling Ubuntu 12.04 because I believe I've done that with no help and it is a time consuming process to transfer my files and what not (Im not paying to have Ubuntu One storage increased when I never use it).

---

### Post by JosephBeck on 2012-07-25
BUMP.....Any help would be nice. I know other people have had this issue in the past.

---

### Post by JosephBeck on 2012-07-26
...

---

### Post by philinux on 2012-07-26
I would try a unity reset from a terminal.

```
unity --reset
```

Be aware this will loose you any customisations you've made.

---

### Post by JosephBeck on 2012-07-26
> **philinux said:**
> I would try a unity reset from a terminal.

```
unity --reset
```

Be aware this will loose you any customisations you've made.

Have done it before and just did it now, no help sadly.

---

### Post by arpanaut on 2012-07-26
I'm not sure if this is your problem, but in 12.04 if you have a program locked to the launcher it will not appear in the Dash's "Recent Apps". 
This is by design, I'm not sure if there is a work-arround?
I believe this was done to "reduce redundancy"

---

### Post by JosephBeck on 2012-07-27
> **arpanaut said:**
> I'm not sure if this is your problem, but in 12.04 if you have a program locked to the launcher it will not appear in the Dash's "Recent Apps". 
This is by design, I'm not sure if there is a work-arround?
I believe this was done to "reduce redundancy"

That is not it, I've used a large amount of apps that aren't locked and they dont show up. Since install it has only showed those two in recent apps.

---

### Post by andygmorris on 2012-09-04
> **arpanaut said:**
> I'm not sure if this is your problem, but in 12.04 if you have a program locked to the launcher it will not appear in the Dash's "Recent Apps". 
This is by design, I'm not sure if there is a work-arround?
I believe this was done to "reduce redundancy"

Ah haaa... I believe this post answers my question at :-
[http://ubuntuforums.org/showthread.php?t=2052441](http://ubuntuforums.org/showthread.php?t=2052441)

I have found that the Recent Apps indeed is stifled by the 'as designed' comment.

Even to the point where the apps I expect to see aren't in the Recent Apps as I've just opened them, and they're still shown in the side bar.

I've just tested it by removing the Apps which I 'pinned' to the side bar... run them from the Dash, then close the app, then go to the Dash and hey presto, they're shown in Recent Apps.

Would ya believe it...

So effectively, if the App is in the dash (pinned or even just active) it seems not to be shown in the Recent Apps.

I'll post these details on my original post too.
For sure, they'll be of help to someone.

---

### Post by Gazbuntu on 2012-10-02
I didn't have any apps showing in the dash, and I cured that by removing recently-used.xbel in .local/share  

Might be worth a try for your problem.

cd ~/.local/share
rm recently-used.xbel

Can't remember if I had to log out or reboot to get it working.

Have fun

[www.TheBroadbandEngineer.co.uk](www.TheBroadbandEngineer.co.uk)

---

