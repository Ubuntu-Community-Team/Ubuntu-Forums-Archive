---
title: "Changing Icon and Setting User Permissions"
date: 2010-10-29
forum: General Help
---

### Post by Hman242 on 2010-10-29
I tried to place a mono icon in usr/icons/etc but I didn't have the permission to do so. I tried to change my user profile to Admin, thinking I could go back to custom, but that hasn't and it isn't allowing me to go back to my previous setting.

Within minutes of being an Admin user I noticed I couldn't even unmount something. I really need to figure out how to change my profile back to default.

After that has been dealt with, I would like some guidance on how to gain root access to put my icon where it needs to be.

Please help me, I can't believe I messed up something this simple and I don't know how to fix it.

---

### Post by trikster_x on 2010-10-30
Well, unless by admin you mean you enabled the root account, there is not really a big deal here.  By default you are an admin account if you are the only user.  The very fact you were able to set your user account to admin shows that.  Permissions are easy to change with the "chown" command.  In your case, simply type in a terminal:
```
chown user_name:user_group /usr/icons/etc
```

Should you need to modify any of the image files in the folder, just set the -R option when you change the permissions.  To change it back to normal, just replace your user name and group with root.  

Alternately you can open a root nautilus window of the directory by putting in terminal:
```
gksudo nautilus /usr/icons/etc
```

I personally don't care for that option in your situation, but if you find yourself in need of moving through unrelated directories, it is fastest.

As for not being able to unmount:  What are you trying to unmount and what error is it giving you?  It may be a simple reboot to fix it.

---

