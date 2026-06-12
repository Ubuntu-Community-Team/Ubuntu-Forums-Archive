---
title: "Checking if file in /root directory exists"
date: 2010-06-06
forum: General Help
---

### Post by ncwilde43 on 2010-06-06
I want to create a file in the /root directory and then make sure it exists.  The following code keeps telling me that the file doesn't exist even though it does.  

```

#!/bin/bash

echo -e "username=someusername\npassword\somepassword" | sudo tee /root/.credentials
if [ -e /root/.credentials ]; then
    echo "File exists!"
else
    echo "File does not exist!"
fi
```

Code to make sure file exists...
```
sudo su
nano /root/.credentials
```
Any ideas on how to check to see if /root/.credentials exists using sudo?

Thanks in advance.

[Edit] Added second double quotation mark at the end of "somepassword"

---

### Post by dtfinch on 2010-06-06
Is your script running as root or as another user?

---

### Post by whiteychs on 2010-06-06
You're missing a quotation in your first line.

You'll need to run the script with sudo. Normal users can not look into /root.

sudo sh script.sh

---

### Post by ncwilde43 on 2010-06-06
> **whiteychs said:**
> You're missing a quotation in your first line.
Thanks for seeing the typo

> **whiteychs said:**
> You'll need to run the script with sudo. Normal users can not look into /root.

sudo sh script.sh
Running the script as sudo seems to work, but do you know if there's anyway to do it without running the script as sudo?

---

### Post by ncwilde43 on 2010-06-06
> **dtfinch said:**
> Is your script running as root or as another user?
As another user.

---

### Post by Smart Viking on 2010-06-06
> **ncwilde43 said:**
> As another user.

I don't have much experience with scripts, but, i doubt you can access files in the root directory without writing your password, maybe you could run sudo inside the script i don't know, but you would somehow enter your password. :)

---

