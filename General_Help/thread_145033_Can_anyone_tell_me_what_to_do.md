---
title: "Can anyone tell me what to do?"
date: 2006-03-15
forum: General Help
---

### Post by lesada411 on 2006-03-15
Each time I open up the available update window a screen comes up: Unavailable to get exclusive lock--- Another package managment application is (like apt -get or aptitude already running. Please close.----  There is nothing else running.  What can I do to get those updates installed?   Thank-you

---

### Post by s_spiff on 2006-03-15
dude, you must be having synaptic or apt-get on... thats why it gives u that error... if you cant figure out what i'm talking about, just reboot ur machine...connect to the net, and click on that update icon... it'll open up...and show you what all updates are required to be downloaded.

---

### Post by lesada411 on 2006-03-15
What web site can I go to and get the updates?

---

### Post by stabface on 2006-03-15
i had a problem like this it happened after i had a failed install from the Synpatic program. I had to do a dpkg of the program i was installing at the time to finish the job and it worked fine.

---

### Post by lesada411 on 2006-03-15
Can you tell how to do that?

---

### Post by m.vanderpoel on 2006-03-15
I had the same problem. With me it was that indeed I had Synaptic open on an other virtual desktop.
Could you first answer the two suggestions made to you:
1) do you have Synaptic open?
2) did you have a Synaptic in stall go wrong?

Greetz, Marlies.

---

### Post by lesada411 on 2006-03-15
No.  I rebooted 2 times and I still had the same problem.

---

### Post by m.vanderpoel on 2006-03-15
Did you have an  install through Synaptic go wrong?

Almost ready to sign of, (bedtime), Marlies

---

### Post by lesada411 on 2006-03-15
No.  I had nothing installing.  I had just rebooted up.

---

### Post by m.vanderpoel on 2006-03-15
Just to make sure.
What do you mean when you say you 'open up the available update window '
Do you mean 
- the red little warning thing with security-updates (top right of screen), or 
- System->admin->update manager, or
- ?

Greetz, Marlies.

---

### Post by lesada411 on 2006-03-15
I clicked on the red warning.

---

### Post by m.vanderpoel on 2006-03-15
Please explain.
Sorry I didn't notice, but then (I'm new to this forum), what does it mean when someone clicks the red button?

Sleepy I guess, You meant the red buuton on top right of screen?
After you click, it opens up and shows the updates.
 (normally)
You **don't** have to add anything whatsoever. It's security-updates you get from day one, without asking.

---

### Post by stabface on 2006-03-22
if you click the red button then the missle fire what else would happen?

---

### Post by wsanders on 2006-03-22
If you have a chance, copy and paste the result of 
```

ps -A

```
(make sure the A is capitalized)

---

