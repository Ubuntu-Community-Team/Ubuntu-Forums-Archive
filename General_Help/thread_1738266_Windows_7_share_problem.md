---
title: "Windows 7 share problem"
date: 2011-04-24
forum: General Help
---

### Post by mert_da on 2011-04-24
Hello!

I use Ubuntu 10.10 and it is full updated. I have two machines at home. I have shared files from windows 7 but i can not access them from Ubuntu. I open the "entire network" from nautilus, i can see the computer names there. I click on computer name and it ask a password. I think this is the password for "home network password" that i had set it from windows 7. I write the password and i click OK. It ask me again the password ( [http://img268.imageshack.us/i/screenshotexr.png/](http://img268.imageshack.us/i/screenshotexr.png/) ). So i can not see the files because i can not pass this step. Now i installed Ubuntu 11.04 beta2, i did all updates too but the exactly same problem still here. Can someone help me please ?

Thank you!

---

### Post by oracle2b on 2011-04-24
Ensure the workgroup is the same and enter your windows username password not the homegroup password.

---

### Post by mert_da on 2011-04-25
> **oracle2b said:**
> Ensure the workgroup is the same and enter your windows username password not the homegroup password.

I am sure for everything... 

I try with both windows user password and homegroup password(i mean the sharing network password).

I forgot to write: I get "Unable to mount location Failed to mount Windows share" error, when i want to use the folders inside on computer_name_of_my_hardware directory from nautilus. But if i use the "connect to server" link it ask me always the password (the case which i explained it on my first text).

---

### Post by Mark Phelps on 2011-04-25
You're mixing terms -- which is making solving the problem a lot harder than it needs to be.

Workgroups have been around since Windows XP days, work even with the newer versions of Windows (Vista, Win7) and support something known as Simple File Sharing.

Homegroups are new to Win7 and DO NOT work with anything else -- including older versions of Windows.

So, if you're trying to participate in a Homegroup from anything other than Win7, that simply will not work.

---

### Post by mert_da on 2011-05-04
I open every folder on windows 7 to share and i make them open (shared) for everyone and guest. Now the problem solved. 

Thank you!

---

