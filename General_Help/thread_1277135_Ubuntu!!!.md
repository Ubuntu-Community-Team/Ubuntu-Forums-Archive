---
title: "Ubuntu!!!"
date: 2009-09-27
forum: General Help
---

### Post by greenerdeaner on 2009-09-27
Hey all

Here's my first post, it's an emergency to get internet in time so I apologize in advance if there is a thread about this already..

Long story short I have to send in my daily driver (mac) and currently have to use a crappy old pc. I deleted windows, now running on ubuntu, but I'm having problems connecting to the internet.

The first time I tried to connect to my apartment wifi it worked fine for 15 minutes, then disconnected. Now, when I try to connect it never works.

The main problem is that every time I try to connect, I enter the WEP password...then a message comes up asking for the password again. Automatically there's a really long password that the computer thinks is the default, but it is an incorrect password.

So basically the computer is editing my password to the long (wrong) password...which explains why it won't connect, but how do I fix this?


thanks in advance
-GD

---

### Post by greenerdeaner on 2009-09-28
bump

---

### Post by ram2500 on 2009-09-28
I don't think your computer is at fault for editing your WEP password:) but may I ask you, does the apartment regularly change its WEP keys via manually or automatically? This has nothing to do with your problem much, but is it broadcasting its SSID or is it not? You might be inadvertently using a different network. I am not sure about this particular network, as on my Wi-Fi I had to enter a key once, so I'm thinking that the WEP key is set to expire and change every so often (so that if residents tell outsiders the key, it won't work for long maybe?)

---

### Post by greenerdeaner on 2009-09-28
My router has  WPA2 password lol

---

### Post by marshmallow1304 on 2009-09-28
Right click the network manager (four bars symbol in upper left) and click edit connections.  Go to the Wireless tab and delete the connection that's been giving you trouble.  Close out of that, then right-click the network manager again and uncheck "Enable wireless".  Then right-click and re-check "Enable wireless".  Hopefully, it will find the network again and it won't prompt every time.


I believe it shows a bunch of characters because it encrypts your password.

---

### Post by fluffman86 on 2009-09-28
On your network manager icon (near the clock), right click and click edit connections.  Then flip to the wireless tab, click on your apartment wireless access point, and click delete.  Then try to connect again.

edit: way to be like 3 seconds faster, marshmallow1304 :P

---

### Post by greenerdeaner on 2009-09-28
I already tried that ^   thanks though

every time I delete it from the list and try again I have the same problem.....it tries to connect for a minute or two, then the menu comes up saying "authentication require by wireless network" with the insanely long incorrect password

---

### Post by fluffman86 on 2009-09-28
Is it possible to change the wep key and try something else?  Or preferably disable wireless encryption altogether temporarily?  Or maybe try WPA?

---

### Post by greenerdeaner on 2009-09-28
> **fluffman86 said:**
> Is it possible to change the wep key and try something else?  Or preferably disable wireless encryption altogether temporarily?  Or maybe try WPA?

already tried all that, except disabling it and plugging it in directly

how do i disable the encryption?

---

### Post by Bigneil on 2009-09-28
i know this doesn't help with your wireless, but if you are in a screaming hurry to get a connection can't you just plug in an ethernet cable, do what you have to do, then work on the wreless problem at a more relaxed pace????

---

### Post by greenerdeaner on 2009-09-28
> **Bigneil said:**
> i know this doesn't help with your wireless, but if you are in a screaming hurry to get a connection can't you just plug in an ethernet cable, do what you have to do, then work on the wreless problem at a more relaxed pace????

yeah, I'm getting a long cable tomorrow

I was hoping to get the wireless problem fixed tonight so i could drop of my mac tomorrow to get fixed before midterms

---

### Post by fluffman86 on 2009-09-28
Well, assuming you actually have the admin password for your router, you should be able to log into it, look for your wireless settings or encryption settings, and change the wireless encryption from "WEP" to "none."  Then if you still can't connect, there's a problem with your wireless adapter.

---

### Post by 3rdalbum on 2009-09-28
The "big long password that is wrong" is the WEP key. Your passphrase gets converted into a WEP key so it can be used to encrypt traffic to your router. The passphrase is not stored at any point in time after the conversion, so if there are errors connecting to the network, the key will be displayed in the "Enter the key" dialog box.

---

