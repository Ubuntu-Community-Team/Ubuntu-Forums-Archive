---
title: "How To Get fils from virtualbox"
date: 2009-09-25
forum: General Help
---

### Post by BAMF1501 on 2009-09-25
OK i installed windows xp in a virtual box and i got some windows files i want to copy from the virtual machine to my main ubuntu desktop how do i do so ??

---

### Post by Commander_Keen on 2009-09-25
The cool thing to do is you set up a network system.
You could assign your XP box 192.168.1.1 (subnet mask of 255.255.255.0)and share out a folder called data
 Assign your ubunto 192.168.1.2 and subnet mask of 255.255.255.0

Try that..

---

### Post by Liolikas on 2009-09-25
If files not big and you have net so just try to upload somewhere.

---

### Post by BAMF1501 on 2009-09-25
commander sounds to diffucult and i tryed uplaoding to a file hosting site but i dont get fast speeds on virtual box with upload an di have 30 mb connection

---

### Post by Commander_Keen on 2009-09-25
O.k.. try this.
Go to virtualbox.com and look up share folder/directory..

---

### Post by amsum on 2009-09-25
> **BAMF1501 said:**
> OK i installed windows xp in a virtual box and i got some windows files i want to copy from the virtual machine to my main ubuntu desktop how do i do so ??

You should try this. First make sure you have Guest Edition already installed. 
1)Now shut down the Windows XP and goto Settings in VirtualBox. 2)Then goto Share Folders. 
3)Create a folder with name something like "Virtualshare" or anything in one of the partitions (partition of ubuntu). Give it both Read/Write permissions. 
4)Now start XP. 
5)Open My Computer. Now single click "Folder" tab in the windows browser bar.
6)Now in the left side you have Folder Bar. Goto "My Network Places", then "Entire Network", then "Virtualbox Shared Folders" and finally click that VBOXSVR Share Folder. NOTE: The partition in which we have created VirtualShare must be already Mounted.
7)Now you will be able to see that VirtualShare folder. Just copy paste the windows content in that folder.
8)Now you can access the same folder from Ubuntu.

---

