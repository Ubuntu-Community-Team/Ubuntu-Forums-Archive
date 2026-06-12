---
title: "SYSTEM MONITOR reports &quot;sleeping&quot;"
date: 2010-11-10
forum: General Help
---

### Post by unueco on 2010-11-10
Greetings:

When I run system monitor in Ubuntu 9.10 Karmic it reports to me that ALL my processes are "sleeping"....with the exception of the annotation for System Monitor itself. 

Also, when I try to change the priority of a process (the "nice" level??) nothing seems to happen.

Am I missing something here.

Assistance appreciated!

---

### Post by Foxheadz on 2010-11-10
Unless your application is lagging you shouldn't need to change any of this. Just because an app is "sleeping" doesn't mean it's not needed, it just means its not being used...or something like that

---

### Post by Frogs Hair on 2010-11-10
Mine also reports all sleeping . I use nmon from the software center which runs from the terminal or just type top into the terminal.Htop works well too for monitoring processes.

---

### Post by Decatf on 2010-11-10
That is normal. Sleep means the processes are idle. If they were all running then your system would likely be heavily bogged down.

---

### Post by unueco on 2010-11-11
> **Decatf said:**
> That is normal. Sleep means the processes are idle. If they were all running then your system would likely be heavily bogged down.

If all processes are reported as "sleeping"...then how can I use this to determine when a process is "hanging"? (which is why I turned to it in the first place)

Also, how do I change the priority? As I mentioned above, nothing seems to happen when i use the Change Priority option from the right click menu.

Thanks again!

---

### Post by Decatf on 2010-11-12
There are a number of process states in Linux. I can't remember off the top of my head but if a process is "hanging" it may be in the Interruptable or Uninterruptable state. It may also be in the Stopped state although I don't think a process would normally be in this state unless it was manually stopped by the user.

Is there a specific process that is causing you problems?

---

### Post by unueco on 2010-11-12
> **Decatf said:**
> Is there a specific process that is causing you problems?

Skype.

I turned to this because i have noticed sometimes Skype seems "unrepsonsive". For example, even though it shows me that I am online, others see me as offline and messages do not go thru. Other times, I notice that my "friends" list has few or no users listed as online....though i know they are. Restarting the program tends to correct the errors.

But in general, I'd just like to know how to use System Monitor.

---

### Post by Foxheadz on 2010-11-12
There not really much to do with it. Most programs will be set to the correct priority. Also, if a program becomes unresponsive hit alt+f2 type in "xkill" and then click on said program

---

### Post by mister_playboy on 2010-11-12
> **unueco said:**
> If all processes are reported as "sleeping"...then how can I use this to determine when a process is "hanging"?

Usually you look for the process that is using a high % of CPU.  On a multicore this number may be lower since it's only hanging one core... say 50% usage on a dual-core.

---

