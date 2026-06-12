---
title: "Double sided printing on HP in 10.10 - can't understand bug fix"
date: 2010-11-15
forum: General Help
---

### Post by MorrisseyJ on 2010-11-15
Hi, 

I am having some trouble getting double sided printing on and HP in 10.10. 

From what i can tell the following bug report ([https://bugs.launchpad.net/ubuntu/maverick/+source/hplip/+bug/657357](https://bugs.launchpad.net/ubuntu/maverick/+source/hplip/+bug/657357)) describes my problem to a T and appears to offer a solution ([https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)) 

The problem is that i don't really know how to understand this bug-fix as i don't know enough about Ubuntu, its development and updates. 

I thus have a number of questions:

1. Has this bug been fixed in some update? If so where can i get it?
2. If the bug-fix is not available in an update how do i enable selective upgrading from -proposed? Do i simply create the file /etc/apt/preferences as instructed at: [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)
3. If i have to do '2.' above, can someone tell me what else i need to do. i.e. should i use the alternative install using > sudo aptitude install packagename/maverick-proposed, do i need to 'Enable Apport', and what will be the implications of all this for my upgrades in the future?

Any help in language which is slightly more simple than that contained on the pages i have referenced would be greatly appreciated. 

Any other solutions for my printing problems would also be welcome.

Thanks.

---

### Post by wt8008 on 2010-11-17
Hello 

The update has been put in the proposed packages, you can enable the proposed updates in Synaptic by checking the corresponding box. You should then update your package list, and upgrade the corresponding package and its dependencies. Then, you can uncheck the proposed update packages to prevent yourself from downloading other untested packages. You may also want to report back that the package is resolved of the bug, so that it can be moved to the normal updates section.

---

### Post by MorrisseyJ on 2010-11-17
Thanks WT8008:

I have, i think, followed the instructions but haven't resolved the double-sided printing issue. I am not sure if this is because i have done the wrong thing, or if the big fix does not work in my case.

So what i did was:
1. Open synaptic
2. Settings tab --> repositories
3. Updates Tab: check 'proposed updates (maverick-proposed)' box
4. Click close - receive info telling me that i need to reload for changes to take effect
5. Reload
6. Search for hplip-gui
7. Check hplip-gui box
8. Hit 'Apply'
9. Approve the installation of 5 packages

This hasn't fixed the double-sided printing problem in either OO or Document Viewer.

Can anyone tell me if i have done the right thing and/or if i have some other problem. Appropriate instructions would be much appreciated. 

On that note, if i have done the wrong thing can anyone tell me all the steps i need to go through to undo what i have done, without wiping out my GUI or similar (something that i have done before...)

Thanks.

---

