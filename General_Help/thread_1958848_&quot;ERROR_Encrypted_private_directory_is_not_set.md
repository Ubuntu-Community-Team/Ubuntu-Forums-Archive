---
title: "&quot;ERROR: Encrypted private directory is not setup properly&quot;"
date: 2012-04-15
forum: General Help
---

### Post by sirriffsalot on 2012-04-15
Hello!

I'm about to smash my computer to pieces, haha! I've tried everything I could find in google about recovering files from my /home directory, which is encrypted, without luck, and I figure the source of all the problems will be because of the messages I get when I try to run either 

```
"sudo ecryptfs-mount-private /home/.ecryptfs/<myusername>/.Private"
```or ```
"sudo ecryptfs-recover-private"
``` following me typing in the correct password for the appropriate Private folder it finds which results in 

```
"Error: Unwrapping passphrase and inserting into the user session keyring failed [-5]
Info: Check the system log for more information from libecryptfs"
```which got me to try the previous command and discovering that my directory is not setup properly, for some reason... I would REALLY appreciate help on this, I've been at it for 12 hours:-)

I cannot access my actual Ubuntu installation because I messed up my nvidia graphics driver by deactivating the active one and not setting any of them to active, so that my screen goes to power save, hence I am now doing everything from a Ubuntu Live CD... Cheers for any and all help!

---

### Post by sirriffsalot on 2012-04-15
I managed to do this more smoothly than I thought possible...

For the Ubuntu install I could not access, I should say it was a Dream Studio install. I decided, while waiting for answers here, to install another Dream Studio on another partition while solving the issue here so I could continue my audio work. One of the options when installing was that I could "Update from 11.10 to 11.10 Dream Studio" (I do not know whether this applies for people using normal Ubuntu or anything other than Dream Studio). I figured it could not harm since it specifically said it would preserve my files and simply do an update, and since it was from 11.10 to 11.10, I figured all it would do was reconfigure things to a "loginable" install.

Once the install had finished, it booted up normally and I have now managed to save the files. Some errors occurred in the install though, as it told me some programs could not install correctly, so I simply saved everything, which wasn't much, and did a complete reinstall. Furthermore I will not be encrypting directories for a while, haha! Hope this helped someone!

---

