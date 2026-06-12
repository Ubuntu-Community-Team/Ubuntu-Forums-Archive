---
title: "Newbie questions"
date: 2011-06-20
forum: General Help
---

### Post by jake142 on 2011-06-20
Hi,

Im new to Ubuntu and have some questions I hope you can help me with:

1. I have a java app as a runnable jar. I can start it using an *_start.sh Ive created but every time I logout the apps shutdown. I run it as root. I also have a *_stop.sh that I cant get to work. Could you help me with:
a. Run the jar as user called serviceuser (I have tried to use it but the user doesnt have access to my custom logs folder, so the app cant write to that one)
b. Make the app continue to run when I logout
c. Help with my stop shell so that it works.

*_start.sh

start-stop-daemon --start --quiet -b -m -p /var/run/myservice.pid --chuid <username> --exec /usr/bin/java -- -jar myservice.jar

*_stop.sh (doesnt work)

start-stop-daemon --stop  --quiet -p /var/run/myservice.pid

rm -f /var/run/myservice.pid

2. I have svn setup using the root user (client is eclipse so not connected to apache). Can you help me setting up a svnuser to use instead?

3. I have configuered apache to run over HTTPs and created my own cert. How do I export the chat an provide it to the clients that are going to connect to my webapp?

Thanks in advance!

---

### Post by smithk on 2011-06-20
The same way happen to me last time. Good question I also want to know the answer.
If someone reply thanks for it..
Good subject..

---

