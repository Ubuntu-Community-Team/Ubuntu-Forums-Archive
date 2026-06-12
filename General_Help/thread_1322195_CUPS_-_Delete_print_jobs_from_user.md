---
title: "CUPS - Delete print jobs from user"
date: 2009-11-10
forum: General Help
---

### Post by StrangeWill on 2009-11-10
```

# Printer configuration file for CUPS v1.3.9
# Written by cupsd on 2009-10-09 16:05
<DefaultPrinter MFC-8480DN>
Info Brother MFC-8480DN with Duplexer
Location Break Room
DeviceURI socket://172.16.100.10
State Idle
StateTime 1255129466
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
Option job-hold-until indefinite
</Printer>

```

Over Samba, users come in as their respective computer names (good).

However, I keep getting downlevel documents from "nobody", not very many, but accidentally printing 20 pages kind of sucks, why is this happening? And if I want to be lazy, how can I configure this to just trash all downlevel documents from nobody (or just everything from nobody).

---

### Post by StrangeWill on 2009-11-11
Bump?

---

