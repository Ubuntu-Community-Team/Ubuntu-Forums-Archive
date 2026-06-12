---
title: "Update Manager Error"
date: 2011-05-26
forum: General Help
---

### Post by PZJM on 2011-05-26
Hey folks,

I just started receiving error while trying to run my update manager.  I was able to capture the error but I'm not sure how to resolve this issue.  Any help would be greatly appreciated.  Thanks.

Also, my Ubuntu Software Center won't even launch.

---

### Post by matt_symes on 2011-05-26
Hi

Open a terminal and type 

```
sudo rm -rf /var/lib/apt/lists/*
```

Enter your password. It will not be echoed to the screen. This is normal.

Then type 

```
sudo apt-get update
```

Kind regards

---

### Post by PZJM on 2011-05-26
Sweet!  Worked like a charm.  Originally, I started deleting the individual files.  So, why is this normal.  I have yet to experience such an issue.

Thanks

"Ditched Winblows 3 months ago
and I'm loving it"

---

