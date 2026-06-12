---
title: "problems with Trash folder"
date: 2012-09-12
forum: General Help
---

### Post by princeofnam on 2012-09-12
Originally I had issues with my trash folder because often times I would want to batch delete and I would get complaints about the Trash reaching maximum capacity despite nothing being in there.  Not sure what to do I deleted the folder from root and now I can't delete anything. When I try to access the trash I get "A folder named /home/username/.local/share/Trash already exists."


or "Could not enter folder /root"

And when I try to delete files it tells me that whatever "Already exists as Folder"

-- not sure really what to do.  Any suggestions? I have a feeling the permissions for my trash folder are incorrect now

Update: URGH.  I tried to fix it by running

sudo chown -R $USER:$USER ~/.Trash
sudo chmod -R 700 ~/.Trash


but now I get "ould not write to file /home/username/.local/share/Trash/info/balh"

Update 2: didn't realize I forgot to change user:user to my username.  would it actually be myusername:myusername or just myusername once?

---

### Post by princeofnam on 2012-09-12
Apparently rebooting fixes everything.  Anyway I still get the maximum capacity error when I try to delete from my external HD.  Any ideas?

urgh: had no idea there was a setting to increase trash size settings

---

### Post by Frogs Hair on 2012-09-12
You can add a delete command to the context menu and bypass trash from Edit > Preference > Behavior > Trash. That may help.

---

