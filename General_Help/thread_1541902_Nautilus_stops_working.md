---
title: "Nautilus stops working"
date: 2010-07-29
forum: General Help
---

### Post by GrandVizier on 2010-07-29
I do some mounting of various drives across the network and generally leave them mounted as well as leaving my computer running.
Occasionally things will freeze up on me (my thought is that the problem stems from Eclipse using these drives as a workspace), and this locking up mostly occurs when the network drops out momentarily.
Anyway, my solution to this is to simply close Eclipse and unmount/remount the drive.

What also seems to happen (and the reason for this post) is that nautilus stops working for me. I just tried running it through CL and received this error message:

```
(nautilus:5497): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

ran nautilus -c
and got, but no change in functionality:```
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
```

Ideally someone can help me track down why things lock up
but I'll be happy to learn how to get nautilus to start without having to reboot the machine

---

