---
title: "Evolution Mail Client"
date: 2009-07-29
forum: General Help
---

### Post by St Nabi on 2009-07-29
Hi there all,

I finally managed to configure Evolution and started to receive as well send messages. I can send messages perfectly ok but can't download anymore...

Suggestions please

Regards

St Nabi

---

### Post by JohnL2009 on 2009-07-29
So how did you get it to send messages?,  I'm using gmail - downloads ok but can't send out.

---

### Post by pmlxuser on 2009-07-29
Please check the gmail setting option, on the web based gmail. you are going to find instruction on how to set POP and STMP for gmail onevolution

---

### Post by JohnL2009 on 2009-07-29
Already have - everything seems to be ok - in fact at one time it did send but stopped for some reason.

---

### Post by St Nabi on 2009-07-29
I am using Sky not gmail.

I am still able to send perfectly OK for some bizarre reason I cant Download any new mail...

I had configured it normally and it was working just fine but now I can only send...

---

### Post by TrakerJon on 2009-07-29
> **St Nabi said:**
> I am using Sky not gmail.

I am still able to send perfectly OK for some bizarre reason I cant Download any new mail...

I had configured it normally and it was working just fine but now I can only send...


Could be a firewall issue, either on your local machine or your broadband router. Research Ubuntu UFW or determine which port needs to be configured on your machine or contact your ISP to assit you in allowing traffic through your router.

---

### Post by plucky on 2009-07-29
> **St Nabi said:**
> I am using Sky not gmail.

I am still able to send perfectly OK for some bizarre reason I cant Download any new mail...

I had configured it normally and it was working just fine but now I can only send...

Check the mail hasn't been sent straight to your **Junk** folder.

---

### Post by St Nabi on 2009-07-29
I know the ports but it could be a firewall issue, so I will check that out. As far as my ISP is concerned, SKY do not offer any supoprt for Ubuntu and will let you know the outcome.

Cheers

---

### Post by St Nabi on 2009-07-29
The Junk Folder is empty. The mail is simply not coming in at all.

---

### Post by howefield on 2009-07-29
Maybe saying the obvious, but presumably you have logged on to webmail and you KNOW there is mail on the server which isn't downloading to Evolution ?

I have a gmail account polling my sky email, but I'll set it up standalone and try to replicate the issue.

---

### Post by St Nabi on 2009-07-29
Correct.

I enabled UFW, as suggested above by TrakerJon, and allowed the two ports for incoming and outgoing mail. 

Bizarrely enough I managed to get one mail to download that came in after that but nothing else. None of the other emails from today have downloaded.

Is there a limit to the number of mails that Evolution can handle? If so can that be amended using sudo commands?

Regards

St Nabi

---

### Post by dcstar on 2009-07-30
> **St Nabi said:**
> 
.........
Is there a limit to the number of mails that Evolution can handle?


Whatever fits into the 2GB database limit for a 32-bit system (64-bit has a much larger limit).

---

