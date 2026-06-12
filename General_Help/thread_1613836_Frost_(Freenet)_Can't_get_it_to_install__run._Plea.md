---
title: "Frost (Freenet) Can't get it to install / run. Please Help, Pleassssse??"
date: 2010-11-04
forum: General Help
---

### Post by unone95 on 2010-11-04
I can't figure out how to install freenet's frost on my Ubuntu 10.10 install.

I extracted the zip to a folder and chmod +x'ed the frost.sh. Then I doubled clicked on the sh file. A java windows pops up and says Frost first startup and gives me a few choices. I pick Freenet 0.7 and click OK, The a Frost logo appears and at the bottom it says "Initializing Mainframe..."

It never gets past Initializing Mainframe..., I've let it run for hours but the program is just not starting.

On a side note I have freenet 0.7.5 up and running. Seems to be fine but when I go to [COLOR="Blue"]hxxp://127.0.0.1:8888/alerts/[/COLOR] I get the error:

"You are trying to run Freenet under a non-Sun Java: Sun Microsystems Inc. 1.6.0_20 (OpenJDK Client VM)"

Which is weird because I got the Java JRE 6 from the software center. I don't know if that is also what is going on with frost??

I'm not sure how to trouble shoot this, I looked for a frost forum but can't find any. I hope the Ubuntu community can help me out on this.

My armature guesses so far is that perhaps I have the wrong java runtime or maybe ubuntu 10.10 is too new? Ok, I have no idea... Please Help.

**EDIT:**

I just noticed I have OpenJDE Java installed instead of Sun. Could that be the problem? I uninstalled The OpenJDE Java and went to java.com.

Under the linux section they have a bin for download. I doubled clicked the bin but it said it didn't know what app to open it with.

There are instructions on the site but for the life of me I cannot figure them out. There are 2 linux downloads:

jre-6u22-linux-i586.bin
and
jre-6u22-linux-i586-rpm.bin

I'm not even sure which one I should be trying. And even if I knew which one was the right one, I can't figure out how to get theses bins installed.

**EDIT**

Can somebody please give me a tutorial on how to install sun java on a fresh ubuntu 10.10? I have been reading and searching and still having a terrible time.

**EDIT**

All problems solved (Thanks oldos2er). For anyone reading this, Switching from OpenJDE to Sun Java fixed the Frost issue.

---

### Post by Lubos on 2010-11-05
Install packages:
sun-java6-bin, sun-java6-jre
with all dependencies if Synaptic need them. It is in Multiverse repository (enable them in Synaptic settings and reload if necessary)
In installation process you will be MAYBE asked to accept license.

EDIT:
before that you can remove open java package
openjdk-6-jre

---

### Post by oldos2er on 2010-11-05
In 10.10 the sun-java6* packages are in the partner repository (which needs to be enabled).

---

### Post by unone95 on 2010-11-05
> **oldos2er said:**
> In 10.10 the sun-java6* packages are in the partner repository (which needs to be enabled).

Where is the partner repository? Is it in the Ubuntu software center and how do I enable it?

Thanks in Advance.

**EDIT**

I went to Ubuntu Software Center - > edit -> Software Sources

there are 5 tabs, but I can't find anything that says partner repository? I have Ubuntu 10.10 with all the updates.

Thanks

---

### Post by oldos2er on 2010-11-05
Open Synaptic Package Manager, click Settings, Repositories, Other software tab, tick both 'Canonical Partners' boxes.

---

### Post by unone95 on 2010-11-05
> **oldos2er said:**
> Open Synaptic Package Manager, click Settings, Repositories, Other software tab, tick both 'Canonical Partners' boxes.

**[COLOR="Red"]Thanks oldos2er[/COLOR]**! All problems are solved now. I'm about to mark this thread as solved but I have one more question.

Ok, here's what I did, I went to the Synaptic Package Manager and did what you told me. Then I went to the Ubuntu Software Center and Uninstalled OpenJDE. but here's the weird, When Unintalling, it said progress (1) so I clicked on that line and while it was unintalling a Sun java user agreement popped up asking me if I agree to Sun's Terms so I clicked yes, then forward and finish. But I can't figure out how it automatically did that. 

I just assumed I would:

1st do Synaptic Package Manager and enable 'Canonical Partners' boxes,

2nd goto Software Center and remove OpenJDE,

3rd go back to the Synaptic Package Manager to search,find, and install sun java but the last step happened automatically. weird, just don't understand.

All I can think of is I was trying to install the sun java bin prior to doing that Synaptic Package Manager and that maybe wh~ ugg I can't finish this sentence, I don't know how sun started installing without me first even searching for it but I'm glad it's installed and working and also it fixed the problems I was having with frost, Just wish I knew how that happened.

Anyways, Sorry for the run on post, and all is working :) And hopefully this thread can be useful to other that run into the same problem of frost not starting up.

---

### Post by oldos2er on 2010-11-05
I don't use Software Center, in fact I've uninstalled it, so I can't check its behavior; but you could have done all your updating, installing, and removing from Synaptic.

From what you describe, I don't know what happened either, but I'm glad everything is working for you now!  :)  Could you please mark the thread as 'Solved'?

---

### Post by unone95 on 2010-11-05
If that's the case, what's the purpose of having both Synaptic and Software Center?

PS Marked as Solved.

---

### Post by Lubos on 2010-11-06
> **unone95 said:**
> what's the purpose of having both Synaptic and Software Center?

Synaptic looks like "ugly" software from professionals for professionals
Software center looks like software from professionals for nonprofessionals with colors, icons, screenshots

:popcorn:

---

### Post by oldos2er on 2010-11-06
> **unone95 said:**
> If that's the case, what's the purpose of having both Synaptic and Software Center?


You'd have to ask the devs that. I can't account for their actions.  :)

---

