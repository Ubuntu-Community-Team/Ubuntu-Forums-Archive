---
title: "permission question"
date: 2010-10-13
forum: General Help
---

### Post by r0k3t on 2010-10-13
Hi there, 

I thought I understood this, I put me (my user) in the www-data group then changed the permission on the /var/www folder to be group owned by www-data and `ls -ls` reads rwxrwxr-x. I thought this should let me create a folder now? Yeah... Am i missing something? 

Thanks - I haven't used Linux in years so maybe I am just getting daft in my old age...

---

### Post by WorMzy on 2010-10-13
I think you need to log out and back in for group changes to take effect.

---

### Post by r0k3t on 2010-10-14
Can someone point me in the direction of more info on this? I have never know this to be the case in unix/linux ever... If you change permissions then you are all set - there was never any logging out and back in stuff. Of course I may be missing something that is why I want more info if someone has it...

Thanks!

---

### Post by Morbius1 on 2010-10-14
You don't need to log out and log in again for a chmod or a chown to take affect but you do need to do that to have a group change to yourself take affect.

EDIT: Are you sure you've been added to the group. Run the following command to verify: ```
id
```

---

### Post by r0k3t on 2010-10-15
Yeah - here is the output of ID

```

kenn@kenn-laptop:~$ id kenn 
uid=1000(kenn) gid=1000(kenn) groups=1000(kenn),4(adm),20(dialout),24(cdrom),29(audio),30(dip),33(www-data),46(plugdev),105(lpadmin),112(netdev),119(admin),122(sambashare)
kenn@kenn-laptop:~$ 


```

Now - in order to get moving with what I was doing I had to change the directory permissions to give `kenn` ownership, but I can guarantee that indeed was owned by root but group owned by www-data with 0775 as the permissions... I should have been able to write to it I am pretty sure.

---

