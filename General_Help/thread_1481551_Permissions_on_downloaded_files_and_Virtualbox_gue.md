---
title: "Permissions on downloaded files and Virtualbox guest additions"
date: 2010-05-12
forum: General Help
---

### Post by KelliShaver on 2010-05-12
Hi everyone! I have a quick question about file permissions and also about an error I'm getting in Virtualbox. I think the two issues are related.

Recently, I replaced the hard drive in my computer and when I did, I decided to upgrade from 9.10 to 10.04 and I'm loving the new version. However, I have one minor problem.

Whenever I download files via firefox (or chrome, etc.), they're not initially executable. I have to chmod them before I can run them. This isn't a problem for most things and is, in fact, more secure, I suppose. However, it causes problems for some programs that automatically download files and then need to run them.

Namely, I tried installing Virtualbox guest additions on my XP guest and Virtualbox couldn't mount the iso after it had downloaded it. 

To clarify, I can use wget, download a file, and execute it just fine. If I download the same file via firefox, I have to chmod the file before I can execute it. Virtualbox also can't mount the guest additions iso after it downloads it, and I assume that it's again running into a permissions problem.

I assume this is probably a simple issue of adding the right users to the right groups, but I'm hoping someone who knows more about it than I do can get me sorted out.

Thanks for reading!

---

### Post by wilee-nilee on 2010-05-12
> **KelliShaver said:**
> Hi everyone! I have a quick question about file permissions and also about an error I'm getting in Virtualbox. I think the two issues are related.

Recently, I replaced the hard drive in my computer and when I did, I decided to upgrade from 9.10 to 10.04 and I'm loving the new version. However, I have one minor problem.

Whenever I download files via firefox (or chrome, etc.), they're not initially executable. I have to chmod them before I can run them. This isn't a problem for most things and is, in fact, more secure, I suppose. However, it causes problems for some programs that automatically download files and then need to run them.

Namely, I tried installing Virtualbox guest additions on my XP guest and Virtualbox couldn't mount the iso after it had downloaded it. 

To clarify, I can use wget, download a file, and execute it just fine. If I download the same file via firefox, I have to chmod the file before I can execute it. Virtualbox also can't mount the guest additions iso after it downloads it, and I assume that it's again running into a permissions problem.

I assume this is probably a simple issue of adding the right users to the right groups, but I'm hoping someone who knows more about it than I do can get me sorted out.

Thanks for reading!

Guest additions will auto run if you click on the correct file when you open it. You may have to mount it from the top panel.

---

### Post by KelliShaver on 2010-05-12
Ah, thanks so much!. That worked for the guest additions. I did have to mount it manually. It was trying to automatically after downloading it (when selecting install guest additions) and the automatic mounting failed. I didn't realize it was also listed under mountable devices (feel a bit stupid now). 

I'm still curious about what's causing the weird permissions when downloading files through the web browser, though.

---

### Post by wilee-nilee on 2010-05-12
> **KelliShaver said:**
> Ah, thanks so much!. That worked for the guest additions. I did have to mount it manually. It was trying to automatically after downloading it (when selecting install guest additions) and the automatic mounting failed. I didn't realize it was also listed under mountable devices (feel a bit stupid now). 

I'm still curious about what's causing the weird permissions when downloading files through the web browser, though.

It would be helpful if you described the programs your downloading and which are host and which are guest.

It may be that your downloading in a improper way or programs that are actually available in synaptic, if the correct repositories on ticked on. You have to down load programs for either OS in their own environment.

Having the guest additions installed now may have fixed this in XP, also the best thing you can do with any windows version is only use IE8 or whatever you have to download FF, and have IE set to remove everything on closing. Install ccleaner, malwarebytes, and avast in the XP setup as well as superantispyware. If you want links to these just post that you do. CCleaner has a nice set up to disable startups you don't need, and other great uses.

---

