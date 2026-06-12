---
title: "SSH Web connection"
date: 2011-10-16
forum: General Help
---

### Post by LatencyRemix on 2011-10-16
I've set up the standard SSH local connection, but i can't figure out how to connect to it from my static web ip :S  When i do, it comes up to login username, but the password gets rejected.  

Is there a file somewhere id have to edit to make it able to accept web connections?

---

### Post by LatencyRemix on 2011-10-19
no one has any suggestions?

---

### Post by Bmonsterboy on 2011-10-19
Ok, Be sure you have checked off this list:

1. Set up SSH server on server side.
2. Port Forwarding for SSH server side.
3. Get WAN for server.
4. Use Client software to connect to server.
    Be sure you have configured your client software to use SSH.
5. Connect. Be sure to use your username and pass for the Server.

---

### Post by collisionystm on 2011-10-19
> **LatencyRemix said:**
> I've set up the standard SSH local connection, but i can't figure out how to connect to it from my static web ip :S  When i do, it comes up to login username, but the password gets rejected.  

Is there a file somewhere id have to edit to make it able to accept web connections?

No file. Did you enable port forwarding in your router to point port 22 to your server? 

What kind of router do you have? How is your system plugged into the "internet"

---

### Post by LatencyRemix on 2011-10-20
Adding the port 22 in the modem seems to have done the trick.  Thanks for the help.

Topic can be marked closed

---

### Post by Bmonsterboy on 2011-10-20
You can do that.

---

