---
title: "Update Manager problem"
date: 2009-11-25
forum: General Help
---

### Post by johntinsley on 2009-11-25
Hey folks, I have a problem with the update manager.

When I open the manager (or it opens at it's regular interval) I see what you see below in the image, all normal. So I click on "Install Updates" and I get the pop-up, "Reading Package Information" -- 'Building Dependency Tree" followed by 'Reading State Information". Then, rather than going ahead and actually installing the updates, it simply returns to the start (as in the image) without ever actually installing anything.

I'm able to install specific packages from the command line or thru syntaptic, but this normal process of updating won't seen to work. Has anyone any suggestions?

[IMG]http://computing.dcu.ie/~jtinsley/update.png[/IMG]

---

### Post by phidia on 2009-11-25
From the terminal enter > sudo apt-get update when that completes you can try the update manager gui again and see if it works correctly.

---

### Post by johntinsley on 2009-11-26
I'd tried that, it just reads the package list and actually prompts the gui to open and tell me there are new updates...

---

### Post by bumanie on 2009-11-26
Try > sudo apt-get update && sudo apt-get upgrade That should fix things up.

---

