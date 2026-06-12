---
title: "2 questions about System Monitor!"
date: 2010-04-02
forum: General Help
---

### Post by hakermania on 2010-04-02
Hi all!
first of all I would like to ask when does the system use the Swap and why, and secondly i would like to ask why the System monitor from the one hand it shows that my Ram uses 240MB of my 2Gib and from the other hand when I go to see the applications running the sum of the memory is lower than 100MB?
See the images below:
[I have 1,7Gbit free Ram...However the system uses the Swap:]
[IMG]http://img225.imageshack.us/img225/4795/screenshotag.png[/IMG]
[From the previous pic you can see that the System monitor says that I use 240MB but the sum of the memory that the running applications take isn't the same:]
[IMG]http://img526.imageshack.us/img526/7919/screenshot1uk.png[/IMG]
Can anybody explain me when does the Swap is used and why is this difference between the sum and the system monitor's result of used memory?
;)?

---

### Post by Ancanus on 2010-04-02
Hello hackermania,

for your swap questions, please take a look at this link:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by DrMelon on 2010-04-02
Some of the memory in use is being used by the kernel itself, which is why the sum is smaller than the total used.

---

### Post by hakermania on 2010-04-03
> **Ancanus said:**
> Hello hackermania,

for your swap questions, please take a look at this link:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Ok I read it, but I don't think so that my System has not enough memory and decides to use the Swap!
How can I disable the Swap space?
I have realized that while my System uses the Swap space becomes slower!
And all in all the System does not need all this space! My Ram used memory never goes higher than 500 Mbit of 1.9GiB total!!!

---

