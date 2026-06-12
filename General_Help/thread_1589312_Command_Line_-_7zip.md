---
title: "Command Line - 7zip"
date: 2010-10-06
forum: General Help
---

### Post by TomAbada on 2010-10-06
hi all
i need help with 7zip
i need to write a short script that will compress a specific folder that`s on the Desktop (and all it`s content)
and also will encrypt it with a password that is inside the script --->meaning it wont ask for a password+verification when compressing+encrypting

thanks a lot in advance

---

### Post by gradinaruvasile on 2010-10-06
man 7z

for 7zip command line options.
You can use ccrypt for encryption.
But be careful with that encrypting stuff - you will have to put the password in plaintext in your script in order to achieve no prompts. That is not good security-wise.
And make sure that you first compress the data then encrypt it - scrambled content yields low compression rates.

---

