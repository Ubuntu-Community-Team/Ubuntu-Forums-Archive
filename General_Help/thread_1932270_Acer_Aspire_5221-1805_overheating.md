---
title: "Acer Aspire 5221-1805 overheating"
date: 2012-02-27
forum: General Help
---

### Post by boatish on 2012-02-27
Greetings! 
    I own an Acer Aspire 5221-1805; I am running Ubuntu 10.04; and I have an issue with overheating. I have lm-sensor installed now, ran it and my temperature came up as 55C with an allowable temperature of 200C maximum. But that is only becasuse I placed a couple ice packs under the laptop so I could do the install. 
    Often I just have to shutdown in the middle of my work. 
    My fan does not always stay on, it turns on by the time the system is already hot, but by then the system is too hot. I have cleaned my fan ports and elevated the back of the computer for better airflow - but it still gets hot.
    Is there a way to keep the fans running constantly or at least turn on sooner? I often have multiple windows open and graphics running for my work; so I cannot just use one application at a time. I have heard that there was a problem with Ubuntu running CPUs at the maximum temperature, and have read some forum posts on that subject - but the explanations only gave command lines with no explanation if they could do system harm.
    I am also still trying to learn the 10.04 system, so if you have an answer, please explain what it is the command means and what it will do to my system.

Thank you, boatish

---

### Post by Mark Phelps on 2012-02-27
Recent Ubuntu versions have a kernel bug that can result in overheating.  See link below:

[https://bugs.launchpad.net/ubuntu/+bug/901232]("https://bugs.launchpad.net/ubuntu/+bug/901232")

Typical solutions others have used is to install Jupiter to throttle-back their PC -- a solution that looks like it won't work for you.

Sorry, but if your laptop is overheating all the time, then you won't be able to use Ubuntu on it.

---

### Post by Bobhuber on 2012-02-27
This was one solution posted at the end of the bug report. 

 Quote >I changed to Lucid and installed the 3.0.0-13-generic kernel (backports).
With this configuration I can change the CPU frequency.

I'm not up on what Kernel you are using with 10.04 on the Laptop but  what this suggests is that you may be able to install a different Kernel  to solve your problem.

---

### Post by boatish on 2012-02-28
Thank you.
   At this time my solution has been to cut a couple of 1" x 2" x 1" wooden blocks (out of Purple Heart wood :rolleyes:), and it seems to be helping to a decent degree. But I will be reading the rest of your instructions carefully. But as of now... my riser is a pretty purple! 

Again, thank you. And I am still willing to hear any other suggestions.

Sincerely, boatish.

---

