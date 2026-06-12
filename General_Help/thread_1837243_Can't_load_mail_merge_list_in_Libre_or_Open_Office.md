---
title: "Can't load mail merge list in Libre or Open Office..permission?"
date: 2011-09-01
forum: General Help
---

### Post by guyfromfl on 2011-09-01
I know this is not directly related to ubuntu, but I think there is a permission issue here.

I have a D-Link NAS that stores the data, mounted at /media/W

There is a folder on that drive that stores the lists.

Here's what I do:
Open either Office Writer programs
Load my template
Tools->Mail Merge Wizzard
3. Insert address block
Select Different Address List...
Browse for the ODB file, and select it.
The file shows up in the list but is unelectable, and shows the file size is 0.

I am using smb to share with the NAS, and logging in with the admin credentials, to at least try to get this working...

the permissions on the folder and odb file are 501, so I think this is where the problem lies.

Any suggestions?

---

### Post by guyfromfl on 2011-09-01
Got it, I didn't have the SMB share set exactly right...I downloaded the Samba GUI program from USC, it corrected the permission issue and its working fine now..

---

