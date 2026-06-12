---
title: "custom launcher"
date: 2010-10-16
forum: General Help
---

### Post by pavankumarl73 on 2010-10-16
Hello everyone,
              I have installed Matlab, its an Digital signal Processing application. I have to start it by giving the following commands from terminal
   cd Matlab/bin
   ./matlab

I cannot launch it by any other way. Is there anyway I can create custom launcher for it. 
:(

---

### Post by nothingspecial on 2010-10-16
Put the binary (the executable file, the actual program) in /usr/bin

Then you can create a launcher with the command matlab

```
sudo mv Matlab/bin/matlab /usr/bin/
```

---

### Post by lindsay7 on 2010-10-16
Right click anywhere on your Desktop and find the create launcher button.

---

### Post by James78 on 2010-10-16
> **nothingspecial said:**
> Put the binary (the executable file, the actual program) in /usr/bin

Then you can create a launcher with the command matlab

```
sudo mv Matlab/bin/matlab /usr/bin/
```
Or you could just add a environment variable to your PATH pointing to Matlab/bin. Or even creating a soft link from Matlab/bin/matlab to /usr/bin/matlab (I prefer soft links, that way if you update the software, the other files are updated too)

P.S.
```
sudo ln -s Matlab/bin/matlab /usr/bin
```

---

