---
title: "VBox Shared folder both way?"
date: 2010-05-26
forum: General Help
---

### Post by mqlmql on 2010-05-26
- I have ubuntu installed, and win7 is installed using vbox.

- I know how to set shared folder, so win7 can access the folder in ubuntu.

- I need to have an access to certain folder in win7 from ubuntu.

How can I do that?
It is not about samba, right?

---

### Post by obscurant1st on 2010-05-26
I cannot say its nothing about samba.
anyway just change the VBox network to host only adapter.
now in Win7 check your ipaddress.
Now in ubuntu in places select connect to server, from panel.
now enter the ipaddress you got from win7. and select service type as windows share.
now enter, thats it if you have shared something or some folder in win7 you can access it form ubuntu!. you may have to wait for some time to get the window open with the shares.

---

### Post by mqlmql on 2010-05-26
Thank you. This is what I wanted.. It works...

---

### Post by mqlmql on 2010-05-26
Hold on...Here is another problem.
Win 7 can't connect to internet.

---

### Post by mqlmql on 2010-05-26
I just found out bridged network makes both internet and shared folder connection.

thanks..

---

### Post by obscurant1st on 2010-05-26
So now as it is solved you can mark it as solved. :)

---

