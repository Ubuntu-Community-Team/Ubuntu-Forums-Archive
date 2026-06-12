---
title: "Help with exe file cannot  open"
date: 2011-05-04
forum: General Help
---

### Post by shaun67 on 2011-05-04
Hi i am using ubuntu 10.04  with opera browser ..

I tried to open a program that i have on disc that i use ( wiring diagrams) 

Now i did originally install it using wine to my  C drive , but since changing from firefox to opera i could not open the EXE  file with wine ,i use to right click and then open with wine.

Now it will not work at all..I un-installed it then reinstalled the program but again nothing..

Is there a way round this without using virtual box (do not like that program) and anyway like i said it use to work flawlessly before.

Thanks

---

### Post by Nerotriple6 on 2011-05-04
Did you right click it and mark it as **executable** in the *permissions tab* inside *properties*?

---

### Post by shaun67 on 2011-05-04
> **Nerotriple6 said:**
> Did you right click it and mark it as **executable** in the *permissions tab* inside *properties*?

Hi Yes i checked it ...I love ubuntu but am seriously thinking of going back to windows (even though i hate it :( ) i need this program to work as i am a white goods engineer ...computers  eh lol Cannot understand it because it worked before i updated to  ubuntu 10.04 and changed to opera browser.

I just tried it again and this is what is coming up - Blocked

The file 'file:///home/shaun/.wine/dosdevices/c:/Program%20Files/TDS%202008%20Back%20up%20File/%20SETUP.EXE' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

But exe is ticked when i go to properties..Any help appreciated

Thanks

---

### Post by Nerotriple6 on 2011-05-04
LOL :tongue:

So nothing happens when you try to run it? Mind me asking what program it is? You don't have to answer but you could make a Google search with that program and Wine.

The file /path/to/your/file/SETUP.EXE ..is this the executable for the program (the launcher itself) or do you think it's launched by the program? If you trust it, mark it as exec and try again?
(You may have to mark it as superuser, I think?)

---

### Post by decrepit on 2011-05-04
I had a similar problem when I first installed 10.04,but now it works OK, I have no idea why it came good, but I suspect updates.
So the question is, have you applied all the updates?

---

### Post by shaun67 on 2011-05-04
> **Nerotriple6 said:**
> LOL :tongue:

So nothing happens when you try to run it? Mind me asking what program it is? You don't have to answer but you could make a Google search with that program and Wine.

The file /path/to/your/file/SETUP.EXE ..is this the executable for the program (the launcher itself) or do you think it's launched by the program? If you trust it, mark it as exec and try again?
(You may have to mark it as superuser, I think?)

Hi the program is a TDS ( a technical disc that has all wiring diagrams for washing machines,dryers ,dishwashers  including service manuals for engineers) ..

When it worked all i did was go to  my C drive under wine double click the TDS folder then double click the EXE file and it would launch the program..It is a program i can use even if not connected to the internet ,but it will do nothing now :(  not sure where to go from here ..i wiped windows off this pc  cause i hate windows but need this program to work..Computers is not my strongest point lol on linux systems.

---

### Post by shaun67 on 2011-05-04
Well i have managed to get it working ..i uninstalled wine then reinstalled it and rebooted  and it now works :D

Now when i open the program it opens fine but i cannot get it to full screen  ..Any ideas ?? clicking on full screen does nothing.

---

### Post by shaun67 on 2011-05-04
No one any idea how i can get full screen ??):P

---

