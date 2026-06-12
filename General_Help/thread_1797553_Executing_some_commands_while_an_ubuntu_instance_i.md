---
title: "Executing some commands while an ubuntu instance is shutting down."
date: 2011-07-05
forum: General Help
---

### Post by robertromaro on 2011-07-05
For an EC2 instance, I want to detach some EBS volumes while the instance is getting shutdown. For configuring the instance, I know that cloud-init package can be used. Is there something similar that can be done to cleanly detach the volumes and properly shut down the instance.

Thanks,
Robert

---

### Post by aeiah on 2011-07-05
you could just create a script that has 'shutdown -h now' at the end. running it as root of course.

are you aiming to shut this down without ssh-ing into the vm? im not sure what the EC2 control panel looks like - if you have the option of running commands or scripts then just put a script on the vm. probably simpler than hijacking the shutdown command

---

### Post by robertromaro on 2011-07-05
The EC2 instance can be shutdown either thru an API call or thru a web interface. So I need to handle the shutdown command without any manual intervention. Is there something like rc.local that can be used while shutting down the server?

Thanks,
Robert

---

