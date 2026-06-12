---
title: "Application prevents shutdown problem"
date: 2011-10-11
forum: General Help
---

### Post by fnadde42 on 2011-10-11
Hello Forum! I have recently got my first Ubuntu desktop computer. Almost everything went fine. All drivers installed perfectly. A little hazzle with the keyboard but it's now working fine.

Problem starts when I try to quit my computer and Teamspeak is running. Instead of shutting down the computer, it just shuts down Teamspeak and just stops right there. Then I have to command the computer again to shut down.

It's just Teamspeak that does this.

Anyone got a solution?

---

### Post by pr3zident on 2011-10-11
> **fnadde42 said:**
> Hello Forum! I have recently got my first Ubuntu desktop computer. Almost everything went fine. All drivers installed perfectly. A little hazzle with the keyboard but it's now working fine.

Problem starts when I try to quit my computer and Teamspeak is running. Instead of shutting down the computer, it just shuts down Teamspeak and just stops right there. Then I have to command the computer again to shut down.

It's just Teamspeak that does this.

Anyone got a solution?

try uninstalling the application and re-installing it to see what happens ... or when you finish with the application kill it ps -e find the id and then kill the id

---

### Post by WasMeHere on 2011-10-11
I think it is good practice to close applications programs before shutting down your computer. It is a safety precaution to avoid leaving files, or Teamspeak sessions or background networking (is there such a thing?) not properly closed.

Have fun finding out about Ubuntu
Olle

---

### Post by fnadde42 on 2011-10-11
> **Olle Wiklund said:**
> I think it is good practice to close applications programs before shutting down your computer. It is a safety precaution to avoid leaving files, or Teamspeak sessions or background networking (is there such a thing?) not properly closed.

Have fun finding out about Ubuntu
Olle

You're right. It's always good to manually close every application. It was just something that bugged me: "Why are every other application shutting down EXEPT Teamspeak...?"

Anyway, I think that was the best answer... :)

---

