---
title: "Apache wont work for external connections"
date: 2006-02-16
forum: General Help
---

### Post by TFleck on 2006-02-16
I have apache2 installed here, and it works fine when I connect locally (with localhost or my IP).
But when I try connecting from an external PC, the browsers says it cant connect to my server.
I searched the documentation, but couldn't find anything about it. The apache2.conf file doesn't look like have somethink to do with it.
Can you help me?

---

### Post by psusi on 2006-02-16
By "external PC" do you mean another computer on your network that otherwise can reach this one?  

You didn't mess with installing firestarter or another firewall front end did you?

---

### Post by KurtB on 2006-02-16
Hi,

Except of that -and starting from the point that the external PC is not on your home network- have you checked if your ISP doesn't block port 80?

My ISP blocks port 80 (and al ports under 1024) for security reasons and the fact that "residential" users aren't allowed to run any server on their network (FTP, Webserver, ...)

Have you checked this already?

---

### Post by TFleck on 2006-02-16
External PC is one outside my network. I dont have any firewall installed.

I changed the port to 81 and it is working now. 
Dont know why. The port 80 always worked here in other installations.
Is there any problem in using other ports?

---

### Post by KurtB on 2006-02-18
normally you'll have to add the port number after the url when you surf to your webserver if you've set apache to another port than nr 80.

the fact that it works on 81 really means that it's a Firewall or the ISP that blocks port 80

---

