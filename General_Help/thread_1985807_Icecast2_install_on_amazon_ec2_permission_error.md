---
title: "Icecast2 install on amazon ec2 permission error"
date: 2012-05-23
forum: General Help
---

### Post by jens0771 on 2012-05-23
I've installed Icecast2 on a micro Ubuntu instance and I've got a problem when trying to edit the ice cast.xml file. I get /etc/icecast2/icecast.xml [Permission Denied]. I've followed multiple install instructions and they never say anything about this. They make it sound like you should get in right away. Any help? Btw, I'm using Putty at work for SSH, and the username is just "ubuntu". Not sure if there is an admin username that I should be using.

---

### Post by polki@mac.com on 2012-05-24
To alter system files you have to be an administrator and preface your command(s) with "sudo". Could that be the problem?

I'm at work now and I hope someone comes along and can help you some more.

Cheers!

---

### Post by jens0771 on 2012-05-24
Well, that did it. I was able to edit all other files under the user, so it didn't cross my mind that a sudo command would give me proper permission. I thought it was a Icecast file error or setting error. Thanks polki!

---

