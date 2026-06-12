---
title: "sudo service cups restart"
date: 2010-08-11
forum: General Help
---

### Post by garethfoxwilliams on 2010-08-11
On the PC used by all members of the family, ( running Lucid)  the CUPS service often does not start at boot-up - hence no printer appears.

I have instructed them in the use of the terminal command "sudo service cups restart", but I would like to either put this into an executable script they can run from an icon, or alternatively find where the cups service/app is run from in the filesystem, so I can create an application launcher for them.

I'm a relative noob, so I have drawn a blank on both of the above so far.

Hope someone can help with either ( or both ) solutions.

---

### Post by Morbius1 on 2010-08-11
Ubuntu 10.04 has introduced two different bugs that affect how / when cups starts but only one seems to affect you.

There are a lot of interrelated services that are dependent on the network being up before they can be started successfully. To ensure cups starts after the network is up:

Create a script:[FONT=sans-serif]
[/FONT]```
[FONT=sans-serif]gksu gedit /etc/network/if-up.d/cups [/FONT]
```With this content:
```
#!/bin/sh
service  cups restart 
```Save the file and make it executable:
```
sudo chmod +x /etc/network/if-up.d/cups 
```Reboot

Once set it should require no further intervention by the user.

---

### Post by garethfoxwilliams on 2010-08-11
Thanks for that.

So, as I understand it, your script runs automatically on boot to start the cups service if it's not already up and running at that point. It waits to see if the network is up first?

Have I understood correctly?

Cheers

Gareth

---

### Post by Morbius1 on 2010-08-11
> So, as I understand it, your script runs automatically on boot to start  the cups service if it's not already up and running at that point. It  waits to see if the network is up first?

Have I understood correctly?Exactly. Any script placed in /etc/network/if-up.d will execute only after the network is up.

---

### Post by garethfoxwilliams on 2010-08-11
BIG THANKS!!

All worked fine in the end

Unless I typed something wrong, then,

sudo chmod +x /etc/network/if-up.d/cups
.....................didn't make the text file executable. However, I used a terminal and used....

gksudo nautilus

... to browse to the file and tick the box on the permissions tab, which fixed it.

---

### Post by Morbius1 on 2010-08-11
Hmm ......

I cut and pasted my instructions into a terminal and the chmod +x changed it to executable. 

```
-rw-r--r-- 1 root root    6 2010-08-11 12:41 cups
-rwxr-xr-x 1 root root    6 2010-08-11 12:41 cups

```

Oh well at least you worked around the issue and it worked.

---

### Post by riyasmp on 2010-08-31
thanks a lot guys

it has fixed my printer too.

with regards

---

