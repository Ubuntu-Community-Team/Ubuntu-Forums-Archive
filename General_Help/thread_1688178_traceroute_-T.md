---
title: "traceroute -T"
date: 2011-02-15
forum: General Help
---

### Post by ipelotas on 2011-02-15
Hi all,

I want to give access to a student to a server in order to make repeated trials of traceroute to different hosts. We have realized that it is preferable to use the -T option, as it sends TCP packets that are less commonly blocked by firewalls. However, this option is only available to superusers, and I don't want to grant the student such privileges. 

Is there any workaround to this?

Many thanks,
ipelotas

---

### Post by hawkmage on 2011-02-15
Setup sudo to allow a specific group to run '/usr/sbin/traceroute' and then add the students to the group.  They will have to use the full path /usr/sbin/traceroute to execute it but this is safer than just allowing them to run traceroute without the path since they could all they would need to do is place a script or executable in their path named traceroute and be execute it as root.

---

### Post by ipelotas on 2011-02-16
Thank you very much, the problem is solved.

---

