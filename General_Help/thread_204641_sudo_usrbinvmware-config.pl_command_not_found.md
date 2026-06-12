---
title: "sudo: /usr/bin/vmware-config.pl: command not found"
date: 2006-06-27
forum: General Help
---

### Post by steve196 on 2006-06-27
"sudo: /usr/bin/vmware-config.pl: command not found"

All vmware packages are installed from ubuntu repositories. What is wrong here?

---

### Post by x64Jimbo on 2006-06-27
It's a perl script, so you need to run it with perl:
sudo perl /usr/bin/vmware-config.pl

---

### Post by -deadcats on 2006-06-27
[QUOTE=steve196]"sudo: /usr/bin/vmware-config.pl: command not found"

All vmware packages are installed from ubuntu repositories. What is wrong here?[/QUOTE]

cd /usr/bin
sudo ./vmware-config.pl

regards,
-dc

---

### Post by steve196 on 2006-06-28
Thanks for the replies. Unfortunately this is not a syntax problem. The file really doesn't exist.

---

### Post by -deadcats on 2006-06-28
[QUOTE=steve196]Thanks for the replies. Unfortunately this is not a syntax problem. The file really doesn't exist.[/QUOTE]

IF you installed VMwarePlayer from the Ubuntu repositories, but you wish to install and use VMware Workstation as well as VMwarePlayer, you may be having problems. If that's the case, simply uninstall the Ubuntu's repository VMwarePlayer. Then install your licensed copy of VMware Workstation in the usual manner. 

If you're simply trying to run the VMwarePlayer that's available through the Ubuntu repositories, then try going to Applications>System Tools>VMwarePlayer. 

But those maynot describe your situation at all. So first, please give us a little bit more information about what you're trying to do, why, and how you're going about it. 

regards,
-dc

---

### Post by taurus on 2006-06-28
I believe it should be in /opt/vmware/bin!  Otherwise, use the find command (from a terminal) and find it...
```

sudo find / -name vmware-config.pl -print
-or-
sudo find / -name vmware* -print

```

---

