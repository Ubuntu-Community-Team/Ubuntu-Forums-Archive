---
title: "How to change archive server?"
date: 2009-10-20
forum: General Help
---

### Post by Usta_AsH on 2009-10-20
Hi, I have chosen Swedish keyboard system, so when i try to install something from aptitude it downloads from swedish server. But I don't live in sweden so how can i change archive server?

---

### Post by cybiko123 on 2009-10-20
1. Type Alt + F2
2. Type "gksu gedit /etc/apt/sources.list"
3. Change all references to the Swedish archive "se.archive..." to the US one "us.archive..."
4. Save the file, and close gedit.
5. Open a terminal (Applications-->Accessories) and type "sudo apt-get update" (and enter your password when prompted.)

---

### Post by snova on 2009-10-20
> **Usta_AsH said:**
> Hi, I have chosen Swedish keyboard system, so when i try to install something from aptitude it downloads from swedish server. But I don't live in sweden so how can i change archive server?

System -> Administration -> Software Properties

Click "Download From", and possibly "Other" if necessary.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

