---
title: "Samba sees but does not conect to windows shares"
date: 2010-04-05
forum: General Help
---

### Post by Zanara on 2010-04-05
I am using Ubuntu 9.1 and want to connect to my other computer (win 7)  on my home network. I installed Samba...and it sees the 'windows network'...then it sees the pc I want to connect to, but when I try to dbl click on its name, I get 'unable to mount location, failed to retrieve share list from server'. There are at least 8 publicly shared folders on that PC that other Windows pc's can connect to without problem.  
I have tried to google this error but see nothing consistent and nothing that does not involve VERY lengthy fixes such as editing many config files, etc. I am a noob and if a simple solution is not available, I will just live with it...but hope that there is a quick fix. Thanks.

---

### Post by spiky001 on 2010-04-05
hi have you set the windows to allow shares ? if so maybe turn off firewall on windows see what happens then

---

### Post by Zanara on 2010-04-06
> **spiky001 said:**
> hi have you set the windows to allow shares ? if so maybe turn off firewall on windows see what happens then

Yes. there are many shares on the Windows 7 pc. I have 4 pc's in my house, 3 Windows 7 and one Ubuntu. The Windows PC's 'talk' to each other just fine...but Ubuntu wants nothing to do with them. Based on my Google search, I see it is somewhat common, but the solution, like 99.999% of all Ubuntu solutions are long and complicated and not worth it. This is why I have 3 Windows PC's and only one Ubuntu...Linux has come a long way, but it is far from being declared user friendly. Maybe in 5-10 more years.

---

### Post by Gunman1982 on 2010-04-06
> **Zanara said:**
> This is why I have 3 Windows PC's and only one Ubuntu...Linux has come a long way, but it is far from being declared user friendly. Maybe in 5-10 more years.

And that is why I switched all PC's (3)/ Laptops (5) to Linux at home. Because Linux is far more userfriendly than Windows who has problems to share folders/printers even between their own OS versions and give a crap about user problems. 
Try to share a folder between win xp and win95 or try to share a printer between xp and vista. Some would say either you're lucky or you're dekcuf. But since its generalization time I say: Windows has a long way to go and is not useful for anyone right now and I doubt it will ever be.

Sorry but I seriously couldn't resist.

---

### Post by Jerry N on 2010-04-06
> **Zanara said:**
>  ......when I try to dbl click on its name, I get 'unable to mount location, failed to retrieve share list from server'. 

I went through the same thing a while back and I think what I had to do was share the Windows 7 folder with the "Share To" option (or something very similar to that) and then select "Everyone" from the drop down list.  

Jerry

---

