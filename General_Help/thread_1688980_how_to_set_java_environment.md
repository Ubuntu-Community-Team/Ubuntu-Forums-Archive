---
title: "how to set java environment"
date: 2011-02-16
forum: General Help
---

### Post by dogfjjf1 on 2011-02-16
I am working on other's pc. I got a problem. I put the export sentence in the user's ~/.bashrc and root's ~/.bashrc. So when I type java -version either in user account or root account in the terminal, it works correctly. But when I type sudo java -version, the error appears, it cannot find the java. I am really confused. Is sudo different from directly using root account? How to set java environment when I type sudo in user account? Help.....

---

### Post by lykeion on 2011-02-16
The correct way to set Java version is using the command *update-java-alternatives*. Read the manual page of the command (afterwards quit with q):
```
man update-java-alternatives
```

---

