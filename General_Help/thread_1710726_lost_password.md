---
title: "lost password"
date: 2011-03-20
forum: General Help
---

### Post by lumaja on 2011-03-20
[FONT=Times New Roman][SIZE=3]To avoid Ubuntu login with password I tried “User and Groups”,[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]**On Password:** Asked in login, I enter my password and then click “Change” new window come up with **Current password:** enter mine, **New Password:**and [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]**Confirmation: **I left the both boxes empty, I tick **Don’t ask for password on login** this was my aim. On booting Ubuntu come up with my “Username” on clicking it dint reboot.[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Went to [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3]www.psychocats.net[/SIZE][/FONT]]("http://www.psychocats.net/")[FONT=Times New Roman][SIZE=3] but **shadow **file has an **X** on it and can’t be open.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Please help to recover from this[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Thank you[/SIZE][/FONT]

---

### Post by blueridgedog on 2011-03-20
If you boot into recovery mode, you can reset your password:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by falko on 2011-03-20
This might help as well: [http://www.howtoforge.com/how-to-reset-a-forgotten-root-password-with-knoppix](http://www.howtoforge.com/how-to-reset-a-forgotten-root-password-with-knoppix)

---

### Post by lumaja on 2011-03-21
[FONT=Times New Roman][SIZE=3]I follow the instructions in [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3][COLOR=#800080]www.psychocats.net/ubuntu/resetpassword[/COLOR][/SIZE][/FONT]]("http://www.psychocats.net/ubuntu/resetpassword")[FONT=Times New Roman][SIZE=3] but no success, my [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ubuntu is10.04 LTS, booting with live CD and getting the menu option F4 “*There is no dedicated rescue mode on this disc”, *I don’t know how get into* recovery mode *so Iboot the live CD and follow the video found my hard drive as a number – **09a0b3c7-3639-4fa8-b21d-ee37feadea3 **carry onfollowing the instructionthe file *shadow* as the correct entry of **U6My0w0jraho **I saved the fileand reboot.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The screen with username come and click it, a warning come up.[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]**Could not update ICE authority file /home/luis/.ICE authority** – CLOSE.[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]Next screen: **There is a problem with configuration server (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)** – CLOSE.[/SIZE][/FONT]
**[FONT=Times New Roman][SIZE=3]Nautilus could not create the following required folders: /home/luis/Desktop,/home/luis.nautilus.[/SIZE][/FONT]**
[SIZE=3][FONT=Times New Roman]I can’t download Knoppix because the file is to big for my cap.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Hopping these can be fixed.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Regards[/FONT][/SIZE]

---

### Post by jerome1232 on 2011-04-14
Why are you directly editing the shadow file?

You shouldn't be doing that. Use the utilities given to you to change passwords like passwd.

---

