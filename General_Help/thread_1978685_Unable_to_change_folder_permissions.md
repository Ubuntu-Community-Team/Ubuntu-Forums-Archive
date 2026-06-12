---
title: "Unable to change folder permissions"
date: 2012-05-12
forum: General Help
---

### Post by qbektrix on 2012-05-12
I am using a Ubuntu 10.04 Live USB. Its running on a 8gb flash drive. My system also has a 1tb hard drive which I want to share over the network. I managed to share the default Documents folder which is in the USB drive. But I am unable to share any folder on the 1tb drive. I am not able to change the permission settings on the folder properties.

Kindly advice me. I search around but could not find a solution.

---

### Post by scouser73 on 2012-05-12
**1** - Open the *Terminal*

Enter the following command;

**2** - **sudo -i**

You have now become *Root*

Enter The following command;

**3** - **gksudo nautilus**

The nautilus file manager will now open, go to the folder you wish to change permissions on.

Right click on the folder and select *Properties*, click on the *Permissions* tab.

In the *Owner* part, click on **File Access** and set it to **Read & Write**, then click on **Apply Permissions To Enclosed Files**.

Close *Terminal*

You have successfully changed folder permissions.

---

### Post by Zvlwab on 2012-05-12
What does your /etc/fstab look like?

---

### Post by Prescilla on 2012-05-12
Use the terminal to change permission.
chmod 777 dir

---

### Post by Morbius1 on 2012-05-12
> **qbektrix said:**
> I am using a Ubuntu 10.04 Live USB. Its running on a 8gb flash drive. My system also has a 1tb hard drive which I want to share over the network. I managed to share the default Documents folder which is in the USB drive. But I am unable to share any folder on the 1tb drive. I am not able to change the permission settings on the folder properties.

Kindly advice me. I search around but could not find a solution.
If I make the assumption that the "1TB hard drive" is formatted in ntfs then I can explain all of your symptoms. The "drive" will mount with a "view" that gives it the appearance that the partition is owned by you and with Linux permissions of 0700 meaning only you have access. 

You can't change ownership and permissions on an ntfs partition ( outside of fstab ) using Linux commands because the "view" is immutable. So one easy way out of this if my assumption is correct is to add the following line to /etc/samba/smb.conf:
```
force user = morbius
```[COLOR=Blue]*Change morbius to your own Ubuntu login user name*[/COLOR]

Where you place that line depends on what method of samba sharing you used - there are 2. For now I would suggest putting it in the [global] section - under the workgroup line as it will work in both methods.

Then restart samba:
```
sudo service smbd restart
```Wait a few minutes for the network to settle down then try to gain access again.

[COLOR=Blue]**EDIT**[/COLOR]: Come to think of it I'm also making the fundamental assumption that you are using Samba to share this partition :wink:

---

### Post by qbektrix on 2012-05-12
Thank you Morbius1. I am sorry that I forgot to mention that it was NTFS. The issue is fixed. Thank you.

Thank you to other users also for helping me.

---

