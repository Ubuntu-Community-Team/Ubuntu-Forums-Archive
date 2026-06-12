---
title: "How to obtain a proper stacktrace for Firefox 3.7a2pre"
date: 2010-02-16
forum: General Help
---

### Post by Prescience500 on 2010-02-16
I'm having trouble getting a proper stack-trace for Firefox 3.7a2pre  64-bit. I built it from ppa:ubuntu-mozilla-daily/ppa. I followed the  instructions on [https://wiki.ubuntu.com/MozillaTeam/Bugs#Obtain%20a%20backtrace%20from%20an%20apport%20crash%20report%20%28using%20gdb%29](https://wiki.ubuntu.com/MozillaTeam/Bugs#Obtain%20a%20backtrace%20from%20an%20apport%20crash%20report%20%28using%20gdb%29) and  [https://wiki.ubuntu.com/Apport#How%20to%20enable%20apport](https://wiki.ubuntu.com/Apport#How%20to%20enable%20apport).  I made sure I tried to make the proper changes to the scripts I wrote  in terminal so that it was aiming at Firefox 3.7a2pre and not Firefox  3.6.
When I posted the bug report on Mozilla's bug tracker, they  rejected the stack-trace. They said that for most distros, I'd need to  run it against xulrunner instead of Firefox. I downloaded debugging  symbols for xulrunner 1.9.3a2pre and tried again. This time I noticed a  line in terminal telling me "no stack trace." I tried several more  times, this time "aiming" it at xulrunner 1.9.3a2pre instead of Firefox  3.7a2pre. Each time I changed the script in terminal a little, but each  time it said "no stack-trace."

Can someone please help me?

---

