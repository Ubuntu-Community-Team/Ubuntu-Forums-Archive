---
title: "Broke KDM"
date: 2006-05-15
forum: General Help
---

### Post by totalnoob on 2006-05-15
Hey I'm using Kubuntu 5.10, I installed Sugar CRM with apache2. Now when I boot it takes me to command line. When trying to run KDM, error failed to locate libXau.so.6... I researched this issue and tried apt-get install libxp6, but thats already present. Thanks.

---

### Post by aysiu on 2006-05-15
What about if you try ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```?

---

### Post by totalnoob on 2006-05-15
those commands don't do anything new.. just says newest version already installed then gives the libXau.so.6 error. apt-get check, looks good. If I boot from the install DVD is there a repair opion? Should I apt-get remove kubuntu-desktop then install?

---

### Post by totalnoob on 2006-05-15
I forgot does it matter that the last thing the boot screen shows is "Starting Apaache2" then goes to command line? I don't think it did that until I tried installing sugarcrm because I needs apache2, mysql

---

### Post by aysiu on 2006-05-15
I don't know if it helps, but *libXau.so.6* lives in /usr/lib. I've uploaded mine to a server. You can try downloading it and copying it to /usr/lib: ```
wget -c http://www.psychocats.net/ubuntu/libXau.so.6.0.0
sudo mv libXau.so.6.0.0 /usr/lib/libXau.so.6.0.0
sudo chown root:root /usr/lib/libXau.so.6.0.0
sudo chmod 644 /usr/lib/libXau.so.6.0.0
sudo ln -s /usr/lib/libXau.so.6.0.0 /usr/lib/libXau.so.6
```

---

### Post by totalnoob on 2006-05-16
I tried all of those steps above... that link didn't work, when I try the mv commands and such I get an error.. don't have permission. I'm in superuser mode. Any other ideas before I wipe the system?

---

### Post by aysiu on 2006-05-16
[QUOTE=totalnoob]I tried all of those steps above... that link didn't work,[/quote] I tested it when I wrote the instructions, and I tested it just now. The link is good. What error do you get? Can you post the output of those commands? > when I try the mv commands and such I get an error.. don't have permission. I'm in superuser mode. Why are you in superuser mode? Just use an ordinary terminal and paste the *sudo* commands. > Any other ideas before I wipe the system? Yes. Open a regular terminal. Paste the commands in exactly as written and then highlight both the commands and the output and copy and paste those back into a post so I can see what went wrong.

---

### Post by totalnoob on 2006-05-16
ok so I got the file from that http site. move file was successful.
sudo chown command error: Chown cannot access /usr/lib/libXau.so.6.0.0: permission denied.
CHMOD - same error. 

I'm not in su mode. I am at whatever "shell" or command line it takes me to when it boots, I'm not sure exactly what it is.... thats the whole problem. I can't copy and paste cause I"m using XP it's the only OS thats usable right now. Thanks.

---

### Post by aysiu on 2006-05-16
I think the fact that *sudo* cannot chown stuff or chmod stuff is a bigger problem than KDM being broken.

When you get the chance, please post exactly what happens. Thanks.

---

### Post by bbarrons on 2006-05-16
aysiu.
aysiu,
 I wanted to drop you a note just and let you know how much I have appreciated your posts. It seems that whenever I have a problem I can search the forum and find the answer. It also seems that most of the threads will have you posting some quality info without any negative feedback.
thanks
Bill

---

### Post by aysiu on 2006-05-16
[QUOTE=bbarrons]aysiu.
aysiu,
 I wanted to drop you a note just and let you know how much I have appreciated your posts. It seems that whenever I have a problem I can search the forum and find the answer. It also seems that most of the threads will have you posting some quality info without any negative feedback.
thanks
Bill[/QUOTE] Thanks, Bill. I just hope it all works out for *totalnoob*.

---

