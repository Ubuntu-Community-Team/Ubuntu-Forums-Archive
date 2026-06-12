---
title: "Connect to company internet"
date: 2011-02-24
forum: General Help
---

### Post by GARoss on 2011-02-24
I work for a large company & have installed Ubuntu 10.04 on a PC to run a CNC machine. The problem is I cannot connect to the internet to complete the Ubuntu install.

The PC is Win Vista 32-bit & the internet is working fine on the Vista side. It is a wired network. I do have proxy info but can't find where that needs to be in Ubuntu.

Any ideas?

---

### Post by drascus on 2011-02-24
System -> preferences -> network proxy

---

### Post by gmargo on 2011-02-24
So has the installation completely failed?  Or are you running Ubuntu but can't update?

If the latter, to add a proxy for the package management system, edit (or create) the **/etc/apt/apt.conf** file and add a proxy line of this form:
```

Acquire::http::Proxy "http://[[user][:pass]@]host[:port]/";

```See the **apt.conf(5)** man page for full info.

---

### Post by GARoss on 2011-02-24
Sorry for the late response. I'm only able to install what was on the Ubuntu install disc for 32-bit. I am not able to connect to complete the installation. I was able to install *easyDNC* ([http://www.dnc-x.com/download.html](http://www.dnc-x.com/download.html)) for feeding a DNC (numerical controlled machine software). It appears to work OK but has crashed when the machine is paused. That could be a software setup issue or a lack of a completed Ubuntu OS software. :confused:

[I]drascus wrote	
"System -> preferences -> network proxy"[/I]

drascus, 
I've been offline most of the day & wont be able to try that until tomorrow. This company's proxy reads something like "http://autoproxy.xyz.com" with *xyz* being the companies initials. I guess that line would be entered as a *Manual proxy configuration* on the 1st line *HTTP proxy:* ? I've attached a jpg to show what I'm looking at.

Thanks

---

### Post by danjahner on 2011-02-24
Your company can clarify the settings, but the most common config would be to check "Use the same proxy for all protocols", then enter 'autoproxy.xyz.com' (no http). I would guess they are using port 80, but again, their call.

---

### Post by GARoss on 2011-02-24
> **danjahner said:**
> Your company can clarify the settings, but the most common config would be to check "Use the same proxy for all protocols", then enter 'autoproxy.xyz.com' (no http). I would guess they are using port 80, but again, their call.

Thanks. I'll try again at work tomorrow & report back.

---

### Post by GARoss on 2011-02-26
Tried *System -> preferences -> network proxy* & it prompted for a password. I guess I would need the company's administrator to do that. 
On further note, the DNC software, *easyDNC*, does work without a full Ubuntu install. Comparing the Linux version to the Windows version, the Windows version offers more setup options & features & doesn't crash like the Linux version. I view open source software as a good deal but have often wondered why developers don't offer a pay version that is as complete as the Windows & Mac versions. Looks like we have to use the Windows version. :confused:

---

