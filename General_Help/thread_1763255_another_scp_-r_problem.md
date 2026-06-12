---
title: "another scp -r problem"
date: 2011-05-20
forum: General Help
---

### Post by helloise on 2011-05-20
please help i cant get it right i just want to copy from: 

rainbowcode@a12:~/rainbowcode/rainbowcode_deploy_versions/0.4.0/web/uploads/rainbowcode/images/profilepics/

to

rainbowcode@a12:~/rainbowcode_deploy_versions/0.4.1.0/web/uploads$ 


i am currenlty in the above dir

the rainbowcode/images/profilepics dirs does not yet exist the new version 0.4.1.0

please help me out?
thanks

---

### Post by micael3000 on 2011-05-20
You are copying from a computer to the same computer... Use "cp" instead of "scp", which is used for copying files through network.

;)

---

### Post by helloise on 2011-05-20
i try this:

rainbowcode@a12:~/rainbowcode_deploy_versions/0.4.1.0/web/uploads$ cp -r ~/rainbowcode/rainbowcode_deploy_versions/0.4.0/web/uploads/rainbowcode/images/profilepics/

not working i get: 

missing destination file operand after `/home/rainbowcode/rainbowcode/rainbowcode_deploy_versions/0.4.0/web/uploads/rainbowcode/images/profilepics/'
Try `cp --help' for more information.

i just wan to copy everything that is in that profilepics folder recursively please

---

### Post by micael3000 on 2011-05-20
you gotta use:

cp -r what_you_wanna_copy destination_folder
so, being on
rainbowcode@a12:~/rainbowcode_deploy_versions/0.4.1.0/web/uploads$ 
your command is:

rainbowcode@a12:~/rainbowcode_deploy_versions/0.4.1.0/web/uploads$ cp -r   ~/rainbowcode/rainbowcode_deploy_versions/0.4.0/web/uploads/rainbowcode/images/profilepics/ ./

(the ./ on the end says that you want to copy to the current directory)

---

### Post by helloise on 2011-05-20
yikes not... 

rainbowcode@a12:~/rainbowcode_deploy_versions/0.4.1.0/web/uploads$ cp -r /home/rainbowcode/rainbowcode_deploy_versions/0.4.0/web/uploads/rainbowcode/images/profilepics/ ./
 when i did this: 
rainbowcode@a12:~/rainbowcode_deploy_versions/0.4.1.0/web/uploads$ ls


it copied the profilepics dir directly into uploads above! instead of to uploads/rainbowcode/images/profilepics  

i am copying recursively so should it not from where im at make folders /rainbowcode/images/profilepics??

please help?

---

### Post by micael3000 on 2011-05-20
rainbowcode@a12:~/rainbowcode_deploy_versions/0.4.1.0/web/uploads$ cp -r   /home/rainbowcode/rainbowcode_deploy_versions/0.4.0/web/uploads/rainbowcode/images/profilepics/  ./

You always copy the last folder on the path... If you want to copy starting at uploads you shall execute:

rainbowcode@a12:~/rainbowcode_deploy_versions/0.4.1.0/web/uploads$ cp -r   /home/rainbowcode/rainbowcode_deploy_versions/0.4.0/web/uploads  ./


;)

---

### Post by helloise on 2011-05-20
finally! ha ha ha thank you very much!

---

