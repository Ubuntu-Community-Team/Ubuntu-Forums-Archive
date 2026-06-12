---
title: "Remotely Shut Off Network Computer"
date: 2009-07-28
forum: General Help
---

### Post by mrd489 on 2009-07-28
I am using Ubuntu 8.04 and am sharing a wired network with people using Windows Vista. I would like to know how to remotely shut down their computer from mine.

---

### Post by philcamlin on 2009-07-28
install vnc and so it from there 

thats what i do just remember to have a good password :popcorn:

---

### Post by niteshifter on 2009-07-28
... and your reason for wanting to do this ______ act is? 

(Or do I get to fill in the blank with A) unethical, B) amoral, C) illegal, D) all of the above, or the long shot of E) repair the network?)

---

### Post by t4thfavor on 2009-07-28
Sounds unethical to me. If you were a sysadmin, you would already know the answer to your question.

---

### Post by ericab on 2009-07-28
since they are on windows, i believe they need to have cygwin installed, or freeSSHd, to provide you with a SSH server that you could log into. 
once in on ssh to their box, navigate the directory structure to C:\windows\system32\shutdown.exe

read the /? of shutdown.exe, and voila.

if installing a ssh server on the remote systems isnt an answer, this google search should provide the answer for you

[http://www.google.com/#hl=en&safe=off&q=linux+shutdown+windows&aq=0&oq=linux+shutdown+window&aqi=g1&fp=5_nS6qv-qCw](http://www.google.com/#hl=en&safe=off&q=linux+shutdown+windows&aq=0&oq=linux+shutdown+window&aqi=g1&fp=5_nS6qv-qCw)

:)


*edit*
for example
[http://lifehacker.com/5275652/shut-down-your-windows-pc-remotely-from-linux](http://lifehacker.com/5275652/shut-down-your-windows-pc-remotely-from-linux)

---

### Post by t4thfavor on 2009-07-28
I guess since all the above mentioned methods require valid user creds, I am OK with the post. Let it be noted that I did not answer the OP's question because there was no mention of his/her authority to do so. I think I can speak for a few of the other posters when I say that this one might have been better left unanswered.

---

### Post by ericab on 2009-07-28
another method would be to purchase an ip-powerstrip such as
[http://www.ambery.com/reposw.html](http://www.ambery.com/reposw.html)
there are many other brands avaliable... just search around.
obviously this would only work if you had physical acces to the computers, as well as a switch that you had an uplink on and if you were willing to hard-off the computers :P


and finally another method would be to use LOphtCrack, to remotley crack the password to the terminal. many methods avaliable, just remember google is your freind :)

---

### Post by cariboo on 2009-07-28
The forums do not support this type of activity. This thread is closed

---

