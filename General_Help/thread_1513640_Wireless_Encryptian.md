---
title: "Wireless Encryptian"
date: 2010-06-19
forum: General Help
---

### Post by Nick_Jinn on 2010-06-19
Hello.

I currently have an open wireless connection by Lynksys. My card is an older Netgear, no longer supported but works with Linux.

I can connect to the internet, but I want to set up security and set a new password in linux/ubuntu/mint without having the windows program that it came with for easy installation and setting up the wireless network.

Currently it is not password protected but I want it to be.


I have tried google but some of the instructions lose me when they tell me to type in some long hex code that I do not have in front of me. I need somebody to dumb it down and tell me how to make my wireless network password protected and then allow me to add computers or allow anyone to connect who has the password.

---

### Post by Miljet on 2010-06-19
You should be able to access the router setup by opening Firefox and typing "192.168.1.1" in the URL box and pressing Enter.

But you really need to read the user's guide to understand what settings to change. If you have the installation CD that came with the router, look on the CD for a file called "User's Guide.Ink.pdf."

---

### Post by Mark Phelps on 2010-06-20
You're not going to be able to change the wireless configuration while connected via wireless for obvious reasons ... You will have to connect via a wired connection and THEN change the wireless configuration.

As to the IP address of your router, if you're using DHCP on your router to assign an address to your PC, simply look at your PC's IP address.  If it's, for example, 196.168.0.100, your router is probably 192.168.0.1; if yours is 196.168.1.100, your router is probably 192.168.1.1.

Notice that the first three sets of numbers (known as "octets") of your client IP address are the same as the router's IP address.

Enter the router's IP address in your web browser.

When that opens the page, it will most probably ask for a password.  The default, if you haven't set one, is a blank user name and a password of "admin".

Enter that info and click through the tabs and entries until you come to a page for setting wireless security.  That will allow you to select which type (WEP, WPA, WPA2) and to decide the passphrase used for the type.  Make sure you remember the passphrase you assign since you'll need that when you then reconnect your machine via wireless.

---

### Post by Nick_Jinn on 2010-06-20
You people are awesome. I love that you have the patience to help noobs who barely know what they are talking about.

Every now and again I find someone with little patience, but I really appreciate this.


I dont have the disk anymore. Thats the problem and the reason i was hoping I could do it from inside linux.

Thans. If i get stumped i will be back.

---

