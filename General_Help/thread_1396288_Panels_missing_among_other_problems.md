---
title: "Panels missing among other problems"
date: 2010-02-01
forum: General Help
---

### Post by dporras on 2010-02-01
Hello to everybody, i'm desperate last night i was working with ubuntu and there was a lot of updates in queue, i allowed all the updates and something really bad happened, when i restart the pc both panels were missing, if i try to create a launcher nothing happens i just can create folder and files, that computer is very important in my work because it runs VMWare with the Sugar CRM of my company, we run the GUI via browser, now i can't either open that page and start the CRM, i read that there is a panel file in the usr/bin or someting like that i seek for it but is missing what can i do a really need to fix it ASAP please i need help i would appreciate a solution. And by the way i'm new in the linux world and because of this kind of things ubuntu scares me, i know that ubuntu is very cool but is difficult to manage it

---

### Post by lindsay7 on 2010-02-01
Just go to where the panels were on the top and bottom of the screen and right click the mouse.  You can add the panels back as they were and then right click on the empty panel and choose the "add to panel" option and put whatever you want back on.

---

### Post by blueshiftoverwatch on 2010-02-01
Try this:

Open up the terminal and enter **metacity --replace**. If you can't get to the GUI terminal hit ctrl+alt+F5 to open one up and after the command is typed, ctrl+alt+F7 to close it.

If you went the ctrl+alt+Fkey route, it's probably a good idea to close out of your session before you go back to the GUI. So, when your done just type **exit**.

After this your panel(s) should be back. If you want to make this permanent. Make a plaintext file with the following information:
```
/usr/bin
metacity --replace
```

Place it anywhere (but preferably somewhere out of the way) and than go to System -> Startup Applications -> Add -> and than browse to the path of the script you just made under "command". Now that script should load up every time you log in and you won't have to worry about loosing panels anymore, theoretically.

---

### Post by anthonymint on 2010-02-11
I too also have a problem with my Panels missing. Though I'm not using Ubuntu, I am using Linux Mint 7. I've tried right clicking though the options for panel when I click does NOT open. (nothing happens).

I've also tried Going through XFCE Config, setting ,etc...
Tried searching the web to find a solution, but still haven't been successful.
 Been to Linux Mint Forums but is hard to find a straight answer or any kind of help on there.
Seems people just answer question with a question. (Thinking they're better than everyone else).

So help would be very appreciated. I would love to get this issue resolved as soon as possible. 

Thank you

AnthonyMint

---

