---
title: "website help?"
date: 2011-09-12
forum: General Help
---

### Post by Smilax on 2011-09-12
hi, i want to make a website, where users can get a username and upload/download  their own files to their own account. 

i looking around but it's hard to see what's the best way. 

i kinda just want a simple static front page with a login box which goes to a list of their stuff. 


any ideas??

thanks for any help

---

### Post by papibe on 2011-09-12
Do you really need a website?

I made the question because if that the only functionality you need,  you can provide that by installing OpenSSH. You would create an account for each user, and let them use SFTP (through Filezilla or WinSCP in Windows).

Just some thoughts,
Regards.

---

### Post by Smilax on 2011-09-12
> **papibe said:**
> Do you really need a website?

I made the question because if that the only functionality you need,  you can provide that by installing OpenSSH. You would create an account for each user, and let them use SFTP (through Filezilla or WinSCP in Windows).

Just some thoughts,
Regards.


ah! 

this could be the way, just let everone ssh into the box, i will check it out

thanks

---

### Post by papibe on 2011-09-12
If you just need files transfers, you may even restrict ssh access (no login).

regards,

---

### Post by Smilax on 2011-09-12
cheers for the info, i will check it out.

however i was thinking more along the lines of being able to download the files without having to have a program like fillzilla etc. 

like when they get login to their account

they can download just by clicking. 

like ubuntu iso's

just hit the button and the download starts.

i think i'll set up openssh just for me thou, looks like fun

---

### Post by Smilax on 2011-09-12
i will

get a site from noip that is like yourname.theirdomain.com/.net/.info


then i will link this to my dynamic ip of my home computer.



so when they type in the name they get pesented a home page, 

then they can login etc,

---

### Post by Dangertux on 2011-09-12
Keep in mind the scripting necessary to provide this functionality through a web browser has a ton of security implications. There are applications that can do it or you can even script control of ssh. However I would not recommend it.

---

