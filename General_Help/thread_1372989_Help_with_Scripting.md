---
title: "Help with Scripting?"
date: 2010-01-05
forum: General Help
---

### Post by WeAreTheSiNs on 2010-01-05
Hello all,

i just installed Ubuntu the other day and since i don't currently have Internet i'm using Wvdial to use the Internet off of my cell phone.
so every time i want to connect it i have to open up Terminal and type

```
sudo wvdialconf
```

And then:

```
sudo wvdial hsdpa
```

So is there and way to put this into a batch? file so all i have to do is open it?

And it would also be great if i didn't have to enter my password as well!

---

### Post by Cheesemill on 2010-01-05
Open up a text editor and type the following:

```
#!/bin/bash
sudo wvdialconf
sudo wvdial hsdpa

```Save this somewhere as dial.sh (I have a folder called Scripts in my home folder) then right-click on it and select Properties. Go to the permissions tab and mark 'Execute'.

You now have your script that will run when you double click on it.

To prevent it asking for your password you can make changes to your sudoers file, do this by opening a terminal and typing 'sudo visudo' and add the following to the end of the file:

```
user ALL=(ALL)NOPASSWD:/usr/bin/wvdialconf,/usr/bin/wvdial
```Replacing user with your username. Save the file and exit (CTRL+O then CTRL+X) and your user can now run those commands without having to type your password.

If you want you can now place a shortcut to the script on your desktop.

---

### Post by zine92 on 2010-01-05
Sorry, but i am new to Ubuntu. Anyway to put those into a sh script just ```
sudo wvdialconf
sudo wvdial hdspa
```
Just put these 2 codes into your normal text file.
And here save the file on desktop.
Rename the file to something like Name_You_Want.sh
Note the .sh extension. And then go double click then press run in terminal. Not sure if it works but hope it helps.

---

### Post by audiomick on 2010-01-05
Hi
I like cheesmill's suggestion.
Having done that, instead of a shortcut on your desktop (my desktop has absolutely nothing on it, because I can never find icons...) you could put a starter in the panel.
Right click on an empty part of the panel
choose "add to panel" then double click "userdefined application starter"
use the search button next to the "command" entry field to point to your script.

---

### Post by WeAreTheSiNs on 2010-01-05
Thanks Cheesemill, it worked like a charm!:guitar:

---

