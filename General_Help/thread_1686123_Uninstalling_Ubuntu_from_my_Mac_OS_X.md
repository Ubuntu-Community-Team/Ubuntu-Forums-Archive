---
title: "Uninstalling Ubuntu from my Mac OS X?"
date: 2011-02-11
forum: General Help
---

### Post by HeavyComponent on 2011-02-11
Hey guys!!

I installed Ubuntu (Latest version off the site) using VMWare Fusion and I want to uninstall it. I went to the partition and the only OS there is my OS X, but then again the 20GB space that I made Ubuntu use up is still missing. So can someone give me a firm detail step by step way to complete remove Ubuntu and gain my HDD space back?

Thanks a lot guys!!!

Sorry if this is the wrong forum section for this, I looked around and couldn't find a better place.

---

### Post by I&#9829;HTML5 on 2011-02-11
From [http://kb.vmware.com/selfservice/search.do?cmd=displayKC&docType=kc&externalId=1003420&sliceId=2&docTypeID=DT_KB_1_1&dialogID=33022852&stateId=1%200%2033024495](http://kb.vmware.com/selfservice/search.do?cmd=displayKC&docType=kc&externalId=1003420&sliceId=2&docTypeID=DT_KB_1_1&dialogID=33022852&stateId=1%200%2033024495):> To delete a virtual machine:
In Fusion, go to Window > Virtual Machine Library.
Power off or suspend your virtual machine.
Click on your virtual machine in the pane on the left side.
Ctrl+click the virtual machine and select Delete.
When prompted, select Move to Trash.

Note: Selecting Keep Files, rather than Move to Trash, will remove the virtual machine from your Virtual Machine Library, but will leave the files that make up your virtual machine intact on your Mac. These files can opened later or moved to another computer. (For details, see Locating the virtual machine bundle in VMware Fusion (1007599).)

To free up the space on your Mac that was taken up by the virtual machine:

Ctrl+click the Trash and select Empty Trash

---

### Post by HeavyComponent on 2011-02-11
Hey thanks for the quick reply. The thing is I had an error when trying to boot into Ubuntu when I started up VMWare Fusion because I accidentally deleted a file that it needed from documents, but I don't even remember what file that was.

I did remove the OS from the left side off Fusion, but nothing asked me to move to trash. Now that the OS isn't there, I did a restart to see if my 20GB space that it took up was back, but it's still missing.

Any help?

---

### Post by HeavyComponent on 2011-02-11
If anyone knows anything please post, I just want my 20GB back!!!

.....I thought having a Mac would make things easier. :(

---

### Post by I&#9829;HTML5 on 2011-02-12
The VMWare article recommends emptying your trash to get the space back.

---

### Post by HeavyComponent on 2011-02-12
Did that and even restarted my Mac twice! ....still missing that 20GB and I uninstalled VMware Fusion. :(

---

### Post by Habeouscorpus on 2011-02-12
It sounds like the Virtual disk is still hanging out on your mac somewhere. Or did you use a partition; if you did that you'll have to resize them to get the space back.

---

