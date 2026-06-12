---
title: "How to force a startup application to open in a minimized state"
date: 2011-01-30
forum: General Help
---

### Post by airtacable on 2011-01-30
Hello,

In my case I have TeamViewer 6 (remote desktop application) opening as one of my Startup applications. I only really need it to run in the background, so I don't need it in my face after logging in.

What I'm looking for is a command line option for opening an application in a minimized state. Is this possible? Or should I start looking into a script to find the window and minimize it?

Thanks, airtacable

---

### Post by [Snc] on 2011-01-30
> **airtacable said:**
> Hello,

In my case I have TeamViewer 6 (remote desktop application) opening as one of my Startup applications. I only really need it to run in the background, so I don't need it in my face after logging in.

What I'm looking for is a command line option for opening an application in a minimized state. Is this possible? Or should I start looking into a script to find the window and minimize it?

Thanks, airtacable

Have you tried putting it in the background?

```
*command* &
```

note the " &" in the end, that should set it to the background...

---

### Post by airtacable on 2011-01-30
Thanks [Snc],

That worked perfectly. I can see that the process is running via the top command. But how do I move into the forground? I tried fg and its PID, but got an error: "no such job". Is PID different to job number?

ATB,

airtacable

---

