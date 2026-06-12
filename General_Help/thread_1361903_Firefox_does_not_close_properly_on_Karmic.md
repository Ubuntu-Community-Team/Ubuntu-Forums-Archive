---
title: "Firefox does not close properly on Karmic"
date: 2009-12-22
forum: General Help
---

### Post by dumpster25 on 2009-12-22
Hi,

I'm running Karmic with kernel 2.6.31-16-generic and Firefox 3.5.6

My problem is that Firefox doesn't close properly. Every time I shut Firefox down nicely and try to start it again it tells me that a process is already running.
I must then kill the process using either through the terminal or using the System Monitor.

I've been experiencing this problem since I upgraded to Karmic.

I've searched for solutions in the forums and launchpad without any success.
Is there anyway for me to fix this. Does anyone have a solution?

Thanks

---

### Post by MooPi on 2009-12-22
I've experienced this as well. after you start Firefox check to see if more than one instance is registering on the System Monitor.

---

### Post by goosecaboose on 2009-12-22
I'm having the same problem.
And it's just one process running for me, no zombies or anything. It's very annoying.

---

### Post by akakingess on 2009-12-22
> **MooPi said:**
> I've experienced this as well. after you start Firefox check to see if more than one instance is registering on the System Monitor.

That, and you could also install top or htop and see the exact PIDS (daemons and all) still running in the background, obviously most of those should be there, but if there is still an instance if FireFox there, you can catch the PID# for it and kill it, or just kill FireFox by name as well.

EDIT: Just to make sure, you aren't closing it and then immediately trying to reopen right after are you, in other words you are at least giving it about 15 seconds to completely close out before trying to reopen, correct?  I assume that you are all doing it correctly, just want to rule out the obvious first before we move on to the more complex stuff.

---

### Post by MooPi on 2009-12-22
Justed check Mozilla and they feel it is an extension issue
[https://support.mozilla.com/en-US/kb/Firefox+hangs#Hang_at_exit](https://support.mozilla.com/en-US/kb/Firefox+hangs#Hang_at_exit)

---

### Post by goosecaboose on 2009-12-22
> **akakingess said:**
> 
EDIT: Just to make sure, you aren't closing it and then immediately trying to reopen right after are you, in other words you are at least giving it about 15 seconds to completely close out before trying to reopen, correct?  I assume that you are all doing it correctly, just want to rule out the obvious first before we move on to the more complex stuff.

You don't have to be condescending. And just for the hell of it, I did what you said, and it still didn't work. Plus, that would be an extremely dumb thing, since a 15-sec limit doesn't even exist on OSX or even Windows for that matter. Why shouldn't I be able to open up a new window immediately?
It has nothing to do with time for me. The problem started when I updated to Karmic.

---

### Post by akakingess on 2009-12-22
> **goosecaboose said:**
> You don't have to be condescending. And just for the hell of it, I did what you said, and it still didn't work. Plus, that would be an extremely dumb thing, since a 15-sec limit doesn't even exist on OSX or even Windows for that matter. Why shouldn't I be able to open up a new window immediately?
It has nothing to do with time for me. The problem started when I updated to Karmic.

I was in no way trying to be condescending, I apologize if you took it that way, that is why I even said that I figured that you all were doing that correctly. I am just trying to help out with trains of thought, etc. I will discontinue trying to help since you take everything so sensitively. Also, I have closed down Firefox before and then remembered that I had forgotten do something and immediately hit the shortcut again and it gave me that message, hence my trying to rule that out.

---

### Post by dumpster25 on 2009-12-22
> **akakingess said:**
> That, and you could also install top or htop and see the exact PIDS (daemons and all) still running in the background, obviously most of those should be there, but if there is still an instance if FireFox there, you can catch the PID# for it and kill it, or just kill FireFox by name as well.

EDIT: Just to make sure, you aren't closing it and then immediately trying to reopen right after are you, in other words you are at least giving it about 15 seconds to completely close out before trying to reopen, correct?  I assume that you are all doing it correctly, just want to rule out the obvious first before we move on to the more complex stuff.

I'll suppose we'll have to move to the more complex stuff then, because this is not relative to the time after I've chosen to quit the program nicely. It just stays there as a sleeping process for a long time. Only option is to kill it if i want to use firefox again.

Also, I'd advice you to be a bit more easygoing to new users and don't scare them away with terms that alienate them. All ubuntu users are not familiar with the terminal, top, PIDs etc. Take it like constructive criticism ;)

For me it also like in goosecaboose's case, started after upgrading to Karmic.

> **MooPi said:**
> I've experienced this as well. after you start Firefox check to see if more than one instance is registering on the System Monitor.

Only one instance for me. And on ending the process it's the same one that sleeps until I forcefully kill it.
And for me it's not an extension issue since I've got none.

---

### Post by goosecaboose on 2009-12-22
> **akakingess said:**
> I was in no way trying to be condescending, I apologize if you took it that way, that is why I even said that I figured that you all were doing that correctly. I am just trying to help out with trains of thought, etc. I will discontinue trying to help since you take everything so sensitively. Also, I have closed down Firefox before and then remembered that I had forgotten do something and immediately hit the shortcut again and it gave me that message, hence my trying to rule that out.

You said "*I assume that you are all doing it correctly, just want to rule out the obvious first before we move on to the more complex stuff*.". And now you're trying to smooth it all over saying you were "*trying to rule it out*".
You're just digging yourself a deeper hole, girl.

---

### Post by akakingess on 2009-12-22
> **dumpster25 said:**
> I'll suppose we'll have to move to the more complex stuff then, because this is not relative to the time after I've chosen to quit the program nicely. It just stays there as a sleeping process for a long time. Only option is to kill it if i want to use firefox again.

Also, I'd advice you to be a bit more easygoing to new users and don't scare them away with terms that alienate them. All ubuntu users are not familiar with the terminal, top, PIDs etc. Take it like constructive criticism ;)

For me it also like in goosecaboose's case, started after upgrading to Karmic.



Only one instance for me. And on ending the process it's the same one that sleeps until I forcefully kill it.
And for me it's not an extension issue since I've got none.

I take absolutely no offense to constructive criticism (actually encourage it), my problem is that I tend to not even pay attention to how many 'beans' someone has before I post, but you are right, I should try to slow it down a tad until it comes to the higher levels.  Thanks for the criticism and I will try my best to pay more attention to who I am posting responses to.

---

### Post by dumpster25 on 2009-12-22
> **akakingess said:**
> I take absolutely no offense to constructive criticism (actually encourage it), my problem is that I tend to not even pay attention to how many 'beans' someone has before I post, but you are right, I should try to slow it down a tad until it comes to the higher levels.  Thanks for the criticism and I will try my best to pay more attention to who I am posting responses to.

Thank you for your answer and for your time.

Do you recommend starting Firefox using 'strace' and then ending it nicely and see what kind of output I get?

Or does Firefox have a built in logging feature like Thunderbird does?

---

### Post by akakingess on 2009-12-22
The only way that I know of (I by no means am an expert and don't pretend to be) is to launch it from within the terminal which is located under the Accessories sub-menu under Applications. So I would open the terminal and just type in Firefox (or in some cases you have to type Firefox-3.5) and the terminal will remain open and should show at least major errors I believe. To be quite honest, I am not even familiar with 'strace', so it could be a better alternative.

---

