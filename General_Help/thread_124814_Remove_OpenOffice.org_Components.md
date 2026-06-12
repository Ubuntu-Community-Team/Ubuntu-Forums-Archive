---
title: "Remove OpenOffice.org Components"
date: 2006-02-02
forum: General Help
---

### Post by Gundamdriver on 2006-02-02
Hi. I am trying to learn to use the Synaptic Package Manager, and I found that it is great...

I have got some problems...
1) I would like to remove some of the components of OpenOffice.org, for example, I don't use Base and I want to remove it. I right-click the Base, then "mark for removal". It noticed me that another component will also be affected. Should I continue to remove Base in this way?
<See attached picture>
2) How do I get new version of programs?
3) To obtain security patches, should I add repositories? I found there is an item about security.

Thanks for your help...

---

### Post by MartinG on 2006-02-02
[QUOTE=Gundamdriver]Hi. I am trying to learn to use the Synaptic Package Manager, and I found that it is great...

I have got some problems...
1) I would like to remove some of the components of OpenOffice.org, for example, I don't use Base and I want to remove it. I right-click the Base, then "mark for removal". It noticed me that another component will also be affected. Should I continue to remove Base in this way?
<See attached picture>
2) How do I get new version of programs?
3) To obtain security patches, should I add repositories? I found there is an item about security.

Thanks for your help...[/QUOTE]1. You can't just remove a part of OpenOffice.org.  It might install as several packages, but they are are all linked.  Remove Base, and you have to remove the entire suite.

2. Run "Reload" in Synaptic (this is the same as apt-get update), and then on the Status page look for upgradeable packages.

3. Open Settings->Repositories, and make sure that the repositories with "security" in their name are enabled (they should be already).  Then any necessary upgrades will be included when you Reload.

---

### Post by Gundamdriver on 2006-02-03
[QUOTE=MartinG]3. Open Settings->Repositories, and make sure that the repositories with "security" in their name are enabled (they should be already).  Then any necessary upgrades will be included when you Reload.[/QUOTE]

Thanks for your reply...
But I still have questions.

1) As you said, OpenOffice.org is installed in suite, so can I remove the suite, and during re-installation, choose the components I need (as what you can do in Windows)?
2) In repositories, I found something called non-free (multiverse), what is that? (Please refer to attached picture)

Thanks for your kindful help again!

---

### Post by MartinG on 2006-02-03
[QUOTE=Gundamdriver]Thanks for your reply...
But I still have questions.

1) As you said, OpenOffice.org is installed in suite, so can I remove the suite, and during re-installation, choose the components I need (as what you can do in Windows)?
2) In repositories, I found something called non-free (multiverse), what is that? (Please refer to attached picture)

Thanks for your kindful help again![/QUOTE]1. No, I'm afraid it's all-or-nothing.  It's the same in Windows, for OpenOffice.org.  You are probably thinking of Microsoft Office, which I believe *does* allow some picking and choosing.  OpenOffice.org is more tightly integrated.

2. Have a look at the following to understand the repository names:
[http://www.ubuntu.com/ubuntu/components](http://www.ubuntu.com/ubuntu/components)

---

### Post by Gundamdriver on 2006-02-03
Thanks for reply.

I think I mixed up MS Office and OpenOffice.org... I thought that OpenOffice.org let users to select which components to be installed...
Thanks for your corrections!

Now I understand what does "multiverse" means... Thanks.

---

