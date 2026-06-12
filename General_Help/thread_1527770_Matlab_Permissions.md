---
title: "Matlab Permissions"
date: 2010-07-09
forum: General Help
---

### Post by JCM_Pico on 2010-07-09
Hi there,
I recently Installed Matlab and it keeps giving me this permission error, even after rining the following command.
sudo chown -R ${USER}:${USER} ~/.matlab

Does anybody know how to solve this


Cannot write to preference file "matlab.prf" in "/home/*"username"*/.matlab/R2010a".
Check file permissions.
Cannot write to preference file "matlab.prf" in "/home/*"username"*/.matlab/R2010a".
Check file permissions.
The desktop configuration was not saved successfully

---

### Post by JCM_Pico on 2010-07-11
I solved the proble using chmod -R 777 ~/.matlab
I hope it does not kill with the program

---

