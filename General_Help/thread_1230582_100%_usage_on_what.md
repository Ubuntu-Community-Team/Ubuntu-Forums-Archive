---
title: "100% usage on what?"
date: 2009-08-03
forum: General Help
---

### Post by theShaggy on 2009-08-03
Hey folks, using Jaunty-64.

My computer is currently using 100% of my CPU, which only started the other day (I've been trying to get some games running to no avail, along with a webserver and such).  When looking at my status monitor, it is a solid dull-blue (as opposed to the bright blue which is spikes up and down, as it should).

The thing is, when I go to the Status Monitor window, it shows absolutely nothing using CPU processes, but still tells me that 100% is in use.  My computer is churning and churning and slows right down, so how can I tell what is running in the background?

---

### Post by Finalfantasykid on 2009-08-03
If it is a background daemon of somesort, you can see this by going to your system monitor, then going View > All Processes.  That should allow you to see everything, including daemons, and other normally hidden system processes.

---

### Post by Locutus_of_Borg on 2009-08-03
run the program "top" in a terminal, it should list all running processes, you could alternatively change system monitors preferences to show all processes as opposed to the default of just user processes

also, it is probably X and it is probably resulting from video driver in some way, but that is just speculation without detail

---

### Post by theShaggy on 2009-08-03
I checked it, and it still gave me nothing.  They didn't show anything other than Xorg using a lot of resources.

However, I went ahead and uninstalled a whole bunch of useless programs that I wasn't using any more, something must have been running in the background without saying so, as it now works fine.

---

### Post by tabibito on 2009-08-04
Try to check the '%wa' parameter using the top command. It's in the third line from above. Probably that what is eating your CPU, and if it does, prepare to buy a new HD 'cause mine is also showing the same symptom. No heavy program  running but the CPU will occassionaly peak to 100%.

---

