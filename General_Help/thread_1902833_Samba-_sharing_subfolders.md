---
title: "Samba- sharing subfolders"
date: 2011-12-31
forum: General Help
---

### Post by Sachin_ruk on 2011-12-31
Hi all,

So I manged to get Windows to recognise the folder I shared from Ubuntu, but I want to access the subfolders and files in it as well. I get a permission denied when I try to access them.

What do I need to do?

Thanks,
Sachin

---

### Post by syerges on 2011-12-31
Sorry... I don't have your answer, but maybe you have one for me. What version of Windows?

---

### Post by 73ckn797 on 2011-12-31
You have to enable sharing for each folder. Right click over the folder from Nautilus, the file browser, and select sharing to set it up.

---

### Post by Sachin_ruk on 2011-12-31
> **syerges said:**
> Sorry... I don't have your answer, but maybe you have one for me. What version of Windows?

Its Windows 7. as for the previous post is there anyway to share ALL subfolders, there's literally 100's of subfolders and I don't want to keep clicking share for each.

Thanks,
Sachin

---

### Post by syerges on 2011-12-31
I've been having the same trouble as I'm trying to share my e-books between my computers. I gave up on the sharing with Windows directly and instead take control of my main computers desktop and read them from there... if that is a possible solution for you what I use is called TeamViewer.
I had to make a GUI icon for the run command and add that to my menu as well.

---

### Post by 73ckn797 on 2011-12-31
> **Sachin_ruk said:**
> Its Windows 7. as for the previous post is there anyway to share ALL subfolders, there's literally 100's of subfolders and I don't want to keep clicking share for each.

Thanks,
Sachin
Homework assignment: [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by syerges on 2011-12-31
> **73ckn797 said:**
> Homework assignment: [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)


OMGoodness! Thank You! I've been having so much trouble with Samba and not finding anything helpful. This is what I've been looking for. Not my thread but thanks none the less!

---

### Post by 73ckn797 on 2011-12-31
> **syerges said:**
> OMGoodness! Thank You! I've been having so much trouble with Samba and not finding anything helpful. This is what I've been looking for. Not my thread but thanks none the less!

Other helpful links are:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[http://www.googlubuntu.com/](http://www.googlubuntu.com/)  (search engine specific to Ubuntu)
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

---

### Post by Sachin_ruk on 2011-12-31
> **73ckn797 said:**
> Homework assignment: [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

Hi,

Is it possible for you to point me where in the manual it will answer my specific question. I really dont want to read through alot to just to answer a question about sub-folder sharing.

And for the last couple of posts, can we keep this thread relevant just to this question.

Thanks,
Sachin

---

### Post by 73ckn797 on 2011-12-31
> **Sachin_ruk said:**
> Hi,

Is it possible for you to point me where in the manual it will answer my specific question. I really dont want to read through alot to just to answer a question about sub-folder sharing.

And for the last couple of posts, can we keep this thread relevant just to this question.

Thanks,
Sachin
You will have to browse through that yourself. I will not do your reading for you.:D

---

### Post by rjf1 on 2012-01-01
> **Sachin_ruk said:**
> ...So I manged to get Windows to recognise the folder I shared from Ubuntu, but I want to access the subfolders and files in it as well.

This works for me:

RClick on the icon of the top folder you want to share; click Properties; click the Permissions tab; set the access permissions; at the bottom of the box, click 'Apply Permissions to Enclosed Files'

---

### Post by Morbius1 on 2012-01-01
> **Sachin_ruk said:**
> Hi all,

So I manged to get Windows to recognise the folder I shared from Ubuntu, but I want to access the subfolders and files in it as well. I get a permission denied when I try to access them.

What do I need to do?

Thanks,
Sachin
There may be a very simple way out of your dilemma but we need some information first to determine that. How are you sharing your folder - there are 2 methods in Samba. If you post the output of the following commands we can figure it out:
```
testparm -s
``````
net usershare info --long
```Note: I would not recommend you share all of the individual subfolders. Having shares within shares will leave you with an incoherent and unmanageable mess.

---

### Post by Sachin_ruk on 2012-01-01
> **73ckn797 said:**
> You will have to browse through that yourself. I will not do your reading for you.:D
Wasn't quite asking for you to read it, but if you knew specifically a quick fix for this problem.

Well thanks anyway. 
Sachin

---

### Post by 73ckn797 on 2012-01-01
> **Sachin_ruk said:**
> Wasn't quite asking for you to read it, but if you knew specifically a quick fix for this problem.

Well thanks anyway. 
Sachin
I would actually do the same thing in many cases. Hope you find a suitable resolution for your question(s).

---

