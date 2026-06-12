---
title: "Command Scripting"
date: 2009-10-05
forum: General Help
---

### Post by EdGy28376 on 2009-10-05
Being a newb to Ubuntu and enjoying it I am on the qwest to make things easier. I run a GUI client widget. In order for it to run I have to start it by running the following commands using a the root terminal:

cd /opt/rocket/netcure/bin
xhost +
csh
chmod +x widget_client.csh
./widge_client.csh
exit

Now I did try scripting and saving with the name widget, in the etc directory, below is what was in the file:

#! /bin/bash
cd /opt/rocket/netcure/bin
xhost +
csh
chmod +x netcure_client.csh
./netcure_client.csh
exit

However it never fails to start. I edited the sudoers visudo  and add the following line to the bottom:

username ALL = NOPASSWD: /etc/widget

Can some explain to me what I am missing? 

Edgy to get this right!

---

### Post by scragar on 2009-10-05
```
#! /bin/bash
cd /opt/rocket/netcure/bin
xhost +
csh netcure_client.csh
exit
```
Try that.

---

### Post by StuartN on 2009-10-05
> **scragar said:**
> ```
#! /bin/bash
cd /opt/rocket/netcure/bin
xhost +
csh netcure_client.csh
exit
```
Try that.

Assuming that you have installed **csh** wouldn't you ensure your script begins with **#! /bin/csh** and just execute it, as you would a bash script?

---

### Post by EdGy28376 on 2009-10-05
So rather than #! /etc/bash it should start with #! /etc/csh or look like this;

#! /bin/csh
cd /opt/rocket/netcure/bin
xhost +
csh netcure_client.csh
exit

---

### Post by StuartN on 2009-10-06
I was assuming that **netcure_client.csh** was a c-shell script, which would start with #! /bin/csh, and be called in the same way as any bash-shell script. I don't know if you need to explicitly change directory before running the script, and you could add **xhost +** to it.

If this assumption is correct then a menu entry or desktop launcher to /opt/rocket/netcure/bin/netcure_client.csh will just execute, without having to write a script to launch a script.

---

### Post by EdGy28376 on 2009-10-06
I added the xhost + to the C Shell scrpit and I can run it from the _root terminal_. I tried creating a launcher for it but fails to start it. The command that I have it calling is:

sudo su ./opt/rocket/netcure/bin/netcure_client.csh

What am I missing?

Thank you Stuart you were right.

---

### Post by StuartN on 2009-10-06
> **EdGy28376 said:**
> sudo su ./opt/rocket/netcure/bin/netcure_client.csh

I am not sure this is what you mean, but if you gksudo instead of sudo then it will open up a password dialogue - sudo would display a password if you selected "Run in terminal".

So your launcher will be:

```
gksudo ./opt/rocket/netcure/bin/netcure_client.csh
```

Edit: (Just noticed you have "sudo su" and not just "sudo", not sure why)

---

### Post by EdGy28376 on 2009-10-06
Thank you StuartN I got it working finally. I ended up removing the '.' as it was not needed. So the launcher command looks like this;

gksudo  /opt/rocket/netcure/bin/netcure_client.csh

with running application in terminal window.

Thanks again!

---

