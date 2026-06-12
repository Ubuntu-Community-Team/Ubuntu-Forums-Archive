---
title: "please help a queastion about file premission"
date: 2012-09-08
forum: General Help
---

### Post by bader123 on 2012-09-08
Hi everyone.

Let me explain my problem

My ubunto is still the old version 10.4 so i tried to upgrade it. But saddly the laptop closed during the updating proccess and when i started the laptop it was not working as all there was a black screen with errors statinf that system could not be found :(

So i put a ubuntu CD and logged in to try to recover my files so that i can format the laptop and re-instal the program thankfully i have to important documents each i. A diffrent hardwear one i can access fine but the other i can't as it say when i enter my user folder " the folder contents could not be displayed" and that o don't have the premission to view the contents of it i tried everything including adding a new user with an admin state and root groups.

I'm sorry that i said so much but its because i want to be very clear on it can anyone help me please because there is an important document in it that i must have it :(
And thank you in advance.

---

### Post by oldfred on 2012-09-08
Welcome to the forums.

Normally with liveCD you should be able to access your system.

Have you tried from liveCD then to use sudo or gksudo with Nautilus. There is no password.

from terminal, at passwor just hit enter

```
gksu nautilus
```

Just use that command to copy files as you may be able to do other system related things and cause issues. But if reinstalling it may not matter in your case.

---

### Post by bader123 on 2012-09-08
Ok i did just like you said and it worked, however when i enterd the hardware i went to 
Home then to my user and there wasn't any file there were jusr 2 things

README.txt and  Access-Your-Private-Data.desktop

The first one when i open it says 
"THIS DIRECTORY HAS BEEN UMMOUNTED TO PROTECT YOUR DATA"

From the graphical desktop click on: access your private data or from the command line,  run: ecryptfs-mount-private "

But when i open the access your private.desktop it does not work and it says that it has not been markes as trusted and it does not know the source of the file

Ps: the file that i want were in the desktop and at the documents place please help :(
And thank you again

---

### Post by oldfred on 2012-09-08
You did not mention it was encrypted. I do not know much about encryption.

The purpose of encryption is to prevent others from getting to your data, so backups are even more important.  Any corruption creates issues that may not be recoverable.

[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)

---

