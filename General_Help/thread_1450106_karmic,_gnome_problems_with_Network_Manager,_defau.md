---
title: "karmic, gnome: problems with Network Manager, default keyring, et al"
date: 2010-04-08
forum: General Help
---

### Post by tlroche on 2010-04-08
summary: After changing my user password on my vanilla karmic box, I am unable to change my default keyring password, and grow weary of entering network keys after every awakening.

details:

I'm running

```
$ lsb_release -rdcs
Ubuntu 9.10
9.10
karmic
$ uname -rv
2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010

```

This has mostly worked well, particularly with regard to 2 things I need/want:

[LIST=1]
[*]change my system password every 90 days, for a network on which I work.
[*]have my keyring pw match my system pw, for convenience
[/LIST]

I have in the past been able to do these by

[LIST=1]
[*]change system pw using `passwd`
[*]change default keyring pw using seahorse
[LIST=1]
[*]from main menu, run Applications>Accessories>Passwords and Encryption Keys 
[*]in the default tab (Passwords), select default keyring, rclick>Change Password
[/LIST]
[/LIST]

Until Monday: I changed my system pw successfully, but was not able to change my default keyring pw. I subsequently tried:

[LIST=1]
[*]deleting and recreating the keyring. 
[LIST=1]
[*]```
rm ~/.gnome2/keyrings/default.keyring
```
[*]shutdown/reboot
[*]start Applications>Accessories>Passwords and Encryption Keys 
[*]in the default tab (Passwords), C-n or mainmenu>File>New
[*]in the resulting dialog, choose=Password Keyring, Continue
[*]New Keyring Name=default
[*]enter the password
[/LIST]
This failed, in that after I restarted and connected to my wireless network, I could not save the key to my default keyring.
[*]using PAM per the instructions in
[this post]("http://ubuntuforums.org/showpost.php?p=2776815&postcount=1"), but using 'libpam-gnome-keyring' instead of 'libpam-keyring' (which is apparently obsolete). After editing '/etc/pam.d/gdm' and rebooting (again per the instructions), I was unable to login via the GINA! However I was able to login via C-A-F1 and fix the problem.
[/LIST]
to no avail. So currently I am regularly forced (not only on every system boot, but on every resume from sleep!) to enter my wireless key. How can I fix this?

---

### Post by tlroche on 2010-04-09
bump (not quite 24 hours, but close)

---

### Post by spiky001 on 2010-04-09
hi I done this when I had a prob wjth network manager

[http://www.gosalia.org/forums/thread-27.html](http://www.gosalia.org/forums/thread-27.html)

---

### Post by tlroche on 2010-04-10
> **spiky001 said:**
> [http://www.gosalia.org/forums/thread-27.html](http://www.gosalia.org/forums/thread-27.html)

That's not quite what I wanted, but at least it makes the network-key prompts go away! What I did:

```

me@it:~$ date ; ls -al ~/.gnome2/keyrings/
> Sat Apr 10 18:14:04 EDT 2010
> -rw-------  1 me me    0 2010-03-31 13:23 default
> -rw-------  1 me me  328 2009-12-14 15:12 login.keyring
me@it:~$ rm ~/.gnome2/keyrings/*
me@it:~$ date ; ls -al ~/.gnome2/keyrings/
> Sat Apr 10 18:18:36 EDT 2010
> total 8
> drwx------  2 me me 4096 2010-04-10 18:18 .
> drwx------ 12 me me 4096 2010-04-06 21:57 ..
me@it:~$ sudo shutdown -r now
me@it:~$ date ; ls -al ~/.gnome2/keyrings/
Sat Apr 10 18:23:13 EDT 2010
> -rw-------  1 me me  105 2010-04-10 18:20 login.keyring
# enter network key in NetworkManager dialog
# get no prompt to authenticate to default keyring!
me@it:~$ date ; ls -al ~/.gnome2/keyrings/
Sat Apr 10 18:23:47 EDT 2010
> -rw-------  1 me me  623 2010-04-10 18:23 login.keyring
me@it:~$ sudo shutdown -r now
# NetworkManager just connects, no prompt for key

```

Thanks!

---

### Post by garvinrick4 on 2010-04-10
Keyrings  
 

    1. Open up your Home Folder by clicking Places>Home Folder  
    2. Press CTRL-H (or click View>Show Hidden Files)  
    3. Find a folder called .gnome2 (it has a period at the beginning of the name) and open it by double clicking on it  
    4. In side of the .gnome2 folder, there is another folder called keyrings.  Open it up.  
    5. Delete any files you find within the keyrings folder  
    6. Restart the computer  
 

 After you restart and login (if you&#8217;re automatically logging in) you&#8217;ll probably be asked to enter your wireless networks WPA/WEP encryption key.  After you type that password in, the keyring manager will appear to let you know that it would like to handle the storage of that password and lock it away with a new keyring password.  The box looks like this:  
 

 Instead of typing in a new password, leave both boxes completely empty and click Create.  
 

 You&#8217;ll then be asked if you know what the hell you&#8217;re doing:  
 

 Go ahead and click Use Unsafe Storage.  
 

 WARNING: Doing this creates a new file in your ~/.gnome2/keyrings/ folder called default.keyring and it will now house passwords IN CLEAR TEXT and not in an encrypted form.  So it is imperative that you are certain no untrustworthy persons can access your user account (either physically or by remote) or they will be able to easily open and read this file and obtain many passwords (for things such as FTP accounts, SSH, e-mail accounts, etc).  Proceed with caution.  
 

 From here on all keyring stored passwords you enter will not safeguarded behind a master password or encryption.  Whether or not you want to do this is entirely up to you.  I personally have had enough of the keyring manager and consider it kind of annoying.  But as I said before, you may have certain environmental factors that make having a master password over the rest of your passwords a good idea.  Keep in mind that the keyring password manager has absolutely nothing to do with your administrative/root privilages password that has to be entered any time you want to apply updates, or add/remove software.  You will still have to type your account password in for these actions, and that is something I am quite comfortable with. I&#8217;m just happy I don&#8217;t have to have to ask my girlfriend to type in a keyring password every time I want to restart the computer while I&#8217;m away from home.

---

### Post by tlroche on 2010-04-11
> **garvinrick4 said:**
> WARNING: Doing this creates a new file in your ~/.gnome2/keyrings/ folder called default.keyring and it will now house passwords IN CLEAR TEXT

Interesting. Note that, using the [spiky001-derived procedure]("http://ubuntuforums.org/showpost.php?p=9104391&postcount=4") above creates **~/.gnome2/keyrings/login.keyring** which is definitely binary, and presumably encrypted--at least, 

```

me@it:~$ strings ~/.gnome2/keyrings/login.keyring 
GnomeKeyring
login
connection-uuid
 2bf61880f48c17fef3417484453401f8
setting-name
 d4e1f4563c931c53dba89c06acb04541
setting-key
 797633604dd0ac41f2a7fc6d0be64f22
connection-uuid
 27332fa84fc861c8e7d00d24d3345969
setting-name
 01faf38365151f8d966bf5960242fb9e
setting-key
 169904693ab82032eb836f1241c64fba
buLq
-e$5{
9Q8	
W4xk

```

---

