---
title: "Not able to become root in terminal"
date: 2011-06-20
forum: General Help
---

### Post by sunandi on 2011-06-20
Hi Everyone,
This I never see enterprise linux which I use.

I just installed Ubuntu 11.04.
I am not able to become superuser in terminal

Same password when I give to sudo <application> it works but when I give it for su it doesnt.
It says authentication failure.

Help will be really appriciated

Thanks,

---

### Post by haqking on 2011-06-20
do you have root enabled ?

by dafault it is disabled

and you shouldnt enable it to keep in line with the canonical security model ;-)

better to use Sudo -i instead

---

### Post by collisionystm on 2011-06-20
> **haqking said:**
> <snip>


Although you should be sure to lock the root account when you are done.

```
sudo passwd -l root

```

---

### Post by yetiman64 on 2011-06-20
@ haqking, this site openly supports Canonical's security model and enabling the root account is not part of that model.

@ sunandi, to get a root shell the preferred method is ```
sudo -i
```  because the root account is disabled by default "su" doesn't work. Please do not enable the root account it may leave you open to lack of support here (threads get closed with that info in them on occasion).

Edit: it may pay you to have a read of the RootSudo link in my sig :-)

---

### Post by coffeecat on 2011-06-20
@sunandi, enabling the root account is not necessary. Use the command yetiman64 suggests, but please also read this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

**EDIT**:

@haqking, please read this:

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by haqking on 2011-06-20
> **yetiman64 said:**
> @ haqking, this site openly supports Canonical's security model and enabling the root account is not part of that model.

@ sunandi, to get a root shell the preferred method is ```
sudo -i
```  because the root account is disabled by default "su" doesn't work. Please do not enable the root account it may leave you open to lack of support here (threads get closed with that info in them on occasion).


Ok sorry about that, good to know, cheers

---

### Post by sunandi on 2011-06-20
Hi Everyone,
Thanks a lot for such a quick response,
sudo -i worked 

I never thought that the response will be this quick ...... awesome

---

### Post by yetiman64 on 2011-06-20
> **sunandi said:**
> Hi Everyone,
Thanks a lot for such a quick response,
sudo -i worked 

I never thought that the response will be this quick ...... awesome

:lol: this subject is always jumped on pretty quick when root account enabling is posted :lol:
Regards, yetiman64

---

