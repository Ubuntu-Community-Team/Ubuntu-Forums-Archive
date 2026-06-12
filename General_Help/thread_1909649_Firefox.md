---
title: "Firefox"
date: 2012-01-15
forum: General Help
---

### Post by Corvair on 2012-01-15
Hello everyone

I have a problem when signing in to Firefox I get the indication below.
Also it causes me to loose my bookmarts. I have to go to a previous date and reload the bookmarts. I have gone to using Google Chrome to see if this will be better. So far so good but I would like to go back to using Firefox. I have re installed Firefox but it did not solve the problem.
The following does not mean anything to me.
How can I solve this?

Assertion failed

ASSERT: node must have _DOMElement set
Stack Trace: 
0:TV_V_nodeAnnotationChanged([object ResultNodeClassInfo],livemark/loadfailed)
1:removeItemAnnotation(6371,livemark/loadfailed)
2:LS__updateLivemarkChildren(0,false)
3:LS__checkAllLivemarks()
4:LS_start()
5:start()
6:(0)

---

### Post by papibe on 2012-01-15
Do you have any add-ons installed? If so, it could be interesting to see if you disable them, and trying again.

If the problem is solved, you have a faulty add-on. Enable them one at a time to identify the culprit.

Just some thoughts,
Regards.

---

### Post by pqwoerituytrueiwoq on 2012-01-15
try a new firefox profile or firefox's safe mode (all add-ons disabled)
[FONT=Courier New]~$ firefox -P
~$ firefox -safe-mode

[/FONT]

---

### Post by Corvair on 2012-01-15
Hello,
Disabling the add ons did not do the trick but deleting profile and adding a new profile seems to have done the trick.
Thanks for your help.

---

