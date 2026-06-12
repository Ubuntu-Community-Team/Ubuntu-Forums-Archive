---
title: "Error in Ubuntu Software Center"
date: 2010-05-31
forum: General Help
---

### Post by HoodedHooligan on 2010-05-31
I keep getting this error when I try to download a program from the Software Center:

"The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software."

I have no idea how to repair it or what even caused it.

---

### Post by DawieS on 2010-06-01
I am not sure, but I think the error is caused by the server at [COLOR=Red]**[COLOR=Black]http://archive.getdeb.net[/COLOR]**[COLOR=Black] being off-line for the last few days.[/COLOR][/COLOR] If so, you could retry when it is back on-line.
:smile:

---

### Post by HoodedHooligan on 2010-06-01
this is what the message says:

"Previous installation hasn't been completed

The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software."

---

### Post by Nabo00o on 2010-06-03
I too have exactly the same problem...

---

### Post by PsychoDevon on 2010-06-03
I had the same problem...open Synaptic instead of the Software Center, and see what it says, so I can make sure we have the same problem.

---

### Post by HoodedHooligan on 2010-06-04
Ok so when I open Synaptic Package Manager, I get this error message:

"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
E:_cache->open() failed, please report."

Ok well I ran "sudo dpkg --configure -a" in the terminal and now everything is good. Thanks man for the advice.

---

### Post by HoodedHooligan on 2010-06-04
I am curious though as to what the problem was?

---

### Post by mujahied on 2011-08-10
> **HoodedHooligan said:**
> Ok so when I open Synaptic Package Manager, I get this error message:

"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
E:_cache->open() failed, please report."

Ok well I ran "sudo dpkg --configure -a" in the terminal and now everything is good. Thanks man for the advice.
thanks this was the same issue i was getting

---

### Post by vyco10 on 2012-02-14
> **HoodedHooligan said:**
> I am curious though as to what the problem was?

I had the problem because I had Ubuntu installed on a thumb drive. I tried to install a program from the software center but I had forgotten about these other files that I had put on the thumb drive that took up space. I ran out of space during the install and that screwed up the install of the program I was trying to install.

---

