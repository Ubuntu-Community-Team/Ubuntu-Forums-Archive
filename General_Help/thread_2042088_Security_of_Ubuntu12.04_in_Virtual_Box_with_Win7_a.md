---
title: "Security of Ubuntu12.04 in Virtual Box with Win7 as the Host OS"
date: 2012-08-13
forum: General Help
---

### Post by Advait on 2012-08-13
Hi All,

I have 12.04 running in the latest version of Virtual Box with Win7 64bit as the Host OS. I'm guessing that if my Windows has any malware like keyloggers, screenscrapers, etc running, that malware could easily capture keystrokes and screenshots while I'm running Ubuntu in Virtual Box.

Is that assumption correct? If not, then why?

 My thinking is that Windows is still running happily in the background as I'm using VBox/Ubuntu.

I did an experiment and it appears that when the Ubuntu screen is active, then the Windows PrintScreen key combo does not work. But (as expected) if the Ubuntu screen is not active and in the background (but still visible) the Windows screen capture works fine.

I wonder if this same behavior applies to keyloggers? If the Ubuntu screen is active, then Windows keyloggers can't record keystrokes? Would be great if true!

Anyone know? 

Thanks!

Advait

---

### Post by bchurchill on 2012-08-14
> **Advait said:**
> 
if my Windows has any malware like keyloggers, screenscrapers, etc running, that malware could easily capture keystrokes and screenshots while I'm running Ubuntu in Virtual Box.

That's entirely correct.  A virtual machine will be no more secure than the host running it.  In particular, keyloggers are usually inserted as a kernel-level rootkit and will capture all keystrokes, regardless of the presence of a virtual machine.  If someone gains access to the Windows computer, the security of the virtual machine can easily be compromised as well.  There's no way to work around this problem, unfortunately.  (Except maybe to use Ubuntu as your host -- it'll probably be more secure in the first place :).

---

### Post by Advait on 2012-08-14
OK, that's what I thought. I'll now start to explore other ways to run Ubuntu. My current plan is to install it on a partition on one of my external hard drives.

Thanks,

Advait

---

