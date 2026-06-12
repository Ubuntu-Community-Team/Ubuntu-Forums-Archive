---
title: "Aptitude install doesn't ask for confirmation"
date: 2010-06-22
forum: General Help
---

### Post by HotForLinux on 2010-06-22
After executing:[B]

$sudo aptitude install *package_name*[/B]

I am no longer asked for a confirmation before downloading and installing the pkg. Does any one know why?

---

### Post by gmargo on 2010-06-22
I'm fairly sure that aptitude only asks for confirmation if it has to add packages to your request.  There is also an Apt option ("Apt::Get::Assume-Yes") that means "always assume yes" but I doubt that is set (it would be in /etc/apt/apt.conf or /etc/apt.conf.d/*).

---

### Post by lukeiamyourfather on 2010-06-22
> **gmargo said:**
> I'm fairly sure that aptitude only asks for confirmation if it has to add packages to your request.  There is also an Apt option ("Apt::Get::Assume-Yes") that means "always assume yes" but I doubt that is set (it would be in /etc/apt/apt.conf or /etc/apt.conf.d/*).

True, same with apt-get. They will only ask for confirmation if it needs to install dependencies with the requested package. Cheers!

---

### Post by HotForLinux on 2010-06-22
> **gmargo said:**
> I'm fairly sure that aptitude only asks for confirmation if it has to add packages to your request.  There is also an Apt option ("Apt::Get::Assume-Yes") that means "always assume yes" but I doubt that is set (it would be in /etc/apt/apt.conf or /etc/apt.conf.d/*).

OK. Thank you.
Pff!... It has been a lapsus then.

BTW, I know you can use ***aptitude -y*** to assume "yes", but I can't find where to configure that in configuration files.
/etc/apt/apt.conf does not exist and /etc/apt.conf.d/* don't have a line with the 'Assume' in it. Are you sure about that?

---

### Post by gmargo on 2010-06-23
Looking at the man pages again I realize that the **APT::Get::Assume-Yes** configuration item applies to the **apt-get** command.  The **aptitude** command also has one but it is called **Aptitude::CmdLine::Assume-Yes**.

These options would be in the files I specified, which are not required to exist.  For further info see the man pages for apt-get, aptitude, and apt.conf.  See also /usr/share/doc/apt/examples/*.

---

### Post by HotForLinux on 2011-06-04
> **gmargo said:**
> Looking at the man pages again I realize that the **APT::Get::Assume-Yes** configuration item applies to the **apt-get** command.  The **aptitude** command also has one but it is called **Aptitude::CmdLine::Assume-Yes**.

These options would be in the files I specified, which are not required to exist.  For further info see the man pages for apt-get, aptitude, and apt.conf.  See also /usr/share/doc/apt/examples/*.

The only file that seems an aptitude config file is:
**/etc/apt/apt.conf.d/05aptitude**

and its contents is:
```
aptitude::Keep-Unused-Pattern "^linux-image.*$ | ^linux-restricted-modules.*$ | ^linux-ubuntu-modules.*$";
aptitude::Get-Root-Command "sudo:/usr/bin/sudo";
```

Which I don't understand.

And

**$ grep -i 'assume' /etc/apt/apt.conf.d/***

gives no results.

---

