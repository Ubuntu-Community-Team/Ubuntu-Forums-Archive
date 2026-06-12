---
title: "running a .exe shows up in sys mon"
date: 2010-08-30
forum: General Help
---

### Post by badbradmx on 2010-08-30
ok, i have an old laptop running as a server it has no video output so i remote desktop to it when making changes using teamviewer. just went into the system monitor and processes to find that teamviewer.exe was running...this has kinda confused me as i thought .exe couldnt run unless using wine. which has to be configured in most cases too. i mean the program is working perfectly but why the .exe?

---

### Post by Sam on 2010-08-30
Wine applications shows as "app.exe" in the system monitor (omitting the "wine" part). Otherwise it could be a .NET/Mono application.

---

### Post by badbradmx on 2010-08-30
ok, so not wine. well it is meant for remote desktop so i think the .net could be a viable reason, there isnt any help required for this as it works i was just wondering why. but its still and exe.

ok so next question, if it is due to the .net framework stuff how does it work, so that is can show up as an exe. if that makes any sense

---

### Post by Sam on 2010-08-30
.NET/Mono applications do have the exe extension (even in linux). The Mono  interpreter handles the execution. Same goes for wine. This is why you can have .exe files running in linux.

---

### Post by badbradmx on 2010-08-30
> **Sam said:**
> .NET/Mono applications do have the exe extension (even in linux). The Mono  interpreter handles the execution. Same goes for wine. This is why you can have .exe files running in linux.

oh ok then, thanks

---

