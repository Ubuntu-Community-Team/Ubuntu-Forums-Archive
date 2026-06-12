---
title: "Ubuntu 11.10 folder navigation using keyboard."
date: 2011-11-04
forum: General Help
---

### Post by Raaaaay on 2011-11-04
Hi, I don't know what the following technique is called, but I'll explain. You know when you open a folder window and there are a lot of things in it, but you know the name file or folder you're looking for, so you just type the first few letters of the name of the file or folder and hope that the correct one will be highlighted? I don't know what it's called, but I do this a lot. A text field also appears at the bottom-right corner of the folder, indicating what you've typed, and you can edit it using backspace and so on.

So, say you open a folder, and you want to open another folder within it whose name you already know. You type the first few letters of the name of the folder whose name you know, and it gets highlighted. You press enter so that this folder is opened. Then you want to open a file whose name you already know, so you want to type the first few letters of its name again. BUT, on my computer the previous text field is sticky and doesn't disappear, so I can't type the name of the file because it would only be appended to the name of the folder I previously typed, which got stuck. Is there any way to solve this? Am I making myself clear??? I think at some point I've accidentally pressed some keyboard shortcut to make this happen but I have no idea what.

Please help! Thank you in advance!

---

### Post by Script Warlock on 2011-11-04
> **Raaaaay said:**
> Hi, I don't know what the following technique is called, but I'll explain. You know when you open a folder window and there are a lot of things in it, but you know the name file or folder you're looking for, so you just type the first few letters of the name of the file or folder and hope that the correct one will be highlighted? I don't know what it's called, but I do this a lot. A text field also appears at the bottom-right corner of the folder, indicating what you've typed, and you can edit it using backspace and so on.

So, say you open a folder, and you want to open another folder within it whose name you already know. You type the first few letters of the name of the folder whose name you know, and it gets highlighted. You press enter so that this folder is opened. Then you want to open a file whose name you already know, so you want to type the first few letters of its name again. BUT, on my computer the previous text field is sticky and doesn't disappear, so I can't type the name of the file because it would only be appended to the name of the folder I previously typed, which got stuck. Is there any way to solve this? Am I making myself clear??? I think at some point I've accidentally pressed some keyboard shortcut to make this happen but I have no idea what.

Please help! Thank you in advance! 
[nautilus]("http://opensuse-tutorials.com/2008/07/nautilus-tips-and-tricks/")

---

### Post by sdh27 on 2011-11-04
I have had the same problem since updating to 11.10 oneiric.

Script Warlock, I have read through the Nautilus page you provided a link to, but don't see any info on this issue/setting. Can you be more specific?

---

### Post by sdh27 on 2011-11-08
See bug report: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/879456](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/879456)

---

### Post by Raaaaay on 2011-11-09
What seemed to have "solved" the problem for me is that I reset Unity and Compiz.

---

### Post by Raaaaay on 2011-11-11
Nope, the problem came back again.

---

### Post by dcroal on 2011-11-11
For me enabling the oneiric-proposed repository and upgrading to nautilus 1:3.2.1-0ubuntu3.1 fixed the problem completely.

---

