---
title: "Ubuntu Software Center is not working."
date: 2011-12-03
forum: General Help
---

### Post by Fusuy on 2011-12-03
Hello! 

i can download programs via terminal using apt-get but when i try to install some software on ubuntu software center it show me this error message: "Failed to download package files, check your internet connection." but my connection is ok. is this a DNS problem? how can i fix this

---

### Post by oldtimer7777 on 2011-12-03
> **Fusuy said:**
> Hello! 

i can download programs via terminal using apt-get but when i try to install some software on ubuntu software center it show me this error message: "Failed to download package files, check your internet connection." but my connection is ok. is this a DNS problem? how can i fix this

No idea. But you can try using Synaptic Package manager instead to do the same role.

sudo apt-get install synaptic
sudo synaptic

---

### Post by bluexrider on 2011-12-03
> **oldtimer7777 said:**
> No idea. But you can try using Synaptic Package manager instead to do the same role.

sudo apt-get install synaptic
sudo synaptic

why answer the question then?


OP please post your ERRORS here lets see if we can get an answer. 

in the mean time go to your software sources and change the Download from: main server to "other" then choose best server.

Try again

---

### Post by oldtimer7777 on 2011-12-03
> **bluexrider said:**
> why answer the question then?


OP please post your ERRORS here lets see if we can get an answer. 

in the mean time go to your software sources and change the Download from: main server to "other" then choose best server.

Try again

Because perhaps they have a need to use a GUI front end instead of apt-get until the problem is completely resolved for themselves...  I don't know.. Maybe you should ask them instead.  Interim work-arounds are good suggestions too.  I hate software center btw.. Dumbed down and slow as molasses. Synaptic is way better. And Synaptic Package Manager will actually tell you what is wrong if it fails -unlike- software center that just sits there with a real vague error msg.

---

### Post by bluexrider on 2011-12-03
> **oldtimer7777 said:**
> Because perhaps they have a need to use a GUI front end instead of apt-get until the problem is completely resolved for themselves...  I don't know.. Maybe you should ask them instead.  Interim work-arounds are good suggestions too.  I hate software center btw.. Dumbed down and slow as molasses. Synaptic is way better. And Synaptic Package Manager will actually tell you what the wrong if it fails -unlike- software center that just sits there with a real vague error msg.


@oldtimer7777

In the event of the posting I may agree with you about the "software center" being slow and well i like synaptic better myself. But answering a post with no idea?

---

### Post by Fusuy on 2011-12-03
Thank guys! Changing server fixed it. 
And there is no need to dispute. it was good idea to install synaptic manager. i dont know why it is not installed default in new version of ubuntu.

---

### Post by oldtimer7777 on 2011-12-03
> **Fusuy said:**
> Thank guys! Changing server fixed it. 
And there is no need to dispute. it was good idea to install synaptic manager. i dont know why it is not installed default in new version of ubuntu.

I don't know why they removed Synaptic Package manager either.  It is so much more robust than software center, and even has more options and features too.  Don't forget to close this thread above when you are done. Just mark it as solved from the drop down above.

---

### Post by oldtimer7777 on 2011-12-03
> **bluexrider said:**
> @oldtimer7777

In the event of the posting I may agree with you about the "software center" being slow and well i like synaptic better myself. But answering a post with no idea?

I was being honest about the real issue.  I wasn't going to guess at something, but I gave them the best work-around for right now possible until they could figure it out. Sometimes a work-around will provide a path to a solution for some users.   On the otherhand, nothing ever solved nothing. A work-around is better than nothing when they need a GUI to work with software packages. Without Synaptic I would be pretty screwed myself without something like it to do the same job, so that is why I suggested it. What is so complicated about that?

---

### Post by bluexrider on 2011-12-03
Glad your going now. 

Thanks oldtimer7777 


Please mark this (SOLVED)

---

### Post by Fusuy on 2011-12-04
Sorry, totally forgot. Done!

---

