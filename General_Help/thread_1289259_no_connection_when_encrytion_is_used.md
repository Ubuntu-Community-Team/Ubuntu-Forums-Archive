---
title: "no connection when encrytion is used"
date: 2009-10-12
forum: General Help
---

### Post by rastro123 on 2009-10-12
Hi
Even when I put the code in my pc will not connect if there is encryption turned on. I have tried it both in ubuntu and windows and backtrack. If there is no encrytion it connects fine but I generally use friends connections as I dont have my own internet and they dont want to turn the encrytion off. It has been sugested that the wireless card may be up the juntion. Has anyone else had a similar problem and how did they fix it? Many thanks if anyone has any ideas. My laptop is a hp dv5 1118es and the wireless is broadcom 4312.

---

### Post by P4man on 2009-10-13
are you using the restricted driver ? System > adminstration > hardware driver.

If updating your system doesnt help, you could consider using ndiswrapper 
with the windows drivers for your wifi

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Another thing I vaguely remember reading is when you use WEP or WPA with a "too short" key, that it doesn't work on linux.

---

### Post by rastro123 on 2009-10-14
Thanks but I've tried it with windows also. I installed windows 7 just to try to cover all angles, but it still wont connect if encryption is on and I put the password in.

---

### Post by P4man on 2009-10-14
Then I suspect its user error, and not a software issue. Are you sure you are not confusing the passphrase with the key ? Which sort of encryption are you using, WPA, WPA2 or WEP ?  Id say double or triple check the passphrase (or key). Its not unheard of to have problems with WPA on some wifi cards on ubuntu, but Ive never heard of one fail on every major OS.

---

### Post by rastro123 on 2009-10-14
hi, I've actually got windows 7 on with ubuntu and a small partition with back track4 installed. None of them connect with encryption enabled. I've been sat next to a guy with windows on his pc, he put the password in and straight away he was on line. As for me, not so. I tried upper case, lower case, with spaces between the words and without, I also tried un installing wicd and went back to network manager. Its very frustrating. I've just written an email to broadcom, but I dont know if they will deal with an end user. I dont really know what else I can do. I didn't know a wireless card can go wrong in such a fashion. One would have thought that it either works or not, full stop. Thanks anyway mate.

---

### Post by P4man on 2009-10-14
dont expect broadcom to reply, you should contact HP.
As a workaround, consider buying a cheapo USB wifi stick. They can be had for around €10-15 if you look around, just google the brand/type beforehand to be sure its supported by ubuntu.

---

### Post by rastro123 on 2009-10-14
I was also thinking that might be the answer. I have one ordered and am waiting for the post. Could you tell me pls, if I right click under the wireless symbol at the top of the screen, click quit, and then plug the usb adapter in, is this how one does it? It seems to me that I should disable the pc's internal wireless before I try to use the usb one. Thanks.

---

### Post by P4man on 2009-10-14
Not sure, but I think you'll just see both wireless cards in network manager, just like you'll see wired and wireless now. Find out :)

edit: tried it by plugging in a wifi stick in my laptop. As you can see, it works just fine:

---

