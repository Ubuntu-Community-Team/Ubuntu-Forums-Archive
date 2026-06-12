---
title: "Error message after login"
date: 2006-05-15
forum: General Help
---

### Post by learning curve on 2006-05-15
This is the error that I get.

Your $home/.dmrc file has incorrect permissions and is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.

Any ideas on how to fix this?

Thanks:)

---

### Post by tonyr on 2006-05-15
If you are using a terminal (look further down for the GUI way), you can
```

cd
ls -l .dmrc

```

and the response should look something like this:
```

-rw----- 1 tonyr tonyr 26 2006-04-09 16:43 .dmrc

```
except with your **userid** and **groupid**.  Mine are userid=tonyr groupid=tonyr

You might have to use **sudo ls -l .dmrc** if the ownership is severely
messed up.

If it doesn't look like that, you can try fixing it with
```

chown <userid>.<groupid> .dmrc
chmod 600 .dmrc

```
I would type **chown tonyr.tonyr .dmrc**.   Again, you might have to use 
**sudo** at the beginning of the commands.  One thing I find curious is that
the error message indicates that the number in the chmod command should
be 644 instead of 600.  You should try both.

If you are using  GUI tools (Gnome or KDE), navigate to your home directory.
In Gnome that's **Places->Home Folder**. In the **View** menu enable
**Show Hidden Files**.  Find the .dmrc file and select its **Properties**.
Under the **Permissions** tab, **Owner** should have **Read** and 
**Write** selected for the 600 permissions.  If you want to try the 644
permissions, check **Read** beside **Group** and **Others**.   The
**User** and **Group** fields at the top should show your **userid** and
**groupid**.  KDE (Kubuntu) has a similar GUI tool for doing this, but I don't have
the details at my fingertips at the moment.

---

