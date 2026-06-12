---
title: "Strange behaviour - slowing down after booting"
date: 2012-08-24
forum: General Help
---

### Post by tonymoloney on 2012-08-24
My Lenovo laptop has started behaving strangely.
I am running 12.04 LTS with the Gnome Desktop and about 30 seconds after booting in the usual 50 seconds, the computer slows to a crawl for about 2 minutes and then comes good again.

To try to see what is happening, I booted up and immediately started System Monitor and could see that all 4 threads of the CPU were running at a low percentage, when suddenly they all jumped up to between 50 and 60 percent utilisation. They stayed that way for the next two minutes and the everything returned to normal.

There was no disk swapping at the time and only a brief network access every few seconds.

Has anyone else had a similar problem?

---

### Post by 2F4U on 2012-08-25
Which programs caused the CPU to ramp-up? You should be able to see this in the process list. I've heard that, for example, the zeitgeist daemon can cause such a behaviour when it attempts to search and index your files.

---

### Post by tonymoloney on 2012-08-25
Sorry, as far as I can see I don't have the zeitgeist daemon on my system. I'm going to reboot now and check the processes.

---

### Post by tonymoloney on 2012-08-25
Thanks for the heads up. I've found the problem and it is the ubuntuone-syncmonitor. And yes, I do have the zeitgeist daemon, just didn't know it, but it's not causing the problem.

How do I mark this as solved?

---

### Post by Kopkins on 2012-08-25
At the top of the page under thread tools, you can select 'mark as solved.'

Kopkins

---

