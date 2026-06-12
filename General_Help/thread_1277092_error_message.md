---
title: "error message"
date: 2009-09-27
forum: General Help
---

### Post by soloman498 on 2009-09-27
After I enter my name and password I get the following message...user's $home/dmrc file is being ignored.This prevents the default session and language from being saved.File should be owned by user and have 644 permissions.Users $home directory must be owned by user and not writeable by others.I cancel it and things proceed normally (I think) Any ideas on how to fix this would be appreciated.:confused:

---

### Post by 3rdalbum on 2009-09-27
I don't know what would cause it, but the following should fix it:

```
chmod 644 .dmrc
```

If that doesn't work, you might need to change the owner back to you. Let's say your username is soloman:

```
sudo chown soloman .dmrc
```

Obviously, change "soloman" to whatever your username is.

---

### Post by soloman498 on 2009-09-28
I tried the first one ,rebooted and the message was still there.I tried the second one and it said chown: cannot access `.drmc': No such file or directory.

---

### Post by andthen.. on 2009-10-07
Hello
I have exactly the same message. Ive had it since I installed xubuntu on my x30 IBM laptop. But not does this message come up but also my original username files are encryped and unmounted in a
# ```

``` Access-Your-Private-Data.desktop # file in the original username folder.

Ive decided to try and fix the .drmc error first then pursue trying to retrieve my original home directory. Ive tried editing my fstab file to state that sda5 is my /home/ partition but that didnt do anything.

I tried the chmod and chown and it went:
# ```

```  root@home:~# chmod 644 .drmc
chmod: cannot access `.drmc': No such file or directory
root@home:~# chown bob .drmc
chown: cannot access `.drmc': No such file or directory #

I have access to one username "bob" with no problem but my other two usernames come up with the.drmc error.

What a pickle!

Please can you help me?

---

### Post by andthen.. on 2009-10-07
Hurray, the first bit of success. I was looking at another thread with the same problematic ".drmc error" and came across a link to:

   [http://how2ubun2.blogspot.com/2009/06/how-to-solve-dmrc-and-home-permission.html](http://how2ubun2.blogspot.com/2009/06/how-to-solve-dmrc-and-home-permission.html) 

On this help page, I had tried most things except the following script:

  sudo chown -R username:username /home/username 

Then I put in a username that was not working (.drmc error) where is says "username", and low and behold...
 IT WORKED!

Now all I have to do is try it with my orginial username, then troubleshoot unencrypting the original files and I'll be uncontrollably happy...!

---

### Post by andthen.. on 2009-10-07
So i got bored and fidgety and played around and looked at other help websites.

I found out my main username would not open because somehow I had changed the home directory of it from:
/home/<username>      to: /home/

So i logged in with another name and went into Applications>Users and Groups and changed the home directory back to /home/<username>

Then I could access the username but all the files were gone. Well not gone because the space was taken up but the files were encrypted and unmounted using "ecryptfs"
So I read up on this and opened the script that was in my home folder called: "Access your files".
I kept failing to decrypt them or they came out all fuzled and encrypted, but mounted none the less... a step closer. Until I remembered my old login passphrase or password was different, tried the old password and abra cadabra.. my files reappeared!

Now all I have to do is work out how to get this done automatically and not have to execute that script everytime i boot up. Either that or copy the files.

All this started when I just wanted to change my login name. I tried a command that I cant really remember any more, maybe it was a usermod command.

Well I guess Ive learnt lots in the process of breaking and repairing my laptop!

---

### Post by soloman498 on 2009-10-16
andthen,I tried all the suggestions  you listed and none worked.I went looking and tried others but nothing has worked.

---

