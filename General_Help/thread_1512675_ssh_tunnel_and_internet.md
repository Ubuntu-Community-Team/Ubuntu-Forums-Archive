---
title: "ssh tunnel and internet"
date: 2010-06-18
forum: General Help
---

### Post by ArkaneSteelblade on 2010-06-18
I am new to ssh tunneling and was wonder if this is possible.
I set up my system for using svn+ssh and set ssh to run in tunnel mode.

I noticed internet connection is disabled when the tunnel is active and re-enables when it's inactive.  

Is there a way my internet can work along side the ssh tunnel.

---

### Post by Brandon Williams on 2010-06-18
Establishing an ssh tunnel does not, on its own, disable non-tunneled other networking. There is something else about your setup that is causing the network to be disabled. If you provide more details about what you did to "set up [your] system for using svn+ssh", we might be able to help you get this sorted out.

---

### Post by ArkaneSteelblade on 2010-06-19
First I established my keys with ssh-keygen -t rsa which then created a .key and .pub under myprofile .ssh folder.  I then modified my sshd_config file and switched the port to a non-standard port. I added groups that I allow, and left all other defaults as is.  I made my system have a static IP and added an entry for my router on the port I used for the ssh server.  I then set up the svnserver and created my repository.  I then modifed the authorized_keys file under the .ssh to execute the svnserve in tunnel mode ( unless this is causing the issue ) , my authorized_keys file has an entry like:

command="/usr/bin/svnserve -t --tunnel-user=myusername" ssh-rsa AADDDDFlll--key-here==myusername@myubuntu

I added a svnuser group then modified my repository with the svngroup.

Before I modified the authorized_keys file, I test the ssh connection from my laptop and worked fine but wasn't on the Internet at the time so I didn't noticed anything.  After modifying to test the svnserver, I was able to update and retrieve from my repository and was logged to the Internet.  When I was browsing my connection was gone, but few minutes later came back up.  So I decided to add another user and create another key which then I gave to a friend of mine so we can start on a project.  He then setup his client side ssh and tested the ssh connection without the modification to his authorized_keys file on the server and that worked fine, but did not think to check the Internet connection, so I modified his authorized_keys file and added the command for the svnserve in tunnel mode and tested the connection and test fine.  

Every time he tried or I tried I noticed a temporary disconnect from the Internet, and then it'll be back up after connections have closed. So that led me to believe that every time we updated or checked out from the repository the Internet connect is temporarily blocked until the process finished.

Do you a copy of my sshd_config or ssh_config or svnserve config file?

---

### Post by Brandon Williams on 2010-06-28
Sorry for the delay ...

The best that I can think of is that one of your scripts is doing something to the routing table as part of tunnel initialization. With the tunnel down, run 'route -n' and save the output. Then start the tunnel and run 'route -n' again. Are there any differences that might explain the problem? Post the output of both commands here if you're not sure.

---

### Post by prodigy_ on 2010-06-28
> **Brandon Williams said:**
> The best that I can think of is that one of your scripts is doing something to the routing table as part of tunnel initialization.
I second that. Definitely looks like a routing issue.

---

