---
title: "Unable To Access Internet After Uninstalling Firefox"
date: 2010-03-23
forum: General Help
---

### Post by johnathanamber on 2010-03-23
Hello,

Just to put things in order.

I did a new install of Karmic.

Update Firefox to 3.6.3pre.

I was unable to load some web pages.

Tried various other versions, etc.

Uninstalled Firefox.

Installed Google Chrome.

Chrome also can not access any web pages.

Chrome give the following error:
This webpage is unavilable.

I know that I am connected to my wireless. I am able to download and send email and I am able to use my IM (Empathy), but I am not able to access the internet via Firefox or Chrome.

Also I am able to ping [www.google.com](www.google.com) and [www.yahoo.com](www.yahoo.com) without issue.

Any ideas?

Thank you and God bless,
Johnathan

---

### Post by linden940 on 2010-03-23
reinstall firefox...if u have dos it work then?

---

### Post by 2hot6ft2 on 2010-03-23
It probably removed some other important files so I would try re-installing it.
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install firefox
```

---

### Post by johnathanamber on 2010-03-23
Thank you for the reply.

That doesn't explain why Chrome will not work.

I will try it (again) and I will report what happens.

Also, not to mention that I am also able to update Ubuntu via the Update Manger... updated xlrunner just minutes ago.

---

### Post by 2hot6ft2 on 2010-03-23
> **johnathanamber said:**
> 
**That doesn't explain why Chrome will not work.**

> **2hot6ft2 said:**
> **It probably removed some other important files**
I thought that explained it pretty well. Firefox is tightly integrated into ubuntu I believe, but I'm on 10.04 right now and that doesn't seem to be the case on it.

---

### Post by johnathanamber on 2010-03-23
> **2hot6ft2 said:**
> I thought that explained it pretty well.

Sorry, I was referring to reinstalling firefox relating to Chrome not working.

BTW I did that and still no go. After reinstalling fierfox did not help.

I did also do a ***sudo apt-get autoremove*** to remove any unneeded packages that I might have installed while toying with firefox versions.

---

### Post by 2hot6ft2 on 2010-03-23
Perhaps someone running 9.10 could go to synaptic and select firefox and mark it for complete removal and take a screen shot of what all it would remove before hitting cancel. I'm sure there's more in 9.10 than in 10.04.

Here's a pic of what it would remove in 10.04.

---

### Post by wojox on 2010-03-23
Here's a good troubleshooting guide: [Troubleshooting]("http://lovinglinux.megabyet.net/?page_id=220#Troubleshooting-1")

---

### Post by johnathanamber on 2010-03-23
> **2hot6ft2 said:**
> Perhaps someone running 9.10 could go to synaptic and select firefox and mark it for complete removal and take a screen shot of what all it would remove before hitting cancel. I'm sure there's more in 9.10 than in 10.04.

Here's a pic of what it would remove in 10.04.

Maybe a required set of packages that are needed for firefox to get on the net would help? Obviously this would relate to more than just firefox, but browsers in general.

Thanks 2hot6ft2

---

### Post by johnathanamber on 2010-03-23
> **wojox said:**
> Here's a good troubleshooting guide: [Troubleshooting]("http://lovinglinux.megabyet.net/?page_id=220#Troubleshooting-1")

@wojox,

Thanks for the link.

I've followed the things that I have not tried before, i.e. safe-mode, profile, removing the .mozilla folder, etc.

None of which worked.

Chrome still doesn't work.

Figured I might have to reinstall unless more insight could be given?

Thank you and God bless,
Johnathan

---

### Post by 2hot6ft2 on 2010-03-23
> **johnathanamber said:**
> Maybe a required set of packages that are needed for firefox to get on the net would help? Obviously this would relate to more than just firefox, but browsers in general.

Thanks 2hot6ft2
That's what I was thinking.
You're welcome, and I hope you figure it out. I tried searching for anything like it and came up with nothing to help.

---

