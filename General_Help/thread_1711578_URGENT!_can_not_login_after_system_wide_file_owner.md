---
title: "URGENT! can not login after system wide file owner change from root to user"
date: 2011-03-21
forum: General Help
---

### Post by fireandspike on 2011-03-21
Hi

I used to use the root account for everything for more than a year then I moved to a user account for security reasons but almost all files had root as owner so I could not go 5 minutes without having to change to root and then change the owner of a file to my username to make it usable. I got fed up with this so I just changed the owner of every file on the system to my username instead of root.

command  chown -R myusername *   in the base directory  /

Everything was fine until i restarted and the login screen became non functional and i got 2 error messages related to xsession and gnome errors. 

I think this is because the login screen might have its own user account and it cant access the files for the login process because it is owned by myusername.

So my question is what is the user-name of the login account and what folders/files need to have their owner changed so the login process can work?

I'm on 10.04 lucid

Thanks

---

### Post by lykwydchykyn on 2011-03-21
I've attempted to walk people through recovering from this sort of thing before, and honestly it's probably better to backup your files from a LiveCD and reinstall at this point.  Permissions are important to a lot of processes, and even if you got it to login again many systems would be subtly broken for who knows how long.

That said, the vast majority of things outside of /home and /tmp are owned by root.  You can try changing all of them back from a live disc and see if that gets you logging in again.

---

### Post by tredegar on 2011-03-21
You need to learn about linux permissions and how to use them to your advantage, rather than the "blunderbuss" approach of making everything accessible and owned by anyone. You tried this, and it broke linux (for good reasons). Linux isn't windows and trying to make it act like windows is a big mistake.

But I agree with lykwydchykyn: Rescue your personal files, reinstall, re-instate your personal files. Trying to restore the correct permissions for thousands of files is not really a valid option.

---

### Post by blueridgedog on 2011-03-21
There are several threads on the forums regarding this type of system destruction:

[http://ubuntuforums.org/showthread.php?t=894674](http://ubuntuforums.org/showthread.php?t=894674)

I recommend you mount your system using a LiveCD, copy over essential files then re-install, as the fix is likely to be more time consuming.

---

### Post by Thund3rstruck on 2011-03-21
> **fireandspike said:**
> 
So my question is what is the user-name of the login account and what folders/files need to have their owner changed so the login process can work?

Guys, you only learn by trying and that's what makes the F/OSS movement so compelling. No need to berate him. 

@fireandspike,

This may or may not help you but get to a shell prompt (CTRL+ALT+BackSpace or recovery mode, etc) and enable the root account

```

$ sudo passwd root

```

You should be able to then interactively login with root. From there reset your ownership

```

$ sudo chown -R /home/yourUserName/*

```

That should get you back into the system.

---

### Post by lisati on 2011-03-21
As others have pointed out (and you have discovered for yourself), running as "root" has its perils for the unwary, which is why the [sudo]("https://help.ubuntu.com/community/RootSudo") approach is commonly recommended here for tasks that require admin privileges.

I'm putting in my vote for backing up as many of your data files as possible, and doing a reinstall as being most likely the easiest approach.

---

### Post by asmoore82 on 2011-03-21
> **fireandspike said:**
> I used to use the root account for everythingStrike One(1)!
> **fireandspike said:**
> for more than a yearStrike Two(2)!!
> **fireandspike said:**
> so I just changed the owner of every file on the systemSteerike THREE(3)!!!

3 wrongs don't make a right, and piling on more won't help either:
> **Thund3rstruck said:**
> ```

$ sudo passwd root

```Strike 4!!!!
Never enable the root account,```
sudo -s
```only when absolutely necessary.
> **Thund3rstruck said:**
> ```

$ sudo chown -R /home/yourUserName/*

```That should get you back into the system.Strike 5!!!!!
There are a ton of system files that are *not* owned by root. There is no quick fix.
If you want a working Ubuntu system, install a working Ubuntu system.

5 Strikes? What is this? Canadian Baseball on Ice?:P

---

