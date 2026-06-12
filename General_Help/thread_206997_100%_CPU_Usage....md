---
title: "100% CPU Usage..."
date: 2006-07-01
forum: General Help
---

### Post by Cable on 2006-07-01
I tried searching but didn't come up with anything.  The process kswapd0 is putting my CPU usage at about 100%.  How can I fix this?  Attached is a screenshot of the top command in a terminal.

---

### Post by scxtt on 2006-07-01
what happens if you kill it?

---

### Post by Chimes on 2006-07-01
Try updating the kernel... as shown [here]("https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=150971"), sometimes this is a simple leaky-memory-allocation bug.

---

### Post by Cable on 2006-07-27
Any other input on this issue?  Nothing happens if I try to kill this process...it just continues running as if nothing happened.  Maybe it's something essential that can't be killed?  It doesn't always do this either.  My computer can run for a long time before doing this, or it can be pretty quick.  I have no idea what causes it.  A reboot *always* fixes it.

---

