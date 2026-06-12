---
title: "Default keyring password for WEP not working."
date: 2009-09-25
forum: General Help
---

### Post by bvanderwaal on 2009-09-25
I am trying to get my wireless network working but every time it asks me for the WEP key and I type it in another box pops up asking for my default keyring password. I tried my WEP password (obviosly didn't work) and I tried my current account password. After reading around a lot on the internet I found out that it is asking because I have changed my account password in the past. So when I tried to connect again I instead typed in my old password....still nothing. The password entry box just keeps popping up. 

I read around on the forums and following some directions, went to "Passwords and Encryption" > Passwords > and Password:login. I tried Unlock at first but again, same problem as trying to type in the WEP password. I then tried the Password change, and changed it to my current account password, but nothing. As I am getting a little desperate I changed my account password back to what it was before but alas, I am still having the same problem. 

After I type in my WEP password and hit connect the box still pops up for my "default keyring password" and sometimes if I just close out that box it will let me connect for a few min. 

My theories are that my poor signal strength is causing it to take the password but then right away disconnect and reconnect requiring me to type in my wep/keyring passwords again (my be impossible but hell who knows).

From what I have read it seems the only sure fire way to get my login and keyring passwords back to normal and remove this problem is to reinstall Ubuntu but I have about 130Gb of programs and files on the computer already and really dont want to install them over again. 

So any ideas? I don't know what other password the computer could possibly want. Is there some master password I could use, or root account (I don't know much about that but I know is is the default admin account)? For now I am stuck without internet so I could really use some help.

---

### Post by Commander_Keen on 2009-09-25
Is is possible that the first box you need to type in your system pwd and then the second box is your network pwd?

---

### Post by bvanderwaal on 2009-09-25
The first box is labeled with my network name the box is labeled WEP. the Second one says something like Networkmanager applet /usr/...... is trying to access default keyring but it is locked. (im not at my computer now so i don't know exactly what it says)and I cant do anything on the computer until I hit "deny" or close out the box with the "X".

---

### Post by philinux on 2009-09-25
Got to your home folder and press ctrl H to show the hidden files.

Navigate to .gnome2/keyrings

Delete any file in there then logout and login.

When connecting to wireless it should ask you for a keyring password, Leave it blank.

---

