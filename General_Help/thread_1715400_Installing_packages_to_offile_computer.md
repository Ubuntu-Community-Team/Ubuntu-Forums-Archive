---
title: "Installing packages to offile computer"
date: 2011-03-26
forum: General Help
---

### Post by kop4 on 2011-03-26
Okay so, I have a laptop with internet and ubuntu, and a desktop without internet, and I need to install some pakages on it. I did my research and generated a script to download them from synaptic, but when I double click it, it opens it gedit, when it is supposed to download the packages. What am I doing wrong?


I was using this article--  [https://answers.launchpad.net/ubuntu/+source/synaptic/+question/81941](https://answers.launchpad.net/ubuntu/+source/synaptic/+question/81941)

Thanks

&#1046;aden


edit- title is supposed to say offline...

---

### Post by LostFarmer on 2011-03-26
When the file opens does it look something like below ? "It will have more displayed"
```
#!/bin/sh
wget -c http://us.archive.ubuntu.com/
```

When you click on it , a new small window does not open and give you an option to 'run' or 'open' ?   You did generate the file with Synaptic Package Manager ?

---

### Post by Krytarik on 2011-03-27
You seem to be referring to this procedure:
[https://help.ubuntu.com/community/InstallingSoftware#Use%20the%20Synaptic%20package%20download%20script](https://help.ubuntu.com/community/InstallingSoftware#Use%20the%20Synaptic%20package%20download%20script)

You need to make those script 'executable': 
- right-click at it
- choose "Properties"
- click at the tab "Permissions"
- tick "Allow executing file as program"

Greetings.

---

### Post by kop4 on 2011-03-27
> You need to make those script 'executable': 
- right-click at it
- choose "Properties"
- click at the tab "Permissions"
- tick "Allow executing file as program




Thank you work perfectly

---

