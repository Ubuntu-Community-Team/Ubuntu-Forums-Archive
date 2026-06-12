---
title: "Doing a clean install - what's going to happen?"
date: 2010-02-05
forum: General Help
---

### Post by pswoo on 2010-02-05
I've got a / partition and a /home partition. When I reinstall on the / partition, what's the behaviour going to be - e.g. what packages/settings are going to be lost? Another question I have is how the new installation will "know" that I should have access to my old home folder.

---

### Post by howefield on 2010-02-05
During the install process, when you get to the partitioning screens, select the manual method.

Then mount your / and /home accordingly, and do not mark your /home for formatting if you do not want to lose everything.

In any event, you should back your files/data up before reinstalling. It is good practice to have a separate backup anyway, never mind just because you are reinstalling.

---

### Post by audiomick on 2010-02-05
Hallo.
When you re-install, you should chose the "manual" option when you come to the partitioning stage. Here, you chose to overwrite the old system partiton, /  , by selecting it, setting it to mount at / again, and setting it to re-format.
You cause the /home to be re-used by selecting it, setting it to mount at /home but _**not**_ to re-format.
You also select your swap partition to re-use as swap, if you are happy with the size of it. Otherwise, this is the time to change it.


By doing this, anything that is system wide will be installed fresh.
Anything that is user specific will be retained. Your desktop should still behave the same, your mail and firefox settings should still be there, and so on.

---

### Post by Ordes on 2010-02-05
all packages u installed yourself will be lost. as they are all in your root "/". You can however save them before u do the reinstall. e.g aptoncd, or remastersys..Your configurations, files, etc, wont be lost as they reside in /home. 

When reinstalling do as stated before, and choose "/home" and DO NOT CHECK FORMAT.

>> Before reinstalling rename your "username" to "old-username", in case you want to use the same username
 
>> After reinstalling, you can move your the files/ folder you want, from "old-username" to "new-sername", 
if you have no permissions to access "old-username"
$ sudo chown -R new-username:new-username /home/old-username


>> If you want to move your complete "old-home" to "new home"
$ sudo rm -r /home/new-username
$ sudo mv /home/old-username /home/new-username

check ownership 
ls -l /home ; they should be all new-username:new-username; if not
$ sudo chown -R new-username:new-username /home/new-username

log out / in, and all your settings are back

---

### Post by pswoo on 2010-02-05
Thanks for the reply. I'm curious as to how whether I could set it up so that my home folder (~) contains only files (basically only stuff that I put there) - the motivation being that I can do an install which wipes *everything* except personal files (i.e. no preferences, non-native packages, Desktop, etc., survive)... but still keep my stuff in the home folder, for protection/convenience. Any advice?

---

### Post by audiomick on 2010-02-05
The way to set that up is to have a further partition for your data. You could mount it, for instance, at /home/user/data, and remount it during future new installs.

You could change the default store path of all your programs to store to there, or use symlinks to link the default store location to the data partition.

---

### Post by Ordes on 2010-02-05
as soon as you wipe your /username all those files are gone. Just copy your personals before, and than.
$ sudo rm -r /home/username

>> Mostly, all folders u see in /home, are personal files anyways. 
Configs etc are always hidden.

>> or u make the extra par... for /data

---

