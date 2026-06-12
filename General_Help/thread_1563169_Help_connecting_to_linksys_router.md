---
title: "Help connecting to linksys router"
date: 2010-08-28
forum: General Help
---

### Post by Rorin on 2010-08-28
okay, today, i downloaded Ubuntu, after installing, i went on it, and under the wireless connections available, all it said was 'disconnected'
My router connects fine when on windows 7 (What i'm using to write this)
And i was wondering if there was a way to get it to connect.
Thank you in advance for the help.

---

### Post by 3Miro on 2010-08-28
Step 1: left-click on the wireless icon and look for available networks. (if left doesn't work, try right). If you see your network, select it. If not, go to step 2.

Step 2: Go to System -> Administration -> Hardware Drivers and check to see if your wireless card needs a proprietary driver. Activate an appropriate driver (if any), reboot and try Step 1 again.

Post back if this doesn't help.

PS some laptops have a button to disconnect the wireless, make sure you have not accidentally pressed it.

---

### Post by Rorin on 2010-08-28
> **3Miro said:**
> Step 1: left-click on the wireless icon and look for available networks. (if left doesn't work, try right). If you see your network, select it. If not, go to step 2.

Step 2: Go to System -> Administration -> Hardware Drivers and check to see if your wireless card needs a proprietary driver. Activate an appropriate driver (if any), reboot and try Step 1 again.

Post back if this doesn't help.

PS some laptops have a button to disconnect the wireless, make sure you have not accidentally pressed it.
Thanks for the help,
Unfortunately, as for step one, It doesn't show any networks, simply says 'disconnected'
How will i know if it needs a proprietary driver?
and I didn't press the button, that was the first thing i checked.

---

### Post by Rorin on 2010-08-28
Okay, so i did what you said for step 2, but it just said 'no propriarety drivers are enabled' and had a blank box under that with nothing in it.

---

### Post by 3Miro on 2010-08-28
Left-click should say: connected/disconnected for wired and wireless and give you a list of available networks. Right-click should let you select "Enable/Disable" for wired and wireless. Make sure everything is the way it is supposed to be (enabled).

As for the proprietary drivers, this can be tricky without a connection. Can you connect with a wire, then go to Systems -> Admin -> Synaptic Package Manager (it will ask for a password) then select Reload -> Mark All Upgrades -> Apply. This will update your system. Then go to the Hardware Manager again, if your system requires special drivers, it will show you a list.

---

### Post by Rorin on 2010-08-28
> **3Miro said:**
> Left-click should say: connected/disconnected for wired and wireless and give you a list of available networks. Right-click should let you select "Enable/Disable" for wired and wireless. Make sure everything is the way it is supposed to be (enabled).

As for the proprietary drivers, this can be tricky without a connection. Can you connect with a wire, then go to Systems -> Admin -> Synaptic Package Manager (it will ask for a password) then select Reload -> Mark All Upgrades -> Apply. This will update your system. Then go to the Hardware Manager again, if your system requires special drivers, it will show you a list.
I cannot connect with a wire, at the moment.
But i'll check if it's enabled/disabled
will post here if That doesn't work

---

### Post by Rorin on 2010-08-28
> **3Miro said:**
> Left-click should say: connected/disconnected for wired and wireless and give you a list of available networks. Right-click should let you select "Enable/Disable" for wired and wireless. Make sure everything is the way it is supposed to be (enabled).

As for the proprietary drivers, this can be tricky without a connection. Can you connect with a wire, then go to Systems -> Admin -> Synaptic Package Manager (it will ask for a password) then select Reload -> Mark All Upgrades -> Apply. This will update your system. Then go to the Hardware Manager again, if your system requires special drivers, it will show you a list.
I cannot connect with a wire, at the moment.
But i'll check if it's enabled/disabled
will post here if That doesn't work

---

### Post by Rorin on 2010-08-28
They ARE enabled, and it still doesn't show any networks, just says 'disconnected'

---

### Post by 3Miro on 2010-08-28
To do it without a wire, you need to find out exactly what kind of video card you have, download a bunch of packages on a flash-drive, read on a bunch of settings, install the driver manually. This is complicated and if there is an easier way, I don't know it.

My advice is to find a wire and use that just to install the updates and driver. This is what I have done several times on my laptop.

---

### Post by Rorin on 2010-08-28
> **3Miro said:**
> To do it without a wire, you need to find out exactly what kind of video card you have, download a bunch of packages on a flash-drive, read on a bunch of settings, install the driver manually. This is complicated and if there is an easier way, I don't know it.

My advice is to find a wire and use that just to install the updates and driver. This is what I have done several times on my laptop.
Okay, I'll get to the wire, though it'll be a hassle =w=
Once i'm there, what do i have to do?

---

### Post by 3Miro on 2010-08-28
Once you have a wired connection:

1. Go to System -> Admin -> Synaptic Package Manager. This will start a software manager program and it will ask for a password.

2. Once in the program, there is a large "Reload" button. Click on it.

3. Once it is done, click "Mark All Upgrades" and then "Apply".

This can take 20 - 30 minutes depending on the connection and the speed of your laptop, but it will update your system with security patches and bugfixes of all kinds. You should reboot at the end.

Then go to System -> Admin -> Hardware Sources and an appropriate driver should be listed.

(technically, if you don't want to wait, once you "Reload" in Synaptic you should be able to close it and go directly to the Hardware Manager and it should work. However, I recommend to make an update first, just in case there is a bugfix specific to your wireless card)

---

### Post by Rorin on 2010-08-28
> **3Miro said:**
> Once you have a wired connection:

1. Go to System -> Admin -> Synaptic Package Manager. This will start a software manager program and it will ask for a password.

2. Once in the program, there is a large "Reload" button. Click on it.

3. Once it is done, click "Mark All Upgrades" and then "Apply".

This can take 20 - 30 minutes depending on the connection and the speed of your laptop, but it will update your system with security patches and bugfixes of all kinds. You should reboot at the end.

Then go to System -> Admin -> Hardware Sources and an appropriate driver should be listed.

(technically, if you don't want to wait, once you "Reload" in Synaptic you should be able to close it and go directly to the Hardware Manager and it should work. However, I recommend to make an update first, just in case there is a bugfix specific to your wireless card)
Thanks, unfortunately, after i connected, it said i was connected, but when trying to connect to the internet, gave me an error = =

---

### Post by Rorin on 2010-08-28
Can anyone help now?
I see it, but when i enter the code, it just loads fora  minute, then tells me to enter the code again
(Yes, i entered the correct code)

---

### Post by 3Miro on 2010-08-28
What kind of error are you getting when you try to connect. Can you open FireFox and go to Google.com? Is the wired network DHCP or does it require static IP (or is it that you are pass the wired phase and you already have a working wireless).

---

