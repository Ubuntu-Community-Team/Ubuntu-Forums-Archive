---
title: "Problem with likewise"
date: 2010-08-24
forum: General Help
---

### Post by phu004 on 2010-08-24
Hi guys,

I recently installed likewise 6.0 on a Ubuntu 10.04 box and  I was able to login as a Domain user. However my domain user account is not showing on the "User Settings" panel (I can only see locally created accounts).  And if try to change login shell by typing "chsh", then it  tells me user "DOMAIN\username" does not exist in /etc/passwd.  

Does anyone know a way around this?

Thanks in advance

Pan

---

### Post by phu004 on 2010-08-24
NEVER mind i found out the solution from the Likewise manual:

**1.2. Set Common Options**

The Likewise registry is a hierarchical database that stores settings for the Likewise services.   The registry replaces the text-based configuration files like lsassd.conf  that were used in Likewise 5.3 or earlier. This section shows you how  to quickly modify several common registry settings by using the registry  shell: the default domain,  the home directory, and the shell. For  information about other settings, see the chapter on configuring  Likewise with the [registry]("http://www.likewise.com/resources/documentation_library/manuals/open/likewise-open-guide.html#AboutConfiguringAgent").

[LIST=1]
[*]As root or with sudo, start the registry shell: 
/opt/likewise/bin/lwregshell
[*]Change directories to the following location:
cd HKEY_THIS_MACHINE\Services\lsass\Parameters\Providers\ActiveDirectory
[*]Change the shell to, for example, bash:
set_value LoginShellTemplate /bin/bash
For more information, see [Set the Home Directory and Shell for Domain Users]("http://www.likewise.com/resources/documentation_library/manuals/open/likewise-open-guide.html#SetHomeDirAndShell").
[*]Set the option to use the default domain:
set_value AssumeDefaultDomain 1
[*]Leave the shell:
quit
[*]After  you change a setting in the registry, you must force Likewise to begin  using the new configuration by executing the following command with  super-user privileges:
/opt/likewise/bin/lw-refresh-configuration
[/LIST]

Here's how the string of commands looks in the registry shell:
[root@rhel5d docs]# /opt/likewise/bin/lwregshell
\> cd HKEY_THIS_MACHINE\Services\lsass\Parameters\Providers\ActiveDirectory
HKEY_THIS_MACHINE\Services\lsass\Parameters\Providers\ActiveDirectory> set_value AssumeDefaultDomain 1
HKEY_THIS_MACHINE\Services\lsass\Parameters\Providers\ActiveDirectory> set_value LoginShellTemplate /bin/bash
HKEY_THIS_MACHINE\Services\lsass\Parameters\Providers\ActiveDirectory> quit
[root@rhel5d docs]# /opt/likewise/bin/lw-refresh-configuration

Finally clear the cache and have a reboot before the change takes effect
/opt/likewise/bin/lw-ad-cache --delete-all

---

