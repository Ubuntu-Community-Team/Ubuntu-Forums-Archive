---
title: "(error: no such device:) during my upgrade from Ubuntu 9.10 to 10.04."
date: 2010-11-01
forum: General Help
---

### Post by agentfortyseven on 2010-11-01
hi everyone,
Yesterday I upgraded from Ubuntu 9.10 to 10.04 using my upgrade manager. When I restarted my computer after being prompted, I ended up with the following error:

boot from CD/DVD:
error: no such device: (followed by my UUID)
grub rescue>

I'm currently using Linux mint live CD to post this thread. I formatted my partition on which Ubuntu was installed thinking it might solve the problem, but I was wrong. I'll be thinking of installing a fresh copy of 10.04 as soon as I get out of this mess.
Please help me get rid of this message. KINDLY HELP:(.

---

### Post by agentfortyseven on 2010-11-02
SIGH!!! I'm probably the only guy on ubuntuforum who posts a thread seeking help but ends up posting the solution without anyone bothering to comment.:mad:

---

### Post by agentfortyseven on 2010-11-02
So here's the solution
1) Insert a Windows XP installation CD and reboot.
2) Boot from the CD and it will show you an option where you can repair/recover by pressing 'R'
3) This will take you to a command line asking you about the O.S i.e XP
4) Type '1' or '2' or so on depending upon the order of the O.S
5) It asks you for the administrator password.
6) Simply press 'enter' if you haven't set any.
Now here's the actual part
7) Type 'fixboot' (press enter)
This replaces your boot file with a new one.
8) Type 'fixmbr' (press enter)
It prompts you with a warning message, simply go ahead and type 'y' (press enter)
9) Type 'exit' (press enter)

System reboots and voila, you're outta this shitty situation.
ENJOY!!!:P

---

