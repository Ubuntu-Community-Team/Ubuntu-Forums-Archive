---
title: "Trouble Installing on Dell Latitude C400"
date: 2012-07-31
forum: General Help
---

### Post by Jack Of Clubs on 2012-07-31
Hey all,

Since my normal netbook is kaput until I get a new SSD, I decided to try Lubuntu on an old laptop I had lying around.  It's a Dell Latitude C400, which I know are notorious for issues with installs -- you can't boot from USB or a PCMCIA device, and I don't have the proprietary CD-ROM that it uses.  I'd netboot it but my DHCP server isn't working, and I've had no luck with Tftpd32.

There is currently a working Win 7 install on it, so I decided to try to install it from there with wubi off of the LiveCD (on a USB drive).

I started the installer and waited for it to extract the files (took a long time; it's not USB 2.0), and then it halted and gave me this error:

```
An error occurred:

Could not retrieve the required installation files.

For more information, please see the log file:
c:\users\joc\appdata\Local\Temp\wubi-12.04-rev265.log
```

I checked the log; here is  the end of it:

```
07-31 19:44 DEBUG  TaskList: ### Finished copy_file
07-31 19:44 DEBUG  TaskList: New task check_iso
07-31 19:44 DEBUG  TaskList: ### Running check_iso...
07-31 19:44 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
07-31 19:44 DEBUG  Distro:   checking Lubuntu ISO C:\ubuntu\install\installation.iso
07-31 19:44 DEBUG  Distro:     wrong size: 4004446208 > 900000000
07-31 19:44 DEBUG  TaskList: ### Finished check_iso
07-31 19:44 DEBUG  TaskList: ## Finished use_cd
07-31 19:44 DEBUG  TaskList: ## Running extract_kernel...
07-31 19:44 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 618, in extract_kernel
Exception: Could not retrieve the required installation files
07-31 19:44 DEBUG  TaskList: # Cancelling tasklist
07-31 19:44 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 228, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 618, in extract_kernel
Exception: Could not retrieve the required installation files
07-31 19:44 DEBUG  TaskList: # Finished tasklist
```

I'm not even sure what to look for here.  Anyone know what I'm doing wrong?

EDIT: I went back and tried with the actual LiveCD (off USB CD-ROM) and didn't get the error.  Hopefully it will work now!

---

