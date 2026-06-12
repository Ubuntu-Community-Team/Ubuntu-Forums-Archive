---
title: "Multi-App Launcher"
date: 2011-06-10
forum: General Help
---

### Post by TheAJGman on 2011-06-10
Hi I'm looking for a gui multi app launcher so i can click one program and open 20 different ones from that one. I would also like something like this for my Win7 pc.

---

### Post by blueridgedog on 2011-06-10
You can create a script that will launch all the programs you want, then run the script with a single launcher.

Make a file with gedit, with the following and save it in your home directory.  Call it anything you want, but for this example, I will call it multilaunch.sh.

```
gedit multilaunch.sh
```

Add:


```
#!/bin/bash
program1 &
program2 &
program2 &
```

Make the file executable:

```
chmod u+x /home/USER/multilaunch.sh
```

Create a launcher to run the script...System -> Preferences -> Startup Applications, then click add, under name, call it whatever you want, then in command put in /home/USER/multilauch.sh.

Change USER to your user account.

---

