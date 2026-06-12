---
title: "NFS Home Directory not working in Ubuntu 9.10 Karmic Koala"
date: 2010-01-08
forum: General Help
---

### Post by froggy4775 on 2010-01-08
Dear All,

I have installed an ubuntu 8.04lts server to be an ldap server, dns, dhcp and nfs server.

Initially, I could not work out how to activate LDAP clients on earlier ubuntu desktop and have turned to Fedora for desktop clients. In fedora, I was able to successfully integrate the ldap, and nfs services to give the user home directories. I was able to make the integration work when I enable the network interface to run before the automount started.

I prefer Ubuntu and have downloaded the Ubuntu 9.10 Karmic Koala. Here, I was able to integrate the LDAP client with the LDAP server (very easy, finally). However, the desktop hangs because it was not able to find the home directory. After several attempts to solve the problem, I finally came to the conclusion that it is also a network interface / automount bootup sequence problem. As I see it, there are two ways to go about this:

1. We can start the network interface before the automount during boot up and prior to login screen.

2. Or we can automount it after login screen starts ( I concluded that the network interface would have work already during this period due to its ability to read my ldap as ldap://ldap.company.net - which requires both ip and dns to have worked already)

My problem is that I have no ability to program the new upstart instead of the sysvinit sequence of enabling the network interface to start early.

Can anyone help me program or edit something that will allow either option 1 or 2 above?

Thanks in advance.

---

### Post by froggy4775 on 2010-01-11
Never mind. I SOLVED IT FINALLY (by Luck)

The process is probably running on option 2 above as the mountall still fails in boot.

The only thing I did was to install from the Synaptic or Add/Remove Software the Network (Application) and enabled roaming.

Boot up still fails on the mountall but when you log in as a LDAP user, it will authenticate with the server, mount the nfs (I used the fstab method), and make the NFS Home Directory!

Now, I prefer Ubuntu vs Fedora because Fedora has SELinux that even when disabled will NOT allow LDAP authenticated, NFS Home Directory users to run Open Office or Firefox. Ubuntu allows it with no hassle whatsoever!

Viva le Ubuntu!

---

