---
title: "My installs doesnt work anymore"
date: 2009-07-11
forum: General Help
---

### Post by razorboy5 on 2009-07-11
Hi

I was installing frostwire but it was taking forever and seemed like it was frozen to me so i force closed it by logging out of my session 

when i logged back on i could not use the deb install or synaptic manager/update manager since i think the original install is still running somehow

how do i fix this problem?

---

### Post by hansdown on 2009-07-11
Hi razorboy5.

Do you get any error messages when you open synaptic?

If synaptic does open, do you see any broken packages?

Click custom filters> broken.

---

### Post by razorboy5 on 2009-07-11
it shows this error

tried typing in the code but dont know what to do after that

---

### Post by razorboy5 on 2009-07-11
here's a screenshot of me trying to run Frostwire install 

tried running the killall command dont think it worked cuz i had songbird running and that didn't close either

---

### Post by razorboy5 on 2009-07-11
sry here's the screen

---

### Post by hansdown on 2009-07-11
O.K. Click applications> accessories> terminal.

Copy and paste this into terminal and hit enter.

```
sudo dpkg -- configure -a
```

When you enter your password you won't see it. Just enter it and hit enter.

Also, the screenshot shows more than one package manager is running.

Be sure to close all programs before opening another.

---

### Post by razorboy5 on 2009-07-11
sudo --configure -a

does not show anything running however my error msg on Synaptic changed

now it tell me to fix broken packages first

researching how to do this atm

---

### Post by oldos2er on 2009-07-11
To fix broken packages, run
```
sudo apt-get install -f
```

---

### Post by hansdown on 2009-07-11
Excellent!

Open synaptic, click custom filters> broken. You should be presented with an option to "fix broken packages".

---

