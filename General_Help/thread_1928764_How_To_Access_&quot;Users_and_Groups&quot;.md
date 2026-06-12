---
title: "How To Access &quot;Users and Groups&quot;"
date: 2012-02-20
forum: General Help
---

### Post by stevedude on 2012-02-20
I'm using Ubuntu Natty 64-bit and I want to setup an OS in VBox. I receive an error message that I need to change the "vboxusers" group. I know exactly what I need to do because I have done this in the past, however, I can't seem to access my "Users and Groups" in Natty.

If I click on my user name in the upper-right corner of the desktop, I can select "User Accounts..." from here (Alternatively from the Power Cog icon and selecting "System Settings > User Accounts", but I have no option to "manage"  any accounts after unlocking the program. The only thing presented to me in the window is the option to change my name, account type, or language. The left side of the window shows my avatar and there is a "+" symbol at the bottom left to add a user/group. Adding "vboxuser" just presents me with an error message that the group already exists.

Prior to Unity I would choose System Settings > Users and Groups > Manage Groups and I would get a list of all of the groups and who belongs to them. I can't seem to get to that point within Natty.

Is there a package I need to install?  If I search for "Users and Groups" or "Manage Groups" in DASH, I just keep getting the "User Accounts" program mentioned above as my search result.

I would appreciate any help here. Thanks!

---

### Post by Leppie on 2012-02-20
I don't know which package holds this, but the executable is "users-admin".
So if you want to launch it from a terminal:
```
gksudo users-admin
```

---

### Post by stevedude on 2012-02-20
Thanks for the reply Leppie

Unfortunately, the terminal just blinks at me. No program is launched after typing the command you gave so I'm guessing I am missing a package?


** EDIT ** I now have something to search for so I searched for "users-admin" and found that I indeed need a package installed called "gnome-system-tools". Once that is installed you can use DASH to look up Users and Groups and the "Users and Groups Accounts" now appears.  Also you can refer to: [http://askubuntu.com/questions/66718/how-to-manage-users-and-groups](http://askubuntu.com/questions/66718/how-to-manage-users-and-groups)


Thanks again Leppie for your information!

---

### Post by catnip_X07 on 2012-03-01
Phenominal. Thank you for the updated post stevedude.

---

