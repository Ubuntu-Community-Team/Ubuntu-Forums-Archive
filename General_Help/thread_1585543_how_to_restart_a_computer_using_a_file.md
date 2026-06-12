---
title: "how to restart a computer using a file?"
date: 2010-09-30
forum: General Help
---

### Post by elephant99 on 2010-09-30
i have a problem i cant access remote support on teamviewer but i have access to transfer file. is there a way to make a file and send it to restart the computer. or is there anyway i can restart the computer over the internet. i cant be physically be at that computer for another 1 week.

---

### Post by spiky001 on 2010-09-30
I use ssh then the command reboot

---

### Post by efflandt on 2010-09-30
I haven't tried reboot (which invokes shutdown), but when I used a laptop as terminal or X display for a headless Linux PC in my basement, I either did **su -** first (or **sudo** prefix depending upon the system) to do **shutdown -r +1 &**

That would fork into the background and give me a minute to log out of ssh.

When I tried **shutdown -r now** (especially in the foreground without &) I think it would immediately interrupt ssh and the shutdown command would abort.

---

