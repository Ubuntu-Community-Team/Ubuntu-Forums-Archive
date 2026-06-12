---
title: "Cisco Packet Tracer can't be found"
date: 2011-07-24
forum: General Help
---

### Post by simsym05 on 2011-07-24
Good evening,

i installed Packet Tracer for cisco lab, i used it, next day i opened my lap top but i can't find it on Application >>internet,

i wanted to install it again but i have the lessage that is alreadyinstalled,

Can you explain to me please:

1-in wich directory it is installed?
2-how can i lanch any application from my terminal (if it is not ubuntu application how can i put it in the terminal file)


Thanks in advance.
Samy

---

### Post by uRock on 2011-07-24
How did you install it?

If installed by running ```
chmod +x Packet*.bin
``` then, ```
sudo ./Packet*.bin
``` then it should be listed under Applications> Internet.

Did it completely install or did it give you an error message?

---

### Post by uRock on 2011-07-24
Running the following in the terminal should start Packet Tracer ```
/usr/local/PacketTracer5/packettracer
```

---

### Post by simsym05 on 2011-07-24
> **uRock said:**
> Running the following in the terminal should start Packet Tracer ```
/usr/local/PacketTracer5/packettracer
```



Thank you very much uRock, it is working, but can you explain to me how  it working with the terminal to lanch any application please?

---

### Post by uRock on 2011-07-24
> **simsym05 said:**
> Thank you very much uRock, it is working, but can you explain to me how  it working with the terminal to lanch any application please?

Yes, If you are using 10.10 or older, then skip to step one, if you are using 11.04 you will need to log out and select to log in with "Classic Ubuntu", which is the only way I know of to add this to the menu selection.

1. Right click the menu on the top panel, then select Edit Menus, then,

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=198320&stc=1&d=1311543868[/IMG]

2. Navigate to where you want to create the launcher, then click the New Item button, then,

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=198322&stc=1&d=1311543868[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=198323&stc=1&d=1311543868[/IMG]

3. Leave the drop down menu set at "Application", then,

4. In the **Name** field enter the name you want to give the launcher, then,

5. In the **Command** field enter **/usr/local/PacketTracer5/packettracer**, then,

6. To select the image to use for the icon, select the icon to the left of the text fields and navigate it to **/usr/local/PacketTracer5/art** and select **app.png**, then,

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=198324&stc=1&d=1311543868[/IMG]

7. Click the OK button and you should now have the item listed in your selected menu. If using Unity, then you will need to log out and select to use Unity and you should be able to bring up Packet Tracer by typing that in the search field, then you can add it to the Unity launcher if you wish.

---

### Post by simsym05 on 2011-07-24
uRock,

It is really a helpful, esier answer i never had;

Thank you very much, it is very professional; THANK YOU :):):)

---

### Post by uRock on 2011-07-24
You're very welcome. :P

---

