---
title: "problem firefox"
date: 2012-02-24
forum: General Help
---

### Post by YesGood on 2012-02-24
Hi

I don't have access in th firefox with my users

Why?

Only with root user, i can access to use.

please, Help me.

---

### Post by enjoijesus94 on 2012-02-24
Explain with more detail and ill see if i can help

---

### Post by YesGood on 2012-02-24
Thanks

I can to open the firefox browser only with the terminal  sudo firefox, and that is with the root user.

When I try to open the firefox browser with the desktop icon, appear one message 

Your profile cannot be loaded. It may be missing or inaccesible

---

### Post by enjoijesus94 on 2012-02-24
Try Reinstalling Firefox 
if that dosnt work see if another browser works 

my favirote
> sudo apt-get install chromium-browser

---

### Post by YesGood on 2012-02-24
I reinstalled twice, but I have the same problem.

Hoe can i solved?

---

### Post by enjoijesus94 on 2012-02-24
> **YesGood said:**
> I reinstalled twice, but I have the same problem.

Hoe can i solved?

Did You Already Install Chromium-browser?

---

### Post by YesGood on 2012-02-24
No, I did'nt.

Thanks for your interest.

I think this problem, can be solved. 
I saw in the google mentioned the same error, but I don't comprehend.

so, I find help here.

---

### Post by enjoijesus94 on 2012-02-24
> **YesGood said:**
> No, I did'nt.

Thanks for your interest.

I think this problem, can be solved. 
I saw in the google mentioned the same error, but I don't comprehend.

so, I find help here.

its no prob 

ill look for this error and be sure to post.

---

### Post by wojox on 2012-02-24
[Firefox doesn't start as normal user, but it does using sudo]("http://www.webgapps.org/tutorials/firefox/troubleshooting/startup-issues-and-solutions")

---

### Post by YesGood on 2012-02-24
Thanks Wojox.

I can solve this problem with your link
First, I close the firefox and  then I run 
sudo chown -R $USER:$USER ~/.mozilla

Now, I use firefox opened with the icon.

---

