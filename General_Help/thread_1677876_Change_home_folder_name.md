---
title: "Change home folder name?"
date: 2011-01-29
forum: General Help
---

### Post by Markansas on 2011-01-29
I just got a used machine with ubuntu on it, and can't seem to change the name of 'Home.' Help?

---

### Post by AlphaLexman on 2011-01-29
You REALLY don't want to do that.

---

### Post by Frogs Hair on 2011-01-29
Do you want to rename home or change the user name that appears on the home folder ?

If it is the latter go to System > Administration > Users and Groups to change the user name.

---

### Post by srs5694 on 2011-01-29
Here's a simpler way:


[list=1]
[*]Go to System -> Administration -> Users and Groups. This will open a window for managing users.
[*]Click Add and go through the menus to create a new user with the desired name.
[*]Select the new user and then, on the right where it reads "Account Type," click Change to change the user from a Desktop User to an Administrator. Alternatively, click Advanced Settings and use the User Privileges tab to duplicate the privileges from the current account. (You'll need to access the same tab for your current account first and write down its settings.)
[/list]


You can now log out and log back in again with the new account. If you set it up as an Administrator account, it will actually have slightly greater power than the original account. Once you're satisfied that the new account is working correctly, you can delete the old one.

---

### Post by tredegar on 2011-01-29
> Here's a simpler way:
Which version of ubuntu are you running and which version of ubuntu is **Markansas** running?

Have you tested this clicky-clicky way with the release he is running?

---

### Post by AlphaLexman on 2011-01-29
To the OP:

Some posts have talked about changing your username directory in the /home directory. Please understand, that is perfectly **ok**, and you may choose one of the posted methods to do so.

But if your intention [is | was] to rename the /home directory in the / directory, *which was my initial understanding*, you should seriously reconsider. It can be done, but forum etiquette prevents me from telling you.

---

### Post by QLee on 2011-01-29
AlphaLexman,
I agree with you, some posters have made a huge leap from the actual question with their description of how to proceed.

One even told how to enable root.

I think Markansas should be asked to clarify what is intended.

---

### Post by CharlesA on 2011-01-29
A better thing to do would be to reinstall. You don't know what is on a used PC.

In any case, it is usually better to use this to get a root prompt:

```
sudo -i
```

Instead of activating the root account.

---

