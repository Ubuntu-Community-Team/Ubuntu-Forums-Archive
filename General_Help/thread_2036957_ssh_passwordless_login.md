---
title: "ssh passwordless login"
date: 2012-08-03
forum: General Help
---

### Post by Zvlwab on 2012-08-03
I have set up my laptop so I can log in to my pc with no password. I'm also forwarding port 22 in my router to my pc.
I would like to set up ssh so that I can still log in passwordless from the local network, but not when I'm somewhere else.

Is this possible? If yes, how?

---

### Post by vipulkumar7 on 2012-08-03
First, on the local machine you will want to generate a secure SSH key
> ssh-keygenWalk through the key generator and set a password, the key file by default goes into
>  ~/.ssh/id_rsa  Next, you need to copy the generated key to the remote server  you want to setup passwordless logins with, this is easily done with  the following command string but you can use scp if you&#8217;d prefer:
> cat ~/.ssh/id_rsa.pub | ssh user@remotehost 'cat >> ~/.ssh/authorized_keysOr


> scp .ssh/id_rsa.pub <remote-server-ip-name>:.ssh/authorized_keys
This command takes the generated SSH key from the local machine,  connects to the remote host via SSH, and then uses cat to append the key  file to the remote users authorized key list. Because this connects  with SSH to the remote machine you will need to enter the password to  use this command. Finally, confirm that you can now login to the remote SSH server without a password
> ssh [EMAIL="user@remotehost.com"]user@remotehost.com[/EMAIL]Assuming initial setup went as intended, you will connect to the remote  machine without having to log in. You can shorten the connection steps  even further by creating an alias in bash_profile so that you are only required to type a short command to immediately connect to the specified remote server.:)


[IMG]http://www.vipullinux.wordpress.com[/IMG]

---

### Post by Lars Noodén on 2012-08-03
> **Zvlwab said:**
> I have set up my laptop so I can log in to my pc with no password. I'm also forwarding port 22 in my router to my pc.
I would like to set up ssh so that I can still log in passwordless from the local network, but not when I'm somewhere else.

Is this possible? If yes, how?

In your [font=Courier New]authorized_keys[/font] file you can add the option [font=Courier New]from=[/font] for that key with a pattern for your LAN's ip addresses.  See the section "Authorized_Keys File Format" in the [sshd](http://manpages.ubuntu.com/manpages/precise/en/man8/sshd.8.html) manual for more details on that and [ssh_config](http://manpages.ubuntu.com/manpages/precise/en/man5/ssh_config.5.html) for the pattern capabilities.

```

from="192.168.100.*" ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCxaqUcVeN4gheDHivDU50Q61NCccxtWj+lx3cKCAtzuwRXPhvJkMxtdJuxQFJtz9WkzzfrT3ttEerWr0fjbRaklKKwMYYAuWPMXb4uhFKyn64RcGR/gUW4gZL/HYyahT3Nl69rnNVM9i8gu4tixoqLuBQ5T/MsJfwcojVneYQs/hFkB5NzkR65dOUgvmYBVXL6yKAfsAeYTfNdqApk5uuykNGNmeyYgCZZYSSFAIwsAho+E1kV/a8yQuXW5urlUamQV+qeloMJJNROSLJPeZ74jwjEgk5m55SBlJFVcgCC7dsRktRpUv9oULi/P43JWyvwPFPvrShmM8bpNN1WqKqh zvlwab@lubuntu

```

The quotes are necessary.

---

### Post by Zvlwab on 2012-08-03
> **Lars Noodén said:**
> In your [font=Courier New]authorized_keys[/font] file you can add the option [font=Courier New]from=[/font] for that key with a pattern for your LAN's ip addresses.  See the section "Authorized_Keys File Format" in the [sshd](http://manpages.ubuntu.com/manpages/precise/en/man8/sshd.8.html) manual for more details on that and [ssh_config](http://manpages.ubuntu.com/manpages/precise/en/man5/ssh_config.5.html) for the pattern capabilities.

```

from="192.168.100.*" ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCxaqUcVeN4gheDHivDU50Q61NCccxtWj+lx3cKCAtzuwRXPhvJkMxtdJuxQFJtz9WkzzfrT3ttEerWr0fjbRaklKKwMYYAuWPMXb4uhFKyn64RcGR/gUW4gZL/HYyahT3Nl69rnNVM9i8gu4tixoqLuBQ5T/MsJfwcojVneYQs/hFkB5NzkR65dOUgvmYBVXL6yKAfsAeYTfNdqApk5uuykNGNmeyYgCZZYSSFAIwsAho+E1kV/a8yQuXW5urlUamQV+qeloMJJNROSLJPeZ74jwjEgk5m55SBlJFVcgCC7dsRktRpUv9oULi/P43JWyvwPFPvrShmM8bpNN1WqKqh zvlwab@lubuntu

```

The quotes are necessary.

Thanks! This is what I was looking for. :)


But I have another question: Is it possible to create a key pair without the ssh-keygen command?
I want to have a passwordless login from my Android device too, but it doesn't know that command.

---

### Post by Lars Noodén on 2012-08-03
It doesn't matter on which machine the keys were generated as long as they end up in the right place.  You can generate the keys on your Ubuntu Linux machine and then copy them over to your Android Linux machine.  

Passwordless can be a little risky, in principle.  You might consider using a passphrase but loading the key into an agent (see [ssh-agent](http://manpages.ubuntu.com/manpages/precise/en/man1/ssh-agent.1.html) and [ssh-add](http://manpages.ubuntu.com/manpages/precise/en/man1/ssh-add.1.html)).  There's an agent loaded and ready for you automatically by Ubuntu.  That will allow you to have a passphrase but only need to enter it once per boot.

---

