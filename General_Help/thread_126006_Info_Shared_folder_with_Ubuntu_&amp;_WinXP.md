---
title: "Info: Shared folder with Ubuntu &amp; WinXP"
date: 2006-02-05
forum: General Help
---

### Post by BigDeal on 2006-02-05
I want to make a shared folder between 2 pc's in my small lan, one running Ubuntu and the other running WinXP. Please, send me a link with detailed instructions how to do this. Thanks, in advance...

---

### Post by deuz on 2006-02-05
I'm a linux noob, but I think you can do that with samba :) 
sudo apt-get install samba

---

### Post by drpolish on 2006-02-05
yes, im having a problem using samba. One day i was using my network cleanly with no problems when suddenly i lost the ability to connect to my samba servers. So i restarted ubuntu because i couldnt fix it for a week, and reinstalled it. Now i have th same problem. I can access the net and all, and ping the local file servers, but i cannot look at their shares. please help im a linux novice.

EDIT: i just tried using smb:// and connecting, and i can browse the shares in firefox. but i still cannot install a network printer or network share that i can mount - once again, i ask for help.

---

### Post by AndyCooll on 2006-02-05
[QUOTE=drpolish]yes, im having a problem using samba. One day i was using my network cleanly with no problems when suddenly i lost the ability to connect to my samba servers. So i restarted ubuntu because i couldnt fix it for a week, and reinstalled it. Now i have th same problem. I can access the net and all, and ping the local file servers, but i cannot look at their shares. please help im a linux novice.

EDIT: i just tried using smb:// and connecting, and i can browse the shares in firefox. but i still cannot install a network printer or network share that i can mount - once again, i ask for help.[/QUOTE]

Have you re-applied your Samba password?

```
sudo smbpasswd -a username
```

:cool:

---

### Post by evilgold on 2006-02-05
[QUOTE=drpolish]yes, im having a problem using samba. One day i was using my network cleanly with no problems when suddenly i lost the ability to connect to my samba servers. So i restarted ubuntu because i couldnt fix it for a week, and reinstalled it. Now i have th same problem. I can access the net and all, and ping the local file servers, but i cannot look at their shares. please help im a linux novice.

EDIT: i just tried using smb:// and connecting, and i can browse the shares in firefox. but i still cannot install a network printer or network share that i can mount - once again, i ask for help.[/QUOTE]

did you make sure your in the same workgroup as your windows computer?

Check /etc/samba/smb.conf and make sure its all correct

---

### Post by FrankTM on 2006-02-06
here is the smb.conf that i use, as an attachment
i stripped out quite a few shares and also the printer part

the share [henk] is a share where anybody from the network can write and read
the other share [frank] is read only for anybody

you could however make a more advance config that checks users rights and all, but this is just what i needed

good luck, and don't mind asking questions

---

