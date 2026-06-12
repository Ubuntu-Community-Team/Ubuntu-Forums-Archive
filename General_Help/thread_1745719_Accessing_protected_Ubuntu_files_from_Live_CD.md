---
title: "Accessing protected Ubuntu files from Live CD"
date: 2011-05-01
forum: General Help
---

### Post by Ghostlove on 2011-05-01
Hi there, I'm the woman who was having problems with Ubuntu freezing every hour or so.

I decided to upgrade to Natty and the computer froze during the upgrade process. Now it won't start up at all.

I have files on that Ubuntu partition that aren't backed up. So I put in the 10.10 Live CD thinking I could access them from there, copy them over to my external hard drive, and do a fresh Natty install.

However, when I try to open my folders or copy them over I get told I don't have permission to access them.

Can anyone help me do this, so I don't lose precious photographs and files? I know I should have been more careful about backing up regularly, but I still hadn't found a program to do this for me adequately!

---

### Post by pme 72 on 2011-05-01
I found the same issue accessing some of my 10.04 files when running the 11.04 Live CD. This seems like a good safe guard to me but my 10.04 is working. 

I tried loading a Knoppix 6.2.1 Live CD and had no issues accessing the files. Just to test I copied one of the files that was previously marked Locked when I accessed it with the 11.04 CD. I was able to copy it to a USB drive and am able to read the file in my Lucid installation. 

Knoppix.com lists stores in the UK where you can purchase a 6.2 LiveCD. V6.4.4 is also available as a download. It looks like Linux Magazine had a Knoppix 6.5 Live disk in a recent issue.

---

### Post by C.S.Cameron on 2011-05-01
My computer froze up while upgrading to 11.04 also, however upgrade seemed to complete after rebooting.

Can you grab your files by typing F2 gksu nautilus?

---

### Post by Rasa1111 on 2011-05-01
Open a terminal..

Type (or copy&paste) into a terminal..

```
gksudo nautilus
```

then type your password,
and a window will open (in root),
then you can copy and save/move any files you need to.

then just close it out, and close terminal when you're done.

hope it helps.

---

### Post by tredegar on 2011-05-01
The above advice is good (gksudo nautilus).

> I know I should have been more careful about backing up regularly, but I still hadn't found a program to do this for me adequately!
I have an **ext4** formatted external drive.
From time to time I plug it in and drag **/home/tred/** to it
Then I rename it **/home/tred-*date*** on the external drive.

Simple, and works.

I also do fancy stuff with **rsync**, which also works, and is much faster, but a *very* little more complicated. But _any_ backup is better than none.

BTW, there seem to be a lot of teething problems with 11.04, so I have stuck with 10.04LTS. It works well.

---

