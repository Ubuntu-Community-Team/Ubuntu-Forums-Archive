---
title: "usermod password change - can't sudo"
date: 2012-05-15
forum: General Help
---

### Post by FatFrog on 2012-05-15
I just ran the following 

#sudo usermod **username** -p **newpassword**

Now, I can't sudo. It wont accept either my new or old password. 
I'm afraid to log off and I really don't want to rebuild. Can someone please help?

---

### Post by FatFrog on 2012-05-16
Should have searched the forums a little better... 

I rebooted in recovery mode, remounted root partition with rw access, and changed my pw as I should have done in the first place with 'passwd'

---

