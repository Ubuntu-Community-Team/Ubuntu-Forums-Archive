---
title: "Thunderbird wont start"
date: 2012-05-26
forum: General Help
---

### Post by linux12 on 2012-05-26
I was using firetray to try and make Thunderbird launch on startup, but now it won't launch at all... I tried reinstalling it, but that didn't do anything. What gives?:confused:

---

### Post by wojox on 2012-05-26
If you start it from the terminal (Ctrl+Alt+T) it will usually spit out some errors.
```
thunderbird
```

---

### Post by Habitual on 2012-05-27
thunderbird -v
What firetray version also please.

---

### Post by linux12 on 2012-05-27
> **Habitual said:**
> thunderbird -v
What firetray version also please.
Thunderbird version 12.0.1 The  one that came with Precise Pangolin. I don't know what version of firetray, but it is likely the latest as I downloaded it last night. Interestingly, when I run thunderbird in the terminal, nothing happens, but when I try to close it, it says that there is an application running in the terminal.

---

### Post by scouser73 on 2012-05-27
> **linux12 said:**
> Thunderbird version 12.0.1 The  one that came with Precise Pangolin. I don't know what version of firetray, but it is likely the latest as I downloaded it last night. Interestingly, when I run thunderbird in the terminal, nothing happens, but when I try to close it, it says that there is an application running in the terminal.

I suggest you delete the Thunderbird profile, go to your home folder, press CTRL & H and look for a folder labelled **.thunderbird** Delete that folder and restart Thunderbird and you shouldn't encounter any more problems with it.

---

### Post by linux12 on 2012-05-27
It's not working... thanks for the suggestion though!;)

---

### Post by linux12 on 2012-05-27
Looking in that folder though, I found another folder labeled crash reports. Inside... is a text file labeled "InstallTime 20120430060637"... containing the number 1338136891. Otherwise the folder is empty...

---

