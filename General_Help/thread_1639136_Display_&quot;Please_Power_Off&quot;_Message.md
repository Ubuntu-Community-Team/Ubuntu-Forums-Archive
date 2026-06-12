---
title: "Display &quot;Please Power Off&quot; Message"
date: 2010-12-06
forum: General Help
---

### Post by awp2513_ on 2010-12-06
Hi,

I have a system that is used to run a single application. When a user is done, they are able to press a shutdown button. However, the user must flip a power switch to actually turn the system off once the system has shut down.

We've made a switch to Ubuntu 10.04, and I'm trying to figure out how to display a message to the user indicating that it is ok to power off the system. 

Here's the flow I'm trying to achieve

1.) User presses the shutdown button.
2.) The Plymouth splash screen appears, and, I'm assuming, the rc0 scripts are run.
3.) The splash screen disappears and the user is presented with a black screen with the text "Please power off the system" (Or something like it).
4.) The user can then flip the power switch (the system really is ok to be shut down).

I'm using a custom splash screen (Plymouth). Is there a way to tell when the system is really done shutting down and have it display the message?

What about editing the halt (/etc/init.d/halt) script?

My main concern is that I do not want to tell the user it is ok to power off before it really is.

Any suggestions?

Thanks!

---

