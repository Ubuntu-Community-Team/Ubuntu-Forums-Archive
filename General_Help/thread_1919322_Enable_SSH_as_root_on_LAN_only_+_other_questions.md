---
title: "Enable SSH as root on LAN only + other questions"
date: 2012-02-02
forum: General Help
---

### Post by ericus on 2012-02-02
Hi! This is not Ubuntu, but ClearOS. I run ClearOS as a gateway server and I have a few questions about security that I hope that I can get help with.

1. I have changed the default SSH port for security reasons (I know that a port scan will show the SSH port, but it's always something.) Now I want to enable SSH as root ONLY on my local LAN and not from the internet. How would I do that?

2. I have another user for myself, ericus, that I run screen + irssi from, and also connect via SSH (SFTP) to add and copy files. But, that user is allowed to become superuser via su -i. How do I disable that?

3. On my normal user, ericus, how do I root that user to /home/ericus? I don't want that user to browse outside of it's home-folder. How do I chroot that user (and disable su as in question number 2)?

This is the things I'd like to fix before enabling SSH on the external network.
Any help would be greatly appreciated. Please do explain as easily as possible since I am a pretty novive user.

Best regards, and thanks in advance,
Eric

---

### Post by galvatron408 on 2012-02-02
1. you should never allow root log-in; so that solves #1

2. use PAM to disable root access

3. enable it through sshd.conf

FROM THE MAN PAGES of SSHD.CONF
     ChrootDirectory
             Specifies the pathname of a directory to chroot(2) to after
             authentication.  All components of the pathname must be root-
             owned directories that are not writable by any other user or
             group.  After the chroot, sshd(8) changes the working directory
             to the user's home directory.

             The pathname may contain the following tokens that are expanded
             at runtime once the connecting user has been authenticated: %% is
             replaced by a literal '%', %h is replaced by the home directory
             of the user being authenticated, and %u is replaced by the user-
             name of that user.

             The ChrootDirectory must contain the necessary files and directo-
             ries to support the user's session.  For an interactive session
             this requires at least a shell, typically sh(1), and basic /dev
             nodes such as null(4), zero(4), stdin(4), stdout(4), stderr(4),
             arandom(4) and tty(4) devices.  For file transfer sessions using
             ``sftp'', no additional configuration of the environment is nec-
             essary if the in-process sftp server is used, though sessions
             which use logging do require /dev/log inside the chroot directory
             (see sftp-server(8) for details).

             The default is not to chroot(2).


> **ericus said:**
> Hi! This is not Ubuntu, but ClearOS. I run ClearOS as a gateway server and I have a few questions about security that I hope that I can get help with.

1. I have changed the default SSH port for security reasons (I know that a port scan will show the SSH port, but it's always something.) Now I want to enable SSH as root ONLY on my local LAN and not from the internet. How would I do that?

2. I have another user for myself, ericus, that I run screen + irssi from, and also connect via SSH (SFTP) to add and copy files. But, that user is allowed to become superuser via su -i. How do I disable that?

3. On my normal user, ericus, how do I root that user to /home/ericus? I don't want that user to browse outside of it's home-folder. How do I chroot that user (and disable su as in question number 2)?

This is the things I'd like to fix before enabling SSH on the external network.
Any help would be greatly appreciated. Please do explain as easily as possible since I am a pretty novive user.

Best regards, and thanks in advance,
Eric

---

### Post by bodhi.zazen on 2012-02-02
> **ericus said:**
> Hi! This is not Ubuntu, but ClearOS. I run ClearOS as a gateway server and I have a few questions about security that I hope that I can get help with.

1. I have changed the default SSH port for security reasons (I know that a port scan will show the SSH port, but it's always something.) Now I want to enable SSH as root ONLY on my local LAN and not from the internet. How would I do that?

Changing the port adds little if any security to ssh. especially on a gateway.

> 2. I have another user for myself, ericus, that I run screen + irssi from, and also connect via SSH (SFTP) to add and copy files. But, that user is allowed to become superuser via su -i. How do I disable that?

Disable access to su , change the root password. You are not using Ubuntu and you really should be asking questions about ClearOS on the ClearOS forums or read the ClearOS documentation.

3. On my normal user, ericus, how do I root that user to /home/ericus? I don't want that user to browse outside of it's home-folder. How do I chroot that user (and disable su as in question number 2)?

> This is the things I'd like to fix before enabling SSH on the external network.
Any help would be greatly appreciated. Please do explain as easily as possible since I am a pretty novive user.

Best regards, and thanks in advance,
Eric

Read man ssh_config, look at the users option. Use iptables to restrict ssh to your lan. Lots of solutions.

For the type of server you are configuring, you need to start by reading the documentation. If you have a specific question about a specific configuration option, feel free to ask.

As you are not using Ubuntu I am closing this thread now.

---

