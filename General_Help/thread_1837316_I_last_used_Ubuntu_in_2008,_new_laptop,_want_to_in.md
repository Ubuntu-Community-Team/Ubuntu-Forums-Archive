---
title: "I last used Ubuntu in 2008, new laptop, want to install 11.10 fully encrypted"
date: 2011-09-01
forum: General Help
---

### Post by marywadcum on 2011-09-01
So I've never encrypted a drive before. I've used TrueCrypt to create container files, etc. I've decided to forego Windows and install Ubuntu instead on my brand new laptop. I travel internationally a lot. I decided since I'll be starting from scratch with Ubuntu and since I'm planning on going through U.S / Chinese immigration a lot over the next year.. How can I install Ubuntu 11.10 from scratch on a brand new laptop and encrypt the entire drive? What is the best, easiest foolproof way that even a noob (like me) can do it?

Thank you very much. I want to do this installation this weekend when I have a few hours to backup all of my files. Thank you again!

---

### Post by gekken on 2011-09-01
Hi Mary - 

[HERE]("https://help.ubuntu.com/community/EncryptedFilesystemHowto") is the Ubuntu How-To on drive encryption. It's pretty straightforward. 

However, you should really think about some things if you plan on encrypting your drive:

(I will NOT get into the politics of good/bad, this is just FYI)


[LIST=1]
[*]US Customs has the the power to search your laptop for anything it wants and confiscate it for any reason, without a warrant. There are already reports of people coming back to the US with encrypted drives and DHS confiscating them for months until they cracked the drive. That being said, they are pretty tech-stupid, so it would not be too hard to simply encrypt a specific volume, such as /home ensuring your data is somewhat secure.
[*]Chinese customs is most likely the same, if not worse. I've never travelled to mainland China but you see horror stories from various sources.
[/LIST]
To that end, I strongly urge you to do your homework before encrypting.

---

### Post by pqwoerituytrueiwoq on 2011-09-01
during a clean install it is pretty easy (using a separate /home partition may be a good idea)
[IMG]http://i.imgur.com/Rt0Jk.png[/IMG]


imagine this
person dreses up like a gov official with a encrypted hdd in a briefcase with a partation labeled "nuclear secrets" (the password is ~500 random unicode characters)
and they check it they keep it for a very long time finally get in after may years and find nothing but funny cat pictures now picture the look on there face
:lolflag:

---

### Post by marywadcum on 2011-09-24
Any other thoughts on this?

I still haven't installed Ubuntu yet because I'm trying to figure out what's the best way to travel internationally knowing that at some point I may be searched by customs (I tend to have back luck going through customs).

While I don't have any illegal on my computer.. I do work for an organization that is helping with cannabis law reform so I am concerned that either a U.S or Chinese customs official could ask to look through my computer and they will find many documents and photos of cannabis.

I think it makes sense not to encrypt the whole system because then it looks like I have "something to hide". But I'm still trying to figure out whether encrypting the /home directory will look suspicious and also figure out how secure the default Ubuntu encryption is compared to TrueCrypt.

For reference.. I've ONLY used TrueCrypt in the past to encrypt anything. So I don't have a lot of experience with how other encryption methods work..

---

