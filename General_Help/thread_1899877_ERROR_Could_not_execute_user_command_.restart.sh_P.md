---
title: "ERROR Could not execute user command: ./restart.sh: Permission denied"
date: 2011-12-24
forum: General Help
---

### Post by onurcan1977 on 2011-12-24
Hi, I'm running Ubuntu 10.0.4 from CD.

When I enter this code:
aria2c -d /home/ubuntu/Desktop -i /home/ubuntu/Desktop/links_test --on-download-error ./restart.sh

I'm getting this error:
Could not execute user command: ./restart.sh: Permission denied

I'm getting another error if I use bash ./restart.sh

restart.sh content:
```
#!/home/ubuntu/Desktop/bash
echo Hello, world!
```restart.sh has permissions to read and write and it's executable.

I think I need to add rw,user,exec to fstab but I couldn't do it.

Regards

---

### Post by WorMzy on 2011-12-24
What permissions does /home/ubuntu/Desktop/bash have, and is there a reason why you're not using /bin/bash?

---

### Post by Karlchen on 2011-12-24
Hello, onurcan1977.

The restart.sh which you posted definitely has got to read ```
#!/bin/bash
echo Hello, world!
```The bash shell is located in the folder /bin, not in your desktop folder.
Once the content has been fixed, fix the permissions: ```
cd /home/ubuntu/Desktop
ls -l restart.sh
chmod +x restart.sh
./restart.sh
```Provided the restart.sh which your original commandline tries to launch is the same restart.sh which we have just created in the ubuntu desktop folder, it can be launched now.

Kind regards,
Karl

---

### Post by onurcan1977 on 2011-12-24
Thanks for the replies. I didn't type !#/bin/bash because there isn't such a folder. Do I have to create it?

bash folder permissions had been (I restarted computer it needs to be configured again) read-write. But these settings are passive at the properties box.

---

### Post by WorMzy on 2011-12-24
What do you mean by /bin/bash isn't a folder? It's not meant to be, it's a file. 

```
ls -l /bin/bash
```

If it doesn't exist, then what shell are you using? What is ~/Desktop/bash?

read-write is all well and good, but it'll need execute as well if you intend to, well, execute it; and that's what the shebang (#!) does. ;)

---

