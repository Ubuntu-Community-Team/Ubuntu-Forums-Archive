---
title: "Partition Confusion. Need Clarification"
date: 2010-03-20
forum: General Help
---

### Post by schoft on 2010-03-20
Hey there,  I am in the process of installing BT4. At the partitioning stage of the install, i noticed that it could not detect my windows 7 like in the example screenshot they provided with the guide: [click here]("http://www.backtrack-linux.org/images/bt4inst-05.png")    This is how the partition stage looks like on my system:
  [IMG]http://img406.imageshack.us/img406/2877/snapshot1ab.png[/IMG] 


 Why can't i see Windows here? I remember from the partition editor in windows, that my primary C:\ disk had 3 partitions. A system reserve,  some small unallocated space and 157 gb wich belongs to windows.  My question is, why does it fail to detect the windows. I'm guessing the ubuntu installer only sees the 6gb of unallocated space as the only possible option to install on. So Ubuntu can only be installed on unallocated space ? Ill have to narrow down the partition that C:\ is on, make the unallocated partition bigger and put Ubuntu on it.   Did i answer my question there? I am being paranoid because in no case can i loose files :_)  Some clarification will be more than welcome 

Here's a screenshot of my gParted 
[IMG]http://img221.imageshack.us/img221/3195/snapshot2d.png[/IMG]

---

### Post by audiomick on 2010-03-20
Hi.
I am not familiar with the installer in your screenshot, sorry.
I notice that gparted is seeing your windows install. What happens if you choose the "manual" option in the installer you are trying to use?

---

