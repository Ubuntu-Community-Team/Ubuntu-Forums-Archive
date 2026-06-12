---
title: "Thunderbird Update Problem 'Requires installation of untrusted packages'"
date: 2012-09-28
forum: General Help
---

### Post by hardikbv on 2012-09-28
Hello Friends,

I just connected my e-mail with Thunderbird and started using it.  

After setting the mail, I ran update manage and found that there are number of updates for Thunderbird.  But, when I click on them, following error is shown by update manager. 
---

Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.
---

How to install those updates? 

Thanks.

---

### Post by CrusaderAD on 2012-09-28
Try this in terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

and hit Y when prompted to install. I think it prompts you. That should do it.

---

### Post by hardikbv on 2012-09-28
Hi Cruseder AD.. 

I think I have managed to do it.  What I did was
-- Went to Download Manager, settings/other softwares and  clicked on Chrocal partners options (both of them)
-- Restarted the computer 

and try to run the update manager again.  It ran after that. 

Does this resemble to the same as you suggested in code? Or should I also do the code option?

Thanks.

Hardik

---

### Post by CrusaderAD on 2012-09-28
> **hardikbv said:**
> Hi Cruseder AD.. 

I think I have managed to do it.  What I did was
-- Went to Download Manager, settings/other softwares and  clicked on Chrocal partners options (both of them)
-- Restarted the computer 

and try to run the update manager again.  It ran after that. 

Does this resemble to the same as you suggested in code? Or should I also do the code option?

Thanks.

Hardik

Nope, you don't have to :) what you did essentially did the same thing.

---

### Post by hardikbv on 2012-09-28
Thanks again for your help.

Greetings from India.

---

### Post by CrusaderAD on 2012-09-28
Hello from America! Welcome to the forums! :)

---

