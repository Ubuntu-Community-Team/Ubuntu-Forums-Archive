---
title: "problem in emptying trash"
date: 2009-08-15
forum: General Help
---

### Post by tprayush on 2009-08-15
hey guys..yesterday i deleted some data from my pen drive... i  tried to empty the trash
......all the files were deleted except the two viz. "Desktop.ini" ,"zaxqsw.exe" !!!
the error it gives is : "permission denied."

it tried "sudo nautilus" to have the superuser permission...but still it didn't work!!!!!!

please help me!!!!!

---

### Post by yeeeev on 2009-08-15
Try the following:
cd ~/.local/share/Trash/files
Now you should be in the Trash folder. You can verify that by running "ls" and seeing the two files.
Now you can run:
pwd
And after seeing that the output is "/home/YOURUSERNAME/.local.share/Trash/files" you can run:
sudo rm *

Good luck!

---

### Post by tprayush on 2009-08-15
thanks a lot yeeev!!!!!
sorry for troubling again ....i've another query......
every time i start ubuntu......"terminal & mozila firfox"  automatically starts..
how can i stop this.....cud u please help me!!!!!

---

### Post by blueridgedog on 2009-08-15
Are they set to start under system -> preferences -> sessions on the "startup programs" tab, or on the "options" tab, is it checked to recall running programs?

---

### Post by yeeeev on 2009-08-15
I can think of 2 options there:
* You have set to the startup at the beginning of a session. That can be controlled through the "Preferences->startup applications->Startup programs" GUI.
* You have set up session saving (which is a great feature IMO) and you always have a terminal & FF open when you turn off a session. Session saving can be turned off through the "Preferences->startup applications->Options" GUI.

---

### Post by tprayush on 2009-08-15
sorry for above....!!!!!!
they are not in the startup programs & and it is also unchecked to "automatically remember session" still they start automatically!!!

---

### Post by michy99 on 2009-08-15
Here is the solution:

Make sure 'automatically remember session' IS checked.

Close out all programs.

Restart computer.

Now, nothing should open on start-up. Go back and UNCHECK 'automatically remember session'.

---

### Post by tprayush on 2009-08-15
thanks michy..it worked perfectly!!!!

---

