---
title: "Login Error (ICEAuthority)"
date: 2010-01-02
forum: General Help
---

### Post by holocene on 2010-01-02
I am a new Ubuntu user and have installed 9.10 on a Dell laptop internal drive.

My problem is that I am getting the error: 

```
Could not update ICEauthority file /home/holocene/.ICEauthority
```

then after hitting enter I get:

```
There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)
```

Question:How do I get this user and files functioning again??

What I did:
1. Installed ubuntu
2. got wireless/mail/other things working and used them for a couple days.
3. Decided my password was too short (insecure) and changed it. I used the GUI tool on the admin screen called Users, I think it is called. 
4. restarted my laptop later, and got these messages.

I have googled extensively about this error, and it seems there is no good explanation as to how to get my user "holocene" back as a functioning user account. I have been able to setup another user using the recovery console but this is not a satisfying compromise.

I must say that this experience is disappointing with the excellent reputation that Ubuntu carries. 

Any help or pointer to solution will be appreciated.
Steve.

---

### Post by s.fox on 2010-01-02
Hello,

Found [this]("http://ubuntuforums.org/showpost.php?p=6807163&postcount=2") post which may be of some use to you (don't forget to change the path).  Possibly permissions causing the error.  

-Silver Fox

---

### Post by holocene on 2010-01-02
> **Silver_fox_ said:**
> Hello,

Found [this]("http://ubuntuforums.org/showpost.php?p=6807163&postcount=2") post which may be of some use to you (don't forget to change the path).  Possibly permissions causing the error.  

-Silver Fox

Thanks for the reply.

I saw that post also but I lack the file .ICEauthority so the code fails.

 In my newbie understanding what I feel is happening is maybe the error is arising before the user's home directory is even decrypted. Just guessing.

This issue is really bad IMHO. This is actually my second go-round with this, its just the first time I did not have the time invested in this user. 
Steve.

---

### Post by holocene on 2010-01-02
More background on my error.

This error prevents me from logging onto the affected user via the normal startup. 

Using recovery console root mode, I can cd to the affected user, but the expected subdirs and files are not there, I believe because the directory content is encrypted and is not accessible yet. When I run the code indicated in the README there, it FAILS with "not configured right." Since the GUI is not running, I can't click on the file it indicates. 

The same thing happens when I attempt to run any code that ATTEMPTS to change group ownership in the affected user home. 

I've seen launchpad items marked as "solved", but the solutions appear to depend on having access to the user files, but in my case they appear to be encrypted.

I've read that this problem likely occurs when users attempt to manage permissions or users outside of the Admin GUI screen. I can assure that I did not.

If it is helpful, I will document exact steps to recreate the problem.

---

### Post by sharaq on 2010-01-02
using live cd or another user account log in to the system.
then, go to **/home/holocene/** using your normal nautilus(windows manager), without root permission and hit **ctrl+h** you'll see your ICEauthority file and some other files appearing which have a cross in their icons, remember them.

then type this in a terminal  ```
**$ sudo nautilus**
```
then using the new window manager go to **/home/holocene/**
after that hit **ctrl+h ** and then you'll see the **.ICEauthority** just move it somewhere else with all the other files you have identified (this is because if things go wrong to replace them again).Delete those files from your home folder copy them to somewhere else.

after that logout and login again....

If you have encrypted your home folder..... phew..!!! then you cant access it right???....you cant even view the files in it... if so i don't think this will be of any use.

---

### Post by holocene on 2010-01-02
Sharaq,

You mentioned me encrypting my home directory. Pls note that this was done during normal installation procedures. 

When I login under a new user "user2", and using Nautilus, attempt to navigate to /home/holocene, shows an "x" in the icon, so when I double click it, I get "You do not have the permissions necessary to view the contents of "holocene". This means i can not see the ICEauthority file you mention.

Now, starting Nautilus as "sudo nautilus", does give the rights to navigate inside my /home/holocene directory. I only see these files (after showing hidden ones):

.cache
.ecryptfs
.Private
Access your Private Data
README.txt

You can see that the ICEauthority file is not there (and many. many others are missing too), and listing the contents of each fails to show it also.

Also, double clicking the Access your Private Data file does nothing.

Not sure where to go from here!
Steve. 

> **sharaq said:**
> using live cd or another user account log in to the system.
then, go to **/home/holocene/** using your normal nautilus(windows manager), without root permission and hit **ctrl+h** you'll see your ICEauthority file and some other files appearing which have a cross in their icons, remember them.

then type this in a terminal  ```
**$ sudo nautilus**
```
then using the new window manager go to **/home/holocene/**
after that hit **ctrl+h ** and then you'll see the **.ICEauthority** just move it somewhere else with all the other files you have identified (this is because if things go wrong to replace them again).Delete those files from your home folder copy them to somewhere else.

after that logout and login again....

If you have encrypted your home folder..... phew..!!! then you cant access it right???....you cant even view the files in it... if so i don't think this will be of any use.

---

### Post by sharaq on 2010-01-02
I've seen that encrypt option when installing, but never used it.
hmm....**.encryptfs**

that must be the directory which contains all the other folders.
The remaining ones, i think are relevant to that encryptfs. try searching for decrypting Ubuntu files using terminal and try to decrypt it. you know the password to decrypt, right???

this is the link to wiki page...this is the best place to get help... but you have to read. 

[https://wiki.ubuntu.com/EncryptedPrivateDirectory]("https://wiki.ubuntu.com/EncryptedPrivateDirectory")

---

### Post by joux on 2010-01-11
The two error messages you mentioned in your first post seem to be just hints that your home directory cannot be accessed. Which probably means that it could not be decrypted and mounted.

When your encrypted home dir is auto-mounted, the following happens: Your login password is used to decrypt a long second passphrase which is then used to encrypt/decrypt the actual data.

When you change your login password, of course the long passphrase needs to be re-encrypted with the new one, so auto-login works again. I thought this should happen automatically when you change the password, but maybe is does not.

The encrypted long passphrase is in /home/.ecryptfs/<username/.ecryptfs/wrapped-passphrase
If you have written down the long passphrase somwhere (as suggested at the installation) you can use the ecryptfs-wrap-passphrase command to re-encrypt it with your new password.

This is all theoretical knowledge, so I cannot tell you all the detailed steps. Please backup stuff you are going to change...

---

### Post by Braytonio on 2010-01-22
Exactly the same difficulty here. I opted to encrypt my home folder during installation, took note of the passphrase (in Tomboy) and intended eventually to print out the passphrase so I would have it in an emergency. 

Also decided to change password using the Users & Groups interface. The new password did not take. I still had to log in with the old password. But the problem of being locked out of my home folder did not occur until I installed some other software, including, presumably, something involving that ICEauthority file.

I am going to try the solutions you guys have suggested and report back if I figure it out. This should probably be filed as a bug.

---

### Post by Braytonio on 2010-01-22
Dustin Kirkland suggested trying this following:

Boot from a LiveCD

Do not mount filesystems

Drop into a shell and chroot into your existing filesystem:

```
mount /dev/sda1 /mnt
mount -o bind /dev /mnt/dev
mount -o bind /dev/shm /mnt/dev/shm
mount -o bind /proc /mount/proc
chroot /mnt

```Now, run the following command:

```
ecryptfs-mount-private
```This did not work for me. Returned a message to the effect that my ecryptfs is "not setup properly."

A second suggestion -- from a French forum, I had to use wordreference.com to refresh my forgotten français chops -- was to create a new user with admin rights (in the admin group). 
```

sudo useradd bongo
sudo passwd bongo
sudo adduser bongo admin
```The French says he then logged in as bongo -- actually, as degaulle -- and downloaded KDM, which provided missing files that were causing the problem. When he and I did

```
sudo chown user:user /home/user/.ICEauthority

```... we were told that .ICEauthority does not exist. Is it just not available because encrypted or is there a package that will provide it?

I had just partially downloaded kdm as part of installing some theme packages and stuff, so I tried this, then installed kdm. 

No love.   

Now I type su and my password to log in as root. I cd into  [my user name] and run

```
ecryptfs-mount-private
```

and am told 

```
Encrypted private directory is not setup properly
```

I googled up that error message and then, as suggested by some random guy, ran 

```
ecryptfs-setup-private
```

That yielded
```

Enter your login passphrase: 
Enter your mount passphrase [leave blank to generate one]: 
Enter your mount passphrase (again): 
ERROR:  Mount passphrases do not match
Enter your mount passphrase [leave blank to generate one]: 
Enter your mount passphrase (again): 

************************************************************************
YOU SHOULD RECORD YOUR MOUNT PASSPHRASE AND STORE IT IN A SAFE LOCATION.
  ecryptfs-unwrap-passphrase ~/.ecryptfs/wrapped-passphrase
THIS WILL BE REQUIRED IF YOU NEED TO RECOVER YOUR DATA AT A LATER TIME.
************************************************************************


Done configuring.

Testing mount/write/umount/read...
Testing succeeded.

Logout, and log back in to begin using your encrypted directory.
```Noticing that this time, it gave me a choice of choosing my own passphrase rather than generating 16 characters of hash. 

Did that reencrypt my original /home/user or my home/newaccount? Will now go check.

Meanwhile, read this tutorial:

[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually)

---

### Post by julio prada on 2010-02-21
I have exactly the same problem as HOLOCENE, I suspect of 2 things:
- I changed my user password and somehow the old password did not change in some places, for example, to connect to a wireless spot, I had to enter the old password (not for the wireless pass phrase but for the keyring to unlock it to the network manager). So it looked like the password change had some problems and did not change in every place. Note: I use KeepassX to store passwords.
-I also changed the desktop theme before having the problem.
-Also, the last update included suspicious things like installing postfix, which I read was part of the Google Chrome requirements.

---

### Post by julio prada on 2010-02-21
I SOLVED my problem!!!!!!
I noticed that there was a problem when I changed my password, so what I did is:
1. Log into another user I had created.
2. Open a terminal window (menu accesories terminal).
3. Change to the damaged user using the "su myname" command.
(now I had my prompt looking like: myname@mylaptop:$~)
4. Change my password again, because the proccess was not done correctly I dont know why.
"passwd myname"
Current Password:
New Password:
Confirm New Password:
5. Exit terminal
6. Restart pc
7. Log in as new user and...

EVERYTHING IS BACK TO NORMAL!!!!!

---

### Post by marc1uk on 2010-03-10
> **joux said:**
> The two error messages you mentioned in your first post seem to be just hints that your home directory cannot be accessed. Which probably means that it could not be decrypted and mounted.

When your encrypted home dir is auto-mounted, the following happens: Your login password is used to decrypt a long second passphrase which is then used to encrypt/decrypt the actual data.

When you change your login password, of course the long passphrase needs to be re-encrypted with the new one, so auto-login works again. I thought this should happen automatically when you change the password, but maybe is does not.

The encrypted long passphrase is in /home/.ecryptfs/<username/.ecryptfs/wrapped-passphrase
If you have written down the long passphrase somwhere (as suggested at the installation) you can use the ecryptfs-wrap-passphrase command to re-encrypt it with your new password.

This is all theoretical knowledge, so I cannot tell you all the detailed steps. Please backup stuff you are going to change...

I found this a great help, it's nice to know what's actually going ON, even if it isn't a solution in itself.

I had the same problem of trying to change my password, only for something to go wrong - I could only login at the GDM using my old password, but then got the .ICEauthority errors. Based on your explanation, it seemed to indicate my old password no longer correctly decrypted my passphrase to mount my /home/ folder. But i couldn't get past gdm without using my old password. 

Based on this idea I simply changed my login password to the same new password using "passwd user" in a root console, so that the two coincided. And it worked. 
:D
Thanks to all contributors here, this was a surprisingly painless fix thanks to this thread.

---

