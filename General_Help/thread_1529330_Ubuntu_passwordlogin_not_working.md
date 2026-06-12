---
title: "Ubuntu password/login not working"
date: 2010-07-12
forum: General Help
---

### Post by Manie on 2010-07-12
Ok, i dual boot with Ubuntu 10 and Windows 7 ,everything was working fine, then i went to boot into Ubuntu, and my password was not working

I did the steps on this

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

I did both methods, neither worked

When i did the method on the youtube video, i did not see my username or pssword in the Shadow file.

Can anyone help?

---

### Post by GrantStoner on 2010-07-12
Did you try just reinstalling Ubuntu? Shouldn't be an issue if you're using the Window$ boot loader.

---

### Post by Manie on 2010-07-12
:(

I really don't want to have to install Ubuntu again

---

### Post by GrantStoner on 2010-07-12
It takes like 30min to reformat that part and install again, but burn it to a different disk to install. This way we'll know if the second disk fails also that 1) Window$ is messing something up with Ubuntu; or 2) that it's a hardware issue; or 3) you just didn't install right the first time.

---

### Post by _Mark_ on 2010-07-12
In what way didn't work? Did you get any errors going through the steps or did all seem ok but still can't login?

remember usernames and passwords are case sensitive

---

### Post by Manie on 2010-07-12
I've reinstalled it already, and it doesnt matter if it takes 30 minutes, i was trying to avoid that completely

---

### Post by JustinR on 2010-07-12
If I understand correctly, why not just boot into recovery mode? Then just use "passwd USERNAME newpassword"?

---

### Post by Manie on 2010-07-12
^^

I didnt see that when i googled :(

I tried what i said in the original post and got no results.

Oh well, atleast i learned something, thanks for the help

---

### Post by JustinR on 2010-07-12
What do you mean no results? Did it give an error?

---

### Post by libssd on 2010-07-12
> **_Mark_ said:**
> In what way didn't work? Did you get any errors going through the steps or did all seem ok but still can't login?

remember usernames and passwords are case sensitive
Once or twice a year, my father-in-law calls with this question. My answer is always: "Is the Caps Lock key on?" So far, this has worked every time. :D

---

### Post by Manie on 2010-07-12
> **JustinR said:**
> What do you mean no results? Did it give an error?

When i followed the steps, gave me no errors, told me password updated successfully, then i went to login, and nothing

---

### Post by GrantStoner on 2010-07-12
Have you tried "root" and "toor"?

---

### Post by Manie on 2010-07-12
no didnt try root and toor

And i re installed Ubuntu and just did it that way.

Should i mark this as solved?

---

### Post by GrantStoner on 2010-07-12
well did it work? if it did then yes.

---

### Post by Manie on 2010-07-12
i booted into windows 7 recovery and went to command prompt type in 

bootrec.exe /fixboot press enter
bootrec.exe /fix mbr press enter

^^ this will fix the startup issue if you use G-Parted to delete the Ubuntu partitions and stuff, and then just reinstall Ubuntu on the free space.

---

